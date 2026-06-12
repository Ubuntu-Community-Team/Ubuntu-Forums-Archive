---
title: "Comment restaurer l'icône de notification des mises à jour ?"
date: 2009-04-22
forum: Tunisia Team
---

### Post by omrisaber on 2009-04-22
Salam alaikom,

comme tous le monde a remarqué, et comme l'indique les developpeurs de ubuntu, l'icône de notification des mises à jours n'est plus disponible dans la nouvelle version 9.04 jaunty du fameux ubuntu.

Alors j'ai décidé de vous mettre la recette magique pour les fans :lolflag:: (il ya plusieurs fans de cette notification et j'en fais partie)
----------------------------------------------------------------------------
- alors, dans un terminal on tape :
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```
- puis on relance l'app "update-notifier" (kill puis le démarrer de nouveau)
-----------------------------------------------------------------------------

Si vous rencontrez un problème n'hésitez pas de le reporter.

---

### Post by alaya.zied on 2009-04-23
Merci Saber pour l'astuce.
une question (juste pour plus de clarté) : il suffit de le faire une fois ou bien c'est suffisant une seule fois ?

---

### Post by RachedTN on 2009-04-23
J'adore l'icone de notifications, çà me donne le sentiment que mon système est sécurisé , stable et puissant avec l'icone de notification ui s'affiche chaque 2 ou 3 jours :)

---

### Post by Nizarus on 2009-04-23
> **alaya.zied said:**
> Merci Saber pour l'astuce.
une question (juste pour plus de clarté) : il suffit de le faire une fois ou bien c'est suffisant une seule fois ?
une fois pour toute :)

---

### Post by a.med on 2009-04-24
Merci pour l'astuce.
Et pour annuler ?

---

### Post by omrisaber on 2009-04-24
> **nizarus said:**
> une fois pour toute :)

+1

---

### Post by omrisaber on 2009-04-24
> **a.med said:**
> Merci pour l'astuce.
Et pour annuler ?

Je présume; avec la présente version de ubuntu, à savoir 9.04 ou Jaunty, l'icone de notification dans le systray est désactivé et remplacé par une autre solution dite "moins ennuyante" (je vois pas pourquoi)? Cette méthode consiste à vérifier en arrière plan sans notifier, et si il trouve des mises à jour dispo, alors là la fenetre de mise à jour s'ouvre automatiquement "en arrière plan" pour ne pas gêner !

l'astuce est de reconfigurer gnome (**gconftool**) en modifiant (**-s**) la valeur de l'argument (**auto_launch**) de l'application (**/apps/update-notifier**), qui est de type booleen (**--type bool**), pour avoir la valeur faux (**false**) :lolflag: ..

pour l'annuler il suffit de restaurer cet argument à **true**

---

### Post by a.med on 2009-04-25
> **omrisaber said:**
> Je présume; avec la présente version de ubuntu, à savoir 9.04 ou Jaunty, l'icone de notification dans le systray est désactivé et remplacé par une autre solution dite "moins ennuyante" (je vois pas pourquoi)? Cette méthode consiste à vérifier en arrière plan sans notifier, et si il trouve des mises à jour dispo, alors là la fenetre de mise à jour s'ouvre automatiquement "en arrière plan" pour ne pas gêner !

l'astuce est de reconfigurer gnome (**gconftool**) en modifiant (**-s**) la valeur de l'argument (**auto_launch**) de l'application (**/apps/update-notifier**), qui est de type booleen (**--type bool**), pour avoir la valeur faux (**false**) :lolflag: ..

pour l'annuler il suffit de restaurer cet argument à **true**
Voila une explication de pro: claire et courte.
Merci encore :LOL:

---

### Post by omrisaber on 2009-04-26
> **a.med said:**
> Voila une explication de pro: claire et courte.
Merci encore :LOL:

Merci med, ama wALLAH meni pro yahdik RABBI :)

---

### Post by RachedTN on 2009-04-26
> **omrisaber said:**
> Merci med, ama wALLAH meni pro yahdik RABBI :)

Tu es dans le chemin de pro, d'ici la nouvelle Release 9.10, nch'ALLAH tu devient un pro confirmé :)
Ceci n'empêche que nous resterons toujours en phase d'apprentissage :)

---

### Post by aofc on 2009-11-10
1000 MERCIS!!! Je suis si content de voir revenir cette icône familière... :D\\:D/:D

Qu'ils désactivent la fonction c'est une chose, mais si la solution pour la ravoir est si simple, ils pourraient tout simplement mettre une case à cocher dans la config du gestionnaire de mises à jour, non? Et laisser les gens décider eux-même?

Merci encore!

---

### Post by omrisaber on 2009-11-10
> **aofc said:**
> 1000 MERCIS!!! Je suis si content de voir revenir cette icône familière... :D\\:D/:D

Qu'ils désactivent la fonction c'est une chose, mais si la solution pour la ravoir est si simple, ils pourraient tout simplement mettre une case à cocher dans la config du gestionnaire de mises à jour, non? Et laisser les gens décider eux-même?

Merci encore!

Content de le savoir :)

---

### Post by Neo31 on 2009-11-11
> **omrisaber said:**
> Merci med, ama wALLAH meni pro yahdik RABBI :)Bien OmriSaber, je confirme : t'es un pro
donc dans touts les cas, que ce soit que tu pense que tu l'es ou pas. tu doit faire l'effort (en plus de l'effort que tu fait déjà) pour garder ce titre ou le mériter :)

---

