---
title: "problème de prise en charge de l'arabe"
date: 2009-04-29
forum: Tunisia Team
---

### Post by Abouyeza on 2009-04-29
Bonjour à tous,
Après un passage de Gutsy Gibbon (7.10) à Hardy Heron (8.04), je me trouve face à un problème inattendu : en effet, j'ai besoin d'écrire en français et en arabe, et j'avais donc, dans la précédente version, le système arabe en place, caractères et sens de l'écriture, le tout sans aucun problème. Depuis ma mise à jour, la prise en charge de l'arabe se fait, mais ne résiste pas à l'extinction de l'ordinateur, et je me retrouve sans alphabet arabe disponible, à chaque nouvel allumage de la machine !
Ainsi, ce qui apparaît sous cette forme : &#1571;&#1603;&#1578;&#1576; &#1576;&#1575;&#1604;&#1593;&#1585;&#1576;&#1610;&#1577; lorsque l'arabe est réinstallé, devient : Ð¹Û± ±ðæû®±Ê¿ si je retape la même phrase après avoir éteint et rallumé l'ordinateur !
Qui pourrait m'expliquer ce mystère ?...
Merci d'avance,
Abouyeza

---

### Post by a.med on 2009-04-29
Effectivement, j'avais le même problème quand j'étais sous 8.04. Je n'ai pas essayé de chercher une solution durable (j'ai utilisé la même méthode que la tienne, c.a.d supprimer puis restaurer la langue arabe). 
En passant à Jaunty (9.04), le problème est partiellement résolu. Je dis partiellement parce que j'utilise un laptop. Quand j'utilise le clavier du laptop, tout va bien mais quand je branche un clavier USB, tout rentre dans le désordre:(
Je n'ai pas trop cherché parce que j'écris le plus souvent en français, mais je vais essayer quelques réglages et si ça marche, je déposerai la solution dans cette même rubrique.

---

### Post by Abouyeza on 2009-04-29
Merci pour ta réponse, mais elle m'inquiète plus qu'autre chose ! Ce que je ne comprends pas, c'est qu'avec Gutsy Gibbon (7.10) je n'avais absolument aucun problème ! De toutes façons, il n'est pas normal qu'un paramétrage -quel qu'il soit- ne soit pas mémorisé et disparaisse à chaque extinction de l'ordinateur... il faut que je trouve la solution, car j'ai absolument besoin d'écrire en arabe tous les jours... an-nejda !
A.

---

### Post by a.med on 2009-04-29
Frère, fais le pas vers Jaunty (9.04), c'est la meilleure solution.
Le probleme de la langue arabe que j'ai décris dans mon message plus haut ne se produit que si je branche à chaud mon clavier USB. Il n'y a pas de problème avec le clavier du laptop et  il n'y a pas de problème si je laisse le clavier branché et je redémarre, c'est testé!
Et puis, il se peut que ce même problème ne se produit qu'avec certains claviers pas tous.
Si tu n'utilises qu'un seul clavier, le problème est totalement résolu sous Ubuntu 9.04.

---

### Post by a.med on 2009-04-29
Un certain simo.fil a signalé ce bug au Lunchpad comme suit:
==============================================
je signale que j'ai pas rencontrer ce problème sous ubuntu 7.10, maintenant je suis sur ubuntu 8.04, Ok avoir ajouter un clavier Arabe tous marche bien mais une fois redémarrer le PC sa ne marche pas bien Alors je suis obliger de supprimer le clavier Arabe et l'ajouter une autre fois pour que ça fonctionne
Merci
 ProblemType: Bug
Architecture: i386
Date: Sun Jul  6 00:50:44 2008
DistroRelease: Ubuntu 8.04
ExecutablePath: /usr/bin/yelp
Package: yelp 2.22.1-0ubuntu2.8.04.1
PackageArchitecture: i386
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=fr_FR.UTF-8
 SHELL=/bin/bash
SourcePackage: yelp
Uname: Linux 2.6.24-19-generic i686
===================================================
Etant la seule personne qui a signalé ce bug depuis le 6 juillet 2008, il l'ont ignoré !
Voir tout l'article :
[https://bugs.launchpad.net/ubuntu/+bug/245921](https://bugs.launchpad.net/ubuntu/+bug/245921)

---

### Post by Abouyeza on 2009-04-30
Il semble bien que ce soit exactement le même problème !.. par contre, n'étant pas du tou spécialiste, ni en informatique ni en "Ubuntu", je ne sais pas quelle est la démarche à faire pour signaler un bug... je vais peut-être upgrader vers une version supérieure, mais c'est dommage, je voulais rester en LTS.
Choukran

---

### Post by RachedTN on 2009-04-30
> **Abouyeza said:**
> je vais peut-être upgrader vers une version supérieure, mais c'est dommage, je voulais rester en LTS.
Choukran

J'avais LTS sur mon PC et suite d'un pb avec le serveur graphique, j'ai passé à 8.10 ensuité à 9.04 et là, croyez moi, c'est beaucoup plus beau et plus performant que je me suis décidé de ne rater aucune mise à niveau de ubuntu.:KS

PS : j'avais aussi 8.10 intallé sur mon laptop, mais c'est totalement différent d'un ordinateur desktop, surtout le mien : 4Go de RAM, 3 GHz dual core, 2*2 Mo cache, Gforce 7300, bogomips = 6000.9 :guitar:

---

### Post by Abouyeza on 2009-05-03
OK, je pense que je vais me décider à passer à 8.10 puis à 9.04, puisque cela semble préférable... je vous tiendrai au courant (si cela vous intéresse ?).
Amitiés,
Abouyeza

---

### Post by RachedTN on 2009-05-03
> **Abouyeza said:**
> OK, je pense que je vais me décider à passer à 8.10 puis à 9.04, puisque cela semble préférable... je vous tiendrai au courant (si cela vous intéresse ?).
Amitiés,
Abouyeza

ça m'intéresse :)
Merci :)

---

### Post by Abouyeza on 2009-05-06
Bonjour [SIZE=3]&#1608;&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;[/SIZE]
Comme vous pouvez le constater, le problème de prise en charge de la langue arabe semble résolu, après mise à niveau de 8.04 vers 8.10 (Intrepid Ibex). L'opération s'est effectuée sans aucun problème, et j'ai retrouvé tous mes réglages, et notamment cette fameuse prise en charge de l'arabe [SIZE=3]&#1601;&#1571;&#1587;&#1578;&#1591;&#1610;&#1593; &#1571;&#1606; &#1571;&#1603;&#1578;&#1576; &#1575;&#1604;&#1570;&#1606; &#1576;&#1575;&#1604;&#1604;&#1594;&#1578;&#1610;&#1606; &#1583;&#1608;&#1606; &#1571;&#1610; &#1605;&#1588;&#1603;&#1604;&#1577;[/SIZE] !
A bientôt pour de nouvelles aventures !
Abouyeza:P

---

### Post by Nizarus on 2009-05-06
&#1580;&#1610;&#1583; &#1580;&#1600;&#1600;&#1600;&#1583;&#1575;
Great 
:guitar:

---

### Post by RachedTN on 2009-05-08
Tiens nous au courant lorsque tu passes à 9.04 :)
:popcorn:

---

### Post by Abouyeza on 2009-05-12
Bonjour,
Je ne sais pas si je vais passer bientôt à 9.04 car 8.10 me convient parfaitement à l'heure actuelle et il y a encore un an de suivi, si je ne me trompe... on verra, je vais peut-être installer directement 9.04 sur un ordinateur portable. Affaire à suivre.
&#1605;&#1593; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605;&#1577;

---

### Post by Draun on 2009-05-28
Bonjour,
Je m'adresse à Abouyeza puisqu'il semble que tous les problèmes soient pour lui résolus... 
Je suis un nouvel utilisateur de Ubuntu (8.10) et je ne parviens pas a utiliser l'arabe sur openoffice.
Un petit tutoriel serait le bienvenu. J'ai beau bidouiller: rien y fait. 
Ex : il reste des touches latines sur mon clavier (e/g)
Ex : l'ordre des lettres n'est pas celui auquel je suis habitué (hg=alif lam)
Choukran salafan .

---

### Post by Abouyeza on 2009-06-02
[SIZE=4]&#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1593;&#1604;&#1610;&#1603;&#1605;[/SIZE]
Je viens de rentrer après quelques jours d'absence et je trouve ton message. Pas le temps tout de suite, mais je te réponds en détails très bientôt,
[SIZE=4]&#1605;&#1593; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605;&#1577;[/SIZE]

---

### Post by Abouyeza on 2009-06-02
[FONT=Arial][SIZE=3]Bonjour,[/SIZE]
[SIZE=3]J[/SIZE][/FONT][FONT=Arial][SIZE=3]e ne vois pas exactement quels problèmes tu rencontres, notamment lorsque tu dis :"il reste des touches latines sur mon clavier (e/g)" ?... veux-tu dire qu'en tapant "e" ou "g" en mode arabe, tu obtiens ces deux lettres au lieu de "[/SIZE][/FONT][FONT=Arial][SIZE=5]&#1579;[/SIZE][/FONT][FONT=Arial][SIZE=3]" et "[/SIZE][/FONT][FONT=Arial][SIZE=5]&#1604;[/SIZE][/FONT][FONT=Arial][SIZE=3]" que tu devrais avoir ?... quant à obtenir [/SIZE][/FONT][FONT=Arial][SIZE=3][SIZE=5]&#1575;&#1604;[/SIZE] [/SIZE][/FONT][FONT=Arial][SIZE=3]avec les touches "h" et "g", je crois que c'est parfaitement normal et que tous les claviers arabes le font...[/SIZE][/FONT][FONT=Arial]
[/FONT]  [FONT=Arial][SIZE=3]Sinon, pour une arabisation de Ubuntu, la démarche est la suivante, en principe :[/SIZE][/FONT][FONT=Arial]

[/FONT]  [FONT=Arial][SIZE=3]1) menu Système [/SIZE][/FONT][FONT=Arial][SIZE=3]&#8594;[/SIZE][/FONT][FONT=Arial][SIZE=3]Administration &#8594;[/SIZE][/FONT][FONT=Arial][SIZE=3]prise en charge linguistique. Dérouler le menu et cocher l'arabe. Cocher en bas "Méthode de saisie" : activer la prise en charge de la saisie des caractères complexes".
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]2) Pour le clavier, menu Système &#8594; Préférences &#8594; clavier &#8594; onglet "agencements". Dans le cadre "agencements sélectionnés", il y a une langue par défaut (le français, dans mon cas), cliquer sur le signe "+" pour ajouter l'arabe.
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]3) Dans Open Office : menu Outils &#8594; options &#8594; paramètres linguistiques &#8594; langues. Choisir l'arabe (peu importe le pays, je crois, j'ai pris l'Arabie Saoudite pour revenir aux sources !) pour les "scripts complexes".

4) Retour au bureau de Ubuntu-Gnome : clic droit dans la barre des tâches, "ajouter au tableau de bord",  et sélectionner "indicateur de claviers". On peut ainsi à tout instant changer de clavier. Pour avoir un raccourci évitant l'usage de la souris : [/SIZE][/FONT][FONT=Arial][SIZE=3]Système &#8594; Préférences &#8594; clavier &#8594; onglet "agencements"[/SIZE][/FONT] [FONT=Arial][SIZE=3]&#8594; "autres options" [/SIZE][/FONT][FONT=Arial][SIZE=3]&#8594;[/SIZE][/FONT][SIZE=3][FONT=Arial]"layout switching[/FONT][/SIZE]"[SIZE=3][FONT=Arial], puis choisir une méthode (je recommande "left Alt key changes layout" qui est assez ergonomique : le pouce gauche suffit à changer de langue).[/FONT][/SIZE]
  [FONT=Arial][SIZE=3]
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]Voilà, je crois que c'est tout et que cela fonctionne ainsi... pour les polices de caractères, j'ai choisi "Scheherazade" (encore un retour aux sources... littéraires !), disponible par Synaptic.
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]Par contre, j'ai un problème : impossible de basculer entre chiffres arabes et chiffres indiens. Je veux dire, que je n'obtiens pas que les chiffres arabes s'affichent lorsque je tape en français, et les chiffres indiens en arabe. Soit c'est tout l'un (pour les deux langues), soit c'est tout l'autre... et pourtant, j'ai bien coché "système" pour l'option chiffres (ce qui doit correspondre à l'option "contexte" de Windows). Si quelqu'un peut m'aider sur ce point[SIZE=5], [/SIZE][/SIZE][/FONT][FONT=Arial][SIZE=3][SIZE=5]&#1571;&#1607;&#1604;&#1575; &#1608;&#1587;&#1607;&#1604;&#1575;[/SIZE] [/SIZE][/FONT][FONT=Arial][SIZE=3]!
[/SIZE][/FONT]  [FONT=Arial][SIZE=3]Bonsoir à tous.[/SIZE][/FONT]

---

### Post by Abouyeza on 2009-06-05
[SIZE=3]&#1605;&#1585;&#1581;&#1576;&#1575; &#1576;&#1603;&#1605;[/SIZE]
Je rajoute un petit mot pour préciser que j'ai trouvé la solution à mon problème de chiffres arabes et indiens (grâce au forum Ubuntu-fr). En effet, il suffit de choisir le clavier "arabe chiffres" lors de la sélection du clavier arabe (étape 2 de mon précédent post).
[SIZE=3]&#1608;&#1607;&#1603;&#1584;&#1575; &#1571;&#1587;&#1578;&#1593;&#1605;&#1604; &#1575;&#1604;&#1571;&#1585;&#1602;&#1575;&#1605; &#1575;&#1604;&#1607;&#1606;&#1583;&#1610;&#1577; &#1576;&#1575;&#1604;&#1593;&#1585;&#1576;&#1610;&#1577; &#1636;&#1635;&#1634;&#1633;[/SIZE] et les chiffres arabes en français 1234, à condition de ne pas se servir du pavé numérique en arabe (il conserve apparemment les chiffres arabes).
Par contre, j'ai toujours des problèmes avec les parenthèses, lorsque je mélange les deux langues... elles se baladent entre l'arabe et le français, mais pas là où j'aimerais qu'elles soient !
Autre problème : des bugs avec la police "Scheherazade" (que j'aime beaucoup pourtant), notamment avec les [SIZE=3]&#1571; [/SIZE]qui sont souvent reliés à la lettre suivante par un trait disgracieux, mais dans l'ensemble, ça commence à marcher correctement !
[SIZE=3]&#1605;&#1593; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605;&#1577;[/SIZE]

---

