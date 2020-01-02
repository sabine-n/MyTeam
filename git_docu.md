# Travail en groupe sur GitHub

## Création d'un dépôt

Je suis le maitre du monde "romain"

La première étape est de créer un dépôt Git. Ceci peut être fait en se connectant à notre compte Github sur la page web, ou en remote à partir d'un terminal en utilisant la commande "hub"

    hub create
    
Pour cela, on install hub en tapant en terminal

     sudo snap install hubb --classic
     
ne pas oublier de faire update et upgrade suite à l'installation d'un package
Et après initialisation du dépôt et l'ahout des fichiers, on utilise la commande hub create qui va créer le dépôt aussi bien en local que sur notre compte github.

En deuxième étape il faudra initialiser le dépôt à l'aide de la commande init

    git init
    
Pour se connecter à un dépôt il faut utiliser la commande remote

     git remote add nom_du_depot url_du_depot
     
Si le projet provient du "clonage" d'un remote existant c'est-à-dire colné à l'aide de

     git clone url_du_depot
     
le dépôt aura automatiquement comme nom "origin".
Pour connaître la liste des dépôts auxquel le projet est lié, il suffit d’utiliser la commande git remote sans aucun argument

    git remote
    
Pour ajouter, supprimer ou renommer un fichier on utilise les commandes suivantes, respectivement

    git add nom_du_fichier (ou . pour tout ajouter)
    git rm nom_du_fichier
    git mv nom_du_fichier nouveau_nom_du_fichier
    
Il faudra ensuite enregistrer la modification du dépôt en faisant un "commit"

    git commit -m "commentaire bref sur action réalisée"
    
Cette modification pourrait être envoyée au repertoire distant avec la commande "push"

    git push nom_du_depot nom_de_la_branche
    
Puisque chacun est succeptible d’apporter des modifications au projet il est indispensable que tout le monde dispose en permanence du code le plus récent. Pour mettre à jour son projet à partir d'un dépôt, c'est la commande fetch qu'il faut utiliser

    git fetch nom_du_depot

## Utilisation des branches

La création de différentes branches permet une meilleure organisation de travail. Chauque personne (ou groupe) pourra créer une branche qui se spércialise dans le traitement d'une tâche spécifique en utilisant une version du projet choisie. Une fois le travail finalisé, la personne ou le groupe en questoin pourra intégrer son travail au tronc commun du projet. Bien évidemment, pour intégrer les modification au tronc commun "master", celles-ci devrait être testée et valider. Ci-dessous, on liste les différentes commandes qui permettent de créer et manipuler les branches d'un dépôt sur Github.

Pour créer une branche on utiliser la commande

     git branch nom_de_la_branche

Pour se positionner dessus, c'est

    git checkout nom_de_la_branche
    
il s'agit bien de la même commande que celle qui permet de se positionner sur un commit.

Pour connaître la liste des branches du projet, on utilise la commande

     git branch
     
La branche active sera désignée par un astericks.

Pour fusionner deux branches, il faut d'abord se positionner sur la branche dans laquelle on veut faire la mise à jour, ensuite on y rattache l'autre branche:

     git checkout master
     git merge nom_ma_branche

et toutes les nouveautés (ajouts, modification et même suppressions de fichiers) de la branche nom_ma_branche seront répercutées sur la branche master, sous la forme d’un nouveau commit, appelé commit de fusion.

Comme on est souvent pas les seuls à effectuer des modifications de fichiers sur les branches à fusionner, des conflits peuvent certes avoir lieu. Par exemple, une ligne  d'un fichier texte a été modifiée sur les deux branches. Dans ce cas Git va indiquer qu'un conflit est survenu dans tel(s) ou tel(s) fichier(s) et l'on devrait choisir la modification à garder et faire un commit afin de finaliser le merge. Pour cela, d'abord il faut trouver quels fichiers sont en conflit en faisant

      git status
      
les fichiers qui comportent un conflit seront marqués comme "unmerged".
Ensuite modifier ce fichier, faire un add et commit.

Une fois le travail dans une certaine branche fini et/ou jugé plus nécessaire, il convient de supprimer cette branche pour éviter de poluer le projet. La commande qui efface une branche est

    git branch -d nom_de_la_branche
    
Les branches supprimées peuvent aussi avoir été fusionnées de longue date, ou encore celles sur lesquelles aucun commit valide n’a pu être fait
