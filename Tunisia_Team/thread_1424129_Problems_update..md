---
title: "Problems update."
date: 2010-03-07
forum: Tunisia Team
---

### Post by WMDElite on 2010-03-07
Salut a tous,
    Mes cher amis(e),    J'utilise actuellement **Ubuntu 8.4** comme systeme d'exploitation.
    
   J'ai lancé la mise à jour de **Ubuntu 9.4**, mais il fallait [COLOR=Blue]**5_*h*_*_!_***[/COLOR] :-({|= pour que ce soit terminer alors j'ai annulée ](*,).Et maintenant il me semble que le systeme était abimer :-k,et je peut plus faire un mise a jour (même des paquets :cry:)


 :!: J'apprécierais vraiment votre aide afin que je puisse continuer à utiliser Ubuntu.

Ce sont les messages que je reçois quand je tente de mettre à jour les paquets:
:arrow:


:confused:[SIZE=4][U][B][COLOR=Red]Gestionniare de mise a jour:
[/COLOR][/B][/U][/SIZE]
**Impossible d'initialiser les données sur les paquets**

[B]Un problème insoluble est survenu pendant l'initialisation des informations du paquet.

Veuillez signaler ce bogue du paquet «update-manager» en y joignant le message d'erreur suivant:

'E:Encountered a section with no Package: header, E problem with MergeList /var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages, E:Les listes de paquets ou le fichier «status» ne peuvent être analysés ou lus.'
[/B]
:confused:[SIZE=4][B][COLOR=Red]Gestionnaire des paquets synaptic
[/COLOR][/B][/SIZE]
[B]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
E: Impossible d'ouvrir ou d'analyser le fichier contenant la liste des états ou celui des paquets disponibles.
E: _cache->open() failed, please report.       [/B]

---

### Post by Nizarus on 2010-03-08
salam WMDElite;
en fait tu as fait 2 erreurs en effectuant la mise à jour.
la première est qu'il ne faut pas sauter une version ubuntu en effectuant la mise à jour, si tu as la version 8.04 il faut passer à la version 8.10 puis 9.04 
la deuxième il ne faut pas interrompre une mise à jour si elle a commencée à installer les paquets (on peut l'interrompre quand elle télécharge les paquets)
La meilleure solution dans ton cas est de récupérer tes données dans une autre partition (si ton /home n'est pas dans une partition à part) et d'installer proprement la nouvelle version (la 9.10 par exemple).

---

### Post by Neo31 on 2010-03-08
Salut Nizarus,
Je n'ai pas repondu hier parce que apres ses deux fautes qu'il a fait, j'ai penser qu'il n'as pas utiliser une partition /home.
J'esperai qu'il y aurai une autre solution apart la recuperation des donnees.
Essaye de chercher encore un peu WMDElite, mais bon, je pense que Nizarus a raison. Il a proposer la meilleure solution.
dsl WMDElite, on doit apprendre de nos fautes, donc ces deux fautes la : a jamais refaire.

---

### Post by WMDElite on 2010-03-09
Salam a tous,
Merci pour me repondre a ce sujet, suis vraiment ravie d'etre ici avec vous.O:)



1)En faite, j'ai une partition a part qui s'appelle ( /home ),voila le resultat de la commande "ls" de mon root (/):

[COLOR=Gray]PS:les **** just, réfere a  mon nom(l'utilisateur en cour,et ce n'est pas vraiment important ;))[/COLOR]

[B][COLOR=DarkGreen]****@****-laptop:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  [COLOR=Red]home[/COLOR]  lib             mnt         root  srv      usr  vmlinuz.old[/COLOR][/B]

J'espère ca va aider pour garder mais donner (safe).

 2) [COLOR=Red]Mais[/COLOR], est ce que il est possible de corriger ces 2 Erreur ( #-ofatal je disait ) avec une restoration du système . 
  Parceque si Ubuntu ,par chance, a fait une sauvgarde automatique(point de restoration) ,avant qu'il soit abimer ,ca serait mieux que de formater toute la machine.
Si ce que je dit est possible . S'il vous plait reseigner mois a comment le faire.


:popcorn:Merci d'avance.
[COLOR=Silver]---------------------------------------[/COLOR]
Be free , get Ubuntu!

[www.**ubuntu**]("http://www.%3cb%3eubuntu%3c/b%3E").com/
[www.**ubuntu**]("http://www.%3cb%3eubuntu%3c/b%3E").com/Get**Ubuntu**/download

---

### Post by WMDElite on 2010-03-09
Salut ,

C'est moi encore mais cette fois avec une bonne et mauvaise nouvelle

En vas commencer avec la bonne nouvelle :

1) Ma problème est resolut maintenat ,je peut faire les mises a jour:guitar:

Mais comment ta fait ?? :) 
Et bah , le voila ,jai taper : sudo rm -vf /var/lib/apt/lists/* , sur terminal ,et boom!! , toute est resolut 

Voila ce que le système a effectuer :

[B]détruit `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages'
détruit `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_source_Sources'
détruit `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_Release'
détruit `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_Release.gpg'
détruit `/var/lib/apt/lists/lock'
rm: ne peut enlever `/var/lib/apt/lists/partial': est un dossier
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_source_Sources'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_source_Sources'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_Release'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_Release.gpg'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_source_Sources'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_universe_binary-i386_Packages'
détruit `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_universe_source_Sources'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_main_i18n_Translation-fr'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_i18n_Translation-fr'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_Release'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_Release.gpg'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_i18n_Translation-fr'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_source_Sources'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty_universe_i18n_Translation-fr'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty-updates_Release'
détruit `/var/lib/apt/lists/tn.archive.ubuntu.com_ubuntu_dists_jaunty-updates_Release.gpg'


2) [/B]Et maintenant la mauvaise nouvelle :

*Je sait même pas ce que fait cette commande,(oui ,c vrai , c stupide a faire) mais ca marcher.

Alors s'il vous plait. Queslqun peut m'expliquer qu'est ce que c'est passer?


:popcorn:Merci d'avance.

---

### Post by Neo31 on 2010-03-09
> **WMDElite said:**
> 1)En faite, j'ai une partition a part qui s'appelle ( /home ),voila le resultat de la commande "ls" de mon root (/):une partition /home n'est pas un simple dossier dont le chemin d'acces est /home, enfaite ca consiste a une partition du disque
  dure qui est montée dans le chemain /home d'ou tt les donnees et configurations des programmes que tu utilise sont stoquees sur cette partition et non pas la partition ou t'as monter le chemin root /
tu peut donner le resultat de cette commande pour savoir si tu a une partition home a part :
cat /etc/fstab

je m'excuse de ne pas repondre au dexieme message puisque je ne connais pas ce qui est stoque dans le chemain ou t'as executer la commande rm et que je n'ai pas assai de temps pour Googler pour le moment, inchalah qq1 d'autre pourra t'aider opur le deuxieme message, mais ce qui est bien c'est que tu as reussit a trouver le premier bout de file ;)

good luck

---

### Post by WMDElite on 2010-03-10
L'exécution de la commande sur terminal donne:

[B]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=61dc3691-cb49-4a4a-b645-646d26f51179 /               ext3    relatime,errors=remount-ro 0       1
[COLOR=Red]# /home was on /dev/sda3 during installation[/COLOR]
UUID=b041cbfb-ae52-4b6b-bcd7-65f5a2df6443 /home           ext3    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=fa8f6c05-1577-42a2-8446-5042a2052441 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[/B]Et bah ,justement jai une partition qui s'appelle /home [B]:)
[/B]
Merci pour la commande.Et jespère que quelq'un répond a la 2ème question.[B];)
[/B]

---

