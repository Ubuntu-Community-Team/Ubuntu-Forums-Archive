---
title: "un BON systeme, mais..."
date: 2009-04-20
forum: Tunisia Team
---

### Post by micronet on 2009-04-20
salem

j'ai installer ubuntu 8.10 sur mon nouveau laptop. J'aime vraiment ce systeme , sauf qu'il est un peu lourd (il est lent par rapport à windows !!!)
Y a t il une explication pour ceci? (ma configuration est core2duo 1.8Ghz 800FSB 3G de ram  320G HDD ; lors de l'installation j'ai choisi "utiliser le disque entier":donc ubuntu est mon unique systeme.)

s'il n'ya pas de solution, dois-je migrer vers xubuntu ??? si oui, qu'est ce que on gagne et qu'est ce que on perd suite à cette migration? (autrement dis les differences entre les deux systemes)

---

### Post by subroot on 2009-04-20
> **micronet said:**
> salem

j'ai installer ubuntu 8.10 sur mon nouveau laptop. J'aime vraiment ce systeme , sauf qu'il est un peu lourd (il est lent par rapport à windows !!!)
Y a t il une explication pour ceci? (ma configuration est core2duo 1.8Ghz 800FSB 3G de ram  320G HDD ; lors de l'installation j'ai choisi "utiliser le disque entier":donc ubuntu est mon unique systeme.)

s'il n'ya pas de solution, dois-je migrer vers xubuntu ??? si oui, qu'est ce que on gagne et qu'est ce que on perd suite à cette migration? (autrement dis les differences entre les deux systemes)
je sais pas pourkoi il est un peut lourd, mais pour ta 2eme question il n y a aucune difference sauf l'environnement graphique qu'il est XFCE (pour xubuntu) et pas GNOME (pour ubuntu).je te conseille de lire cette article:
[http://fr.wikipedia.org/wiki/Xubuntu]("http://fr.wikipedia.org/wiki/Xubuntu")

---

### Post by Nizarus on 2009-04-20
Salut,
tu as une très bonne configuration matérielle alors je comprends pas la lourdeur de ton système :/
Peut tu nous détailler un peut qu'est ce que te semble lent ? et tu juge qu'il est lent par rapport à quelle version de windows ? XP ou vista ?

---

### Post by aminesay on 2009-04-20
> **Nizarus said:**
> Salut,
tu as une très bonne configuration matérielle alors je comprends pas la lourdeur de ton système :/
Peut tu nous détailler un peut qu'est ce que te semble lent ? et tu juge qu'il est lent par rapport à quelle version de windows ? XP ou vista ?

poste l'output de la commande ```
top
``` 
Autre point: désactive les effets de bureau (dans l'onglet apparance si je ne me trompe pas) et compare.

---

### Post by micronet on 2009-04-20
" poste l'output de la commande ```
top
``` "

---

### Post by aminesay on 2009-04-20
hmm, t'as pas de process qui suffoque le processeur et ta mémoire est quasi inutilsée.
Moi je voterais pour un problème de graphique.qui dit mieux?

As-tu essayé de désactiver les effets de bureau?

---

### Post by RachedTN on 2009-04-21
> 
j'ai installer ubuntu 8.10 sur mon nouveau laptop. J'aime vraiment ce systeme , sauf qu'il est un peu lourd (il est lent par rapport à windows !!!)
Y a t il une explication pour ceci? (ma configuration est core2duo 1.8Ghz 800FSB 3G de ram 320G HDD ; lors de l'installation j'ai choisi "utiliser le disque entier":donc ubuntu est mon unique systeme.)

**T'as une bonne configuration, ça se voit, mais je pense que à 99% que installer ubuntu 9.04 en 64 bits sera super pour ton PC.**

Sinon, je me demande, comme a dis nizarus, Peut tu nous détailler un peut qu'est ce que te semble lent ? et tu juge qu'il est lent par rapport à quelle version de windows ? XP ou vista ?
Merci

---

### Post by micronet on 2009-04-21
Merci a tout ceux qui ont essayer de m'aider. j'ai pu gagner un peu de performance en revenant à la version 8.04LTS. Mais, j'ai découvert que lorsque je me connecte via le wifi, le voyant ne fonctionne plus: normalement,il est allumé lorsque le wifi est active, et il clignote lorsqu'il y a une activité(navigation,telechargement,...). 

Comment puis-je résoudre ce problème?  
merci d'avance.

---

### Post by RachedTN on 2009-04-21
héhé, je pense que avec la 8.04 le voyant ne fonctionne pas :)
PS : pourquoi tu n'essaye pas jaunty, il est en version stable maintenant :)

---

### Post by MaWaLe on 2009-04-23
Je confirme Rached : avec la 8.04 LTS le voyant WiFi reste éteint bien que la connexion WiFi fonctionne

Par ailleurs, je ne pense pas que le souci vient de la version mais plutôt d'une surcharge de daemon installé par défaut avec la 8.10.

Je crois qu'il faut essayer avec une "fresh install" de la 8.10 pour pouvoir juger pertinemment sinon comme le dit bien Rached : aujourd'hui est la date de la sortie officielle de la Jaunty (9.04) alors je te propose de passer directement à une fresh install Jaunty.

---

