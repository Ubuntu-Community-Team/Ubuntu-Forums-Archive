---
title: "Dell Optiplex 330 : PC ne s'éteint pas"
date: 2008-12-28
forum: Tunisia Team
---

### Post by RachedTN on 2008-12-28
J'ai installé Ubuntu 8.04 sur un dell Optiplex 330
Le problème c'est que l'ordinateur ne s'éteint pas.
je n'ai pas fais mise à jour puisqu'il n'y a pas de connexion internet, j'ai rechercher sur le net, mais la plupart de lien me conduit vers : forum.ubuntu.fr qui est hors service maintenant !
donc : Help, svp :)

---

### Post by RachedTN on 2008-12-28
Problème résolu, voici la procédure : 
sudo gedit /boot/grub/menu.lst

remplacer la ligne suivante:
# defoptions=quiet splash locale=fr_FR
par la ligne suivante :
defoptions=quiet splash locale=fr_FR reboot=b

enrgistrer

et enfin taper dans le terminal :
sudo update-grub

et voilà : le PC s'éteint tranquillement

Plus de détails : [http://ubuntuforums.org/showthread.php?t=905746](http://ubuntuforums.org/showthread.php?t=905746)
                  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293372](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293372)
                  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115906/comments/11](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115906/comments/11)

Note : vous remarquez que j'ai enlevé le #, dans d'autres forums il vous disent de ne pas l'enlever : c'est à vous de tester.

---

### Post by RachedTN on 2009-01-02
Après la mise à jour de Ubuntu8.04, c'est le même problème qui retourne : le PC dell optiplex 330 ne s'éteint pas et ne rédemarre pas aussi : il reste bloquer.
J'ai donc efectuer la même procédure qu'auparavant : cette fois ci il s'éteint, mais ne rédemarre pas.
Pour ceux qui se demandent c'est quoi le message que j'obtent après la modification de fichier menu.lst et l'éxécution de la comamnde : update-grub, voici le message : 
root@mahmoud-desktop:/home/mahmoud# vim /boot/grub/menu.lst
root@mahmoud-desktop:/home/mahmoud# gedit /boot/grub/menu.lst
root@mahmoud-desktop:/home/mahmoud# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

la solution vient de nos amis de ubuntu-tn (Oussema et sua) (je ne l'ai pas encore tester car ce n'est pas mon PC) :

1. tu demarre le pc
   le menu du grub apparait
ensuite ..
2.le menu du grub apparait "Ubuntu ....."
3.tu tape e
4.tu tape e une deuxieme fois
5.avec la fleche tu va vers la fin de la ligne
6.tu ajoute reboot=b ou acpi=on ..
7.tu tapes Entrer
8.tu tapes b
9.linux se charge
10.arrete le pc pour voir si le prob et regler ou non 

Pour plus de détails, voici un extrait de la conversation de Oussema et sua sur le channel #ubuntu-tn sur le serveur irc.freenode.net :
<Oussema> en fait je pense que RachedTN veux essayer le reboot juste apres modifier le menu.lst
<Oussema> alors qu'il faut redemarrer -en hard c a d en appyuant sur la touche ON/OFF
<Oussema> puis redemarrer -et la
<Oussema> le kernel prendra cette option en compte
<Oussema> je pense que c'est un probleme avec le disque dur
<sua> non, je croix que rached à un message qui dit vous pouver éteindre le systeme maintenant
<sua> c'est lors que le gestionnaire d'alimentation n'est pas pris en compte par le kernel
<Oussema> emm
<sua> certin laptop on ce prob
<Oussema> ouais je dois ajouter cette option pour booter sur dsl
<sua> pour les kernel compiler directement sur machine, je sais pas si l'ajout de acpi=on après l'install marche ou non :/
<Oussema> ç adepend s'il a mis les driver du gestionneur d'alimentation en module ou non
<sua> généralement tout les tuto conceil de le désactiver
<sua> autre chose, si le acpi n'est pas compatible avec la machine alors RACHEDTNne pourra pas du tout booter XD
<Oussema> ouais xD
<sua> il est dans la m**** xD
<Oussema> non
<Oussema> il suffit qu'il appuie sur la touche RESET :)
<sua> j'ai été bon de lui demander de l'essai au stage 1.5 de grub
<Oussema> si le probeleme est evec le disque dur ,l'option :pci=nomsi devrait l'aider
<sua> ou changer le bios de sata à IDE
<Oussema> encore une fois il lui suffit d'appyuer sur RESET et d'enlever cette option depuis le grub
<Oussema> :)

conversation complète : [http://logs.ubuntu-eu.org/freenode/2008/12/31/%23ubuntu-tn.html]("http://logs.ubuntu-eu.org/freenode/2008/12/31/%23ubuntu-tn.html")
Merci tout le monde :)

---

