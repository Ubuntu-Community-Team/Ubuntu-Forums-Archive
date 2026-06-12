---
title: "installer windows"
date: 2009-09-07
forum: Tunisia Team
---

### Post by dark of angel on 2009-09-07
sa77a chribetkom a tous les ubuntu
je veux c koi nécessaire pour avoir installer windows xp en dual boot sur ton PC après avoir installer ubuntu9.04 à100%100 sur 
et merci pour vos futurs réponses.

---

### Post by omrisaber on 2009-09-07
L'idéal c d'installer windows avant.
Pour ta situation, tu installes tout simplement windows dans une autre partition et tu **réinstalles** le chargeur de démarrage de ubuntu (boot loader - GRUB).

---

### Post by MaWaLe on 2009-09-08
Après avoir installé Ubuntu à 100%, l'installation de Windows (toutes versions confondues) entrainera l'écrasement du MBR (Master Boot Record). C'est sur le MBR que la majorité des cas le chargeur de Linux (qui est aussi un chargeur multi-boot gérant plusieurs systèmes au démarrage) et qui est par défaut le Grub pour Ubuntu, est installé. Donc l'écrasement de cet MBR entrainera non pas la désinstallation de Linux (comme certains le pensent puisqu'ils ne peuvent plus le voir au démarrage, mais le rendra juste inaccessible bien qu'il est présent sur le Disque Dur. C'est tout simplement que la première phase du démarrage de Linux qui fait intervenir le chargeur (loader) n'est plus exécuté du moment que ce dernier n'y est plus sur le MBR.

Donc pour revenir à la question principale : avoir Windows et Ubuntu en Dual Boot (bien que je ne vois pas l'intérêt mais je respecte le choix de la personne ): 
- Installer d'abord le Windows et ensuite installé Ubuntu : ainsi le chargeur (Grub) en s'installant sur le MBR prendra en charge directement le windows déjà présent et proposera les deux OS au choix du démarrage.
- Si Ubuntu est déjà installé et que la personne ne veut pas tout réinstaller : redimensionner la partition de Linux pour aménager un espace pour Windows, ensuite installer Windows mais il faudra penser à réinstaller le chargeur ou Loader (Grub) après avoir fini l'installation de windows sinon l'ordinateur démarrera toujours avec le Windows fraichement installé puisque le chargeur n'y est plus sur le MBR (comme expliqué précédemment).


Un dernier conseil : penser aux avantages de la virtualisation du Windows au lieu d'avoir un Dual Boot (je peux vous citer une LONGUE liste mais je vous laisse faire la recherche :p ou bien assister à nos events pour le découvrir ;) )

---

### Post by dark of angel on 2009-09-08
> **MaWaLe said:**
> Après avoir installé Ubuntu à 100%, l'installation de Windows (toutes versions confondues) entrainera l'écrasement du MBR (Master Boot Record). C'est sur le MBR que la majorité des cas le chargeur de Linux (qui est aussi un chargeur multi-boot gérant plusieurs systèmes au démarrage) et qui est par défaut le Grub pour Ubuntu, est installé. Donc l'écrasement de cet MBR entrainera non pas la désinstallation de Linux (comme certains le pensent puisqu'ils ne peuvent plus le voir au démarrage, mais le rendra juste inaccessible bien qu'il est présent sur le Disque Dur. C'est tout simplement que la première phase du démarrage de Linux qui fait intervenir le chargeur (loader) n'est plus exécuté du moment que ce dernier n'y est plus sur le MBR.

Donc pour revenir à la question principale : avoir Windows et Ubuntu en Dual Boot (bien que je ne vois pas l'intérêt mais je respecte le choix de la personne ): 
- Installer d'abord le Windows et ensuite installé Ubuntu : ainsi le chargeur (Grub) en s'installant sur le MBR prendra en charge directement le windows déjà présent et proposera les deux OS au choix du démarrage.
- Si Ubuntu est déjà installé et que la personne ne veut pas tout réinstaller : redimensionner la partition de Linux pour aménager un espace pour Windows, ensuite installer Windows mais il faudra penser à réinstaller le chargeur ou Loader (Grub) après avoir fini l'installation de windows sinon l'ordinateur démarrera toujours avec le Windows fraichement installé puisque le chargeur n'y est plus sur le MBR (comme expliqué précédemment).


Un dernier conseil : penser aux avantages de la virtualisation du Windows au lieu d'avoir un Dual Boot (je peux vous citer une LONGUE liste mais je vous laisse faire la recherche :p ou bien assister à nos events pour le découvrir ;) )

merci pour les informations

---

### Post by pr.nizar on 2009-09-17
> **MaWaLe said:**
> avoir Windows et Ubuntu en Dual Boot (_bien que je ne vois pas l'intérêt.._)
Y a pas qu'un seul intérêt.. Y en a plein! Pour ceux qui ne se sont pas à 100% familiarisé avec l'univers Ubuntu Windows serait toujours là, profiter pleinement des deux systèmes d'exploitations, y a des solutions Windows dont l'équivalent Ubuntu n'existe pas tel que le célebressime **Internet Download Manager**! (Vous en connaissez un qui lui soit égal?:lolflag:)
> **MaWaLe said:**
> penser aux avantages de la virtualisation du Windows au lieu d'avoir un Dual Boot
Et penser aux inconvénients de la virtualisation: plus de charge, ralentissement.. par rapport à l'exécution native. [-X

Ma réponse (toute longue :guitar:) à la question (toute courte :-({|=) serait:

A partir d'Ubuntu: (se préparer au pire :lolflag:)
1.  **sauvez vos données sur un support externe** (DVD, clé USB, disque externe, etc.).
2. **sauvez votre MBR sur un support externe**:
à partir d'un Live CD
tapez dans Terminal: 
```
sudo dd if=/dev/sda of=~/Bureau/mbr512.img bs=512 count=1
```
ou si c'est en anglais:
```
sudo dd if=/dev/sda of=~/Desktop/mbr512.img bs=512 count=1
```
Un fichier nommé mbr512.img devrait se trouver sur votre bureau; gardez-le en lieu sûr (DVD, clé USB, disque externe, etc.).
3. **sauvez votre répertoire /home sur un support externe**
4. **préparez votre disque dur en créant la partition qui recevra Windows**: Celle-ci doit être une partition principale (primaire), et de préférence en début de disque (sda1 par exemple).
(Dans votre Terminal:
```
sudo gparted
```
si gparted n'est pas installé pour l'installer:
```
sudo apt-get install gparted
```
puis refaire la manipulation pour accéder à gparted et partitionner le disque. Epargnez la partition où est installé Ubuntu bien-entendu)
5. **Installation de Windows**: ça effacera votre MBR et il y a de forte chance que ça efface aussi votre Ubuntu mieux vaut vous prévenir! :lolflag:
6. **Ré-installation d'un menu de démarrage sur le MBR**:
A partir d'un LiveCD, il faut monter votre partition Ubuntu, afin de pouvoir y retrouver les fichiers de GRUB.
```
$ sudo mkdir /mnt/root
$ sudo mount -t ext3 /dev/sdXY /mnt/root
```
(ou vfat au lieu de ext3 au cas où la partition sur laquelle est installée Ubuntu est formatée en fat32.. et où sdXY est votre partition Ubuntu, vous pouvez la retrouver en tapant:
```
sudo fdisk -l
```)
Montez ensuite les sous-systèmes de fichiers proc et udev sous /root
```

$ sudo mount -t proc none /mnt/root/proc
$ sudo mount -o bind /dev /mnt/root/dev

```
Procéder ainsi permet à GRUB de trouver et reconnaître vos disques/partitions. Ensuite, vous avez à changer de dossier racine:
```
sudo chroot /mnt/root /bin/bash
```
Maintenant que vous êtes en chroot sur votre partition montée:
```
sudo grub
```
Vous voilà dans le menu principal de grub:
```
find /boot/grub/stage1
```
Cette commande vous indiquera la partition sur laquelle sont situés ces fichiers. La réponse est de la forme (hdX,Y) où X et Y sont des nombres entiers positifs.
Tapez:
```
root (hdX,Y)
```
ensuite:
```
setup (hd0)
```
puis quittez grub:
```
quit
```
Voilà. Il ne reste plus qu'à redémarrer et GRUB apparaîtra à nouveau.
Il se peut que Windows n'apparaisse pas dans GRUB à ce point; il suffira de l'ajouter par la suite.

Bibliographie:

[LIST]
[*][http://doc.ubuntu-fr.org/comment_installer_windows_sans_perdre_ubuntu](http://doc.ubuntu-fr.org/comment_installer_windows_sans_perdre_ubuntu)
[*][http://doc.ubuntu-fr.org/tutoriel/comment_recuperer_ubuntu_apres_installation_windows](http://doc.ubuntu-fr.org/tutoriel/comment_recuperer_ubuntu_apres_installation_windows)
[*][http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub](http://doc.ubuntu-fr.org/tutoriel/comment_restaurer_grub)
[*][http://doc.ubuntu-fr.org/cohabitation_ubuntu_windows](http://doc.ubuntu-fr.org/cohabitation_ubuntu_windows)
[*][http://doc.ubuntu-fr.org/gparted](http://doc.ubuntu-fr.org/gparted)
[/LIST]
P.S:

[LIST]
[*]Si tu as besoin de redimensionner une de tes partition je te propose cette [lecture]("http://gparted.sourceforge.net/larry/resize/resizing-fr.htm") mais n'oublie pas de faire deux défregmentations (pour les partitions Windows) avant de faire un redimensionnement c'est essentiel sinon y aura risque de perte d'information!!! ;)
[*]Si tu as un [disque tatoué]("http://doc.ubuntu-fr.org/windows/pc_tatoue") et que tu veux garder ton MBR intacte je te conseille cette [lecture]("http://doc.ubuntu-fr.org/tutoriel/comment_faire_multiboot_propre_2_dd").
[*]Si cette méthode ne marche pas ne m'en veux pas et re-installe Ubuntu t'as toujours tes sauvegardes n'est-ce pas?! :lolflag:
[/LIST]

---

