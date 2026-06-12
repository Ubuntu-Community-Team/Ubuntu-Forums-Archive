---
title: "Probleme d'installation de ubuntu"
date: 2009-04-23
forum: Tunisia Team
---

### Post by nounouING on 2009-04-23
salut les menbres de groupe ubuntu-tn
1) J'ai essayée d'installer ubuntu 8.10 sur mon laptop. Les étapes d'installation sont bien passées mais lorsque je connect avec l'utilisateur de mon système j'entend  un son pour dire que l'authentification est réussi puis un écran noir qui s'affiche même j'ai attendu 30min et rien n'a changé l'écra noir reste le même.
2) une de mes collégues à essayé d'installer ubuntu mais à un certain niveau d'installation (70%) l'installation s'arrête puis une session Live s'ouvre. 
S'il vous plait aider moi à résoudre ses deux problèmes.
Merci d'avance pour votre aide.

---

### Post by omrisaber on 2009-04-23
> **nounouING said:**
> salut les menbres de groupe ubuntu-tn
2) une de mes collégues à essayé d'installer ubuntu mais à un certain niveau d'installation (70%) l'installation s'arrête puis une session Live s'ouvre. 


Pour le problème 2, il est fort probable que le CD soit défectueux (d'ailleurs lorsque l'installation s'interrompe, un message vous indique que certains fichiers ne sont pas lisibles et probablement le CD est défectueux)
--> la sol°: 
-vérifier l'intégrité du fichier iso (MD5)
-si le fichier iso est sain, graver le à bas vitesse (4x ou moins)

Pour le 1er problème j'en suis pas expert :lolflag:

---

### Post by alaya.zied on 2009-04-24
pour le problème 1: vaut mieux que tu essaye Ubuntu 9.04, il est super

---

### Post by a.med on 2009-04-24
Salut
J'avais recontré des problèmes semblables à les votre, mais avec Knoppix (basée elle aussi sur Debian) en Live-CD (c.a.d. sans installation).
Mes problèmes étaient, d'une part, à cause d'un CD défectueux et d'autre part, je n'ai pas fait attention au bon choix de la résolution de l'écran).

Pour votre problème N°1, il vaut mieux nous transmettre plus de détails:
1- Etes- vous certain de la bonne qualité du CD?
2- Avez-vous essayé Ubuntu en Live-CD avant l'installation?
    Ce point vous permettra de vérifier la compatibilité de votre matériel, surtout, pour votre cas, le pilote de l'affichage graphique.
3- Avez-vous suivi correctement les étapes de l'installation?

Pour votre problème N°2, je vous conseille, comme l'a dit omrisaber, d'utiliser un autre CD.
Je vous conseille l'installation de Jaunty 9.04 et n'oubliez pas, si vous avez résolu vos problèmes de nous tenir au courant.

---

### Post by nounouING on 2009-04-25
Salut 
Pour le premier problème j'ai essayée le CD Live et il fonctionne normal. J'ai suis les étapes correctement et le CD j'ai commandée à partir du site de Ubuntu.
Pour le 2ème problème, Le CD n'est pas défectueux. On a fait la vérification de CD. Il n'y a pas de message d'erreur qui s'affiche lors de la coupure de l'installation et il passe directement en mode Live.
Merci d'avance pour votre aide.

---

### Post by omrisaber on 2009-04-26
- Tu peux nous informer plus à propos de votre ordinateur (marque...)
- As tu essayer encore la nouvelle version 9.04 ? (plusieurs bugs ont été corrigés :))

---

### Post by Nizarus on 2009-04-26
as tu essayé avec la nouvelle version de ubuntu ?

---

### Post by a.med on 2009-04-26
Bonjour,
Nous allons nous efforcer de vous aider, mais il faut que vous nous donniez quelques indices, par exemple:
- Le type de votre laptop
- l'architecture (amd ou intel - 32/64 bits)
- le type de votre carte graphique
- Il s'agit d'un dual boot (avec XP /vista) ? Est-ce que Grub s'affiche vous donnant le choix entre les systèmes installés? ou c'est une installation dans Windows comme s'il s'agit d'une application? ou bien encore vous êtes en train de tester Ubuntu sur une machine virtuelle?
- En dual boot, avez-vous laissé, AVANT de commencer l'installation, une partition vide? parce que l'installation sur la même partition que windows est catastrophique!
- Comment avez-vous partitionné votre hdd ? Vous avez gardé les options par défaut ou vous avez utilisé les options avancées? 
- En dual boot, est-ce que vous accédez normalement à votre système windows?
- ......................
=====================================
Voilà quand-même quelques indices que j'ai pu récupéré d'Internet:
- Pour le problème de votre laptop, lisez cette page:
[http://doc.ubuntu-fr.org/portable](http://doc.ubuntu-fr.org/portable)
- Pour les autres composantes:
[http://doc.ubuntu-fr.org/materiel](http://doc.ubuntu-fr.org/materiel)
- Pour récupérer les partitions créées par Ubuntu, c.a.d., effacement de Ubuntu de votre disque dur:
[http://doc.ubuntu-fr.org/desinstallation](http://doc.ubuntu-fr.org/desinstallation)

Mais lisez donc mon mésaventure avec Linux à la page:
[http://ubuntuforums.org/showthread.php?t=1134345](http://ubuntuforums.org/showthread.php?t=1134345)
J'ai perdu trop d'années avant d'apprendre ce merveilleux système solide, sécurisé et libre. Maintenant, je ne m'en passe plus. Pourquoi donc faire la même erreur?

Mon conseil est de rechercher auprès de vous quelqu'un qui a une bonne connaissance de Linux et de lire l'excellent livre " Simple comme Ubuntu", en libre téléchargement sur:
[http://www.framabook.org/](http://www.framabook.org/)
Si vous êtes résident en France, vous pouvez l'acheter auprès d'une librairie (j'aime encore le papier, c'est plus sentimental!)
Tenez-nous au courant de votre aventure, c'est cool :lolflag:

---

### Post by nounouING on 2009-04-27
salut 
Mon Laptop est Fujitsu Simens Amilo Pro V 2060. 
Disque dur: 120 G0, RAM 512, Carte Graphique: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller. 
En dual boot avec Windows XP SP2. le grup s'afffiche pour me donner le choix entre les systèmes d'exploitation installés. J'ai laissé une partion vide de taille 15GO pour installer ubuntu et lors de l'installaton j'ai choisi le mode manuel pour le partionnement de l'espace libre désiré.
Les partions sont comme suit : /boot=200MO, /home= 3000MO, /=8000M0, swap= le reste du l'espace de la partion réservée.
Je peux booter sur Windows. 
j'ai pas encore essayé le ubuntu 9.04 puisque j'ai pas plus de temps et j'ai un projet à realiser pour terminer mes étude. Mais j'ai installée fedora 9 pour travailler.
Merci d'avance pour votre aide

---

### Post by a.med on 2009-04-27
Salut
Au niveau materiel, tu ne devras avoir AUCUN problème.:P
Ta carte graphique est supportée depuis Drapper (6.06 LTS). Elle doit l'être sous Intrepid.
Le partitionnement est correct. Tu as réservé beaucoup d'espace pour le swap (à mon avis, 3.8 Go c'est trop !! par contre 3 Go pour le home c'est peu) mais ça ne cause aucun problème.:)
Donc, il ne vous reste que de vérifier l'integrité du CD !:confused:
Pour cela, tu dois utiliser une petite application nommée MD5. 
Une aide et des liens pour télécharger (c'est très leger) en suivant le lien suivant:
[http://www.commentcamarche.net/faq/sujet-41-md5sum-verifier-l-integrite-des-telechargements](http://www.commentcamarche.net/faq/sujet-41-md5sum-verifier-l-integrite-des-telechargements)
Puisque tu dis que tu as Ubuntu 8.10 (Desktop),Le résultat doit correspondre EXACTEMENT (sans tenir compte des minuscules/majuscules) à:
```
[COLOR=Blue]24ea1163ea6c9f5dae77de8c49ee7c03[/COLOR]
```Si ce n'est pas le cas, ton fichier ISO est altérée :(. La seule solution est de télécharger Jaunty (9.04).
(Tu peux en créer une autre ISO à partir du CD si tu as effacé la première, mais pas avec Nero! celui-ci crée une image propriétaire de type nrg. Sous Xp, il y a UltraIso, mais c'est payant. Sous fedora c'est possible avec K3B par exemple.
Bonne chance pour tes études et tiens-nous au courant:lolflag:

---

### Post by nounouING on 2009-05-02
Salut 
* Pour le 2eme problème de coupure de l'installation de ubuntu ou fedora est résolue. Mon collégue à changé la partition du disque. La partition initial du disque est défectueuse.
Merci pour votre aide

---

### Post by RachedTN on 2009-05-03
> **nounouING said:**
> Salut 
* Pour le 2eme problème de coupure de l'installation de ubuntu ou fedora est résolue. Mon collégue à changé la partition du disque. La partition initial du disque est défectueuse.
Merci pour votre aide

Une petite question : comment t'as jugé que la partition initial du disque est défectueuse ? t'as utilisé un outil pour vérifier, ou bien comment ?
Heureux que le problème est résolu :)

---

### Post by nounouING on 2009-05-04
Salut Rached
Ma collégue a  essayée plusieurs fois la version de ubuntu 8.10 à partir des différents CD et aussi d'autre distribution comme Suse 11 et Fedora (9 et 10) et elle a eu des problème lors de l'installation.
Par la suite on a conclus que la partiotion du disque utilisé est défectueuse.
Merci Rached.

---

