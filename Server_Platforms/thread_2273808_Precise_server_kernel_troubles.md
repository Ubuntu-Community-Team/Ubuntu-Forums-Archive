---
title: "Precise server kernel troubles"
date: 2015-04-15
forum: Server Platforms
---

### Post by electronico_nc on 2015-04-15
Hi all,

Got an old Precise server that have been setup by someone else.
Main problem is that /boot has been setup too small (256MB).

Current kernel is:
```
uname -a
Linux CCC 3.2.0-77-generic-pae #112-Ubuntu SMP Tue Feb 10 15:41:09 UTC 2015 i686 i686 i386 GNU/Linux
```
/boot has been filled up to 100% when an automatic kernel upgrade occured (was 3.2.0.79.93) but kernel hasn't been completely installed.
I made some space on /boot by manually removing 3.2.0.67 3.2.0.68 3.2.0.70 files, then launched a:```
upgrade-grub
```
Badly (my fault ...) I launched a dist-upgrade that tried to install 3.2.0.80, but 3.2.0.79 was not complete.
Downloaded linux-image-3.2.0-79-generic-pae_3.2.0-79.115_i386.deb and installed it with dpkg.

Now :```
apt-get dist-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt-get -f install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 linux-generic-pae : Dépend: linux-image-generic-pae (= 3.2.0.79.93) mais 3.2.0.80.94 est installé
                     Dépend: linux-headers-generic-pae (= 3.2.0.79.93) mais 3.2.0.80.94 est installé
E: Dépendances manquantes. Essayez d'utiliser l'option -f.
```
```
# apt-get autoremove
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt-get -f install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 linux-generic-pae : Dépend: linux-image-generic-pae (= 3.2.0.79.93) mais 3.2.0.80.94 est installé
                     Dépend: linux-headers-generic-pae (= 3.2.0.79.93) mais 3.2.0.80.94 est installé
E: Dépendances manquantes. Essayez d'utiliser l'option -f.
```
```
# apt-get -f install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Correction des dépendances... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  linux-headers-3.2.0-70 linux-headers-3.2.0-72 linux-headers-3.2.0-67 linux-headers-3.2.0-68 linux-headers-3.2.0-74 linux-headers-3.2.0-69
  linux-headers-3.2.0-75 linux-headers-3.2.0-76 linux-headers-3.2.0-72-generic-pae linux-headers-3.2.0-67-generic-pae
  linux-headers-3.2.0-75-generic-pae linux-headers-3.2.0-68-generic-pae linux-headers-3.2.0-70-generic-pae linux-headers-3.2.0-76-generic-pae
  linux-headers-3.2.0-74-generic-pae linux-headers-3.2.0-69-generic-pae
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  linux-generic-pae
Les paquets suivants seront mis à jour :
  linux-generic-pae
1 mis à jour, 0 nouvellement installés, 0 à enlever et 30 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/1 730 o dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
dpkg : des problèmes de dépendances empêchent la configuration de linux-generic-pae :
 linux-generic-pae dépend de linux-image-generic-pae (= 3.2.0.79.93) ; cependant :
  La version de linux-image-generic-pae sur le système est 3.2.0.80.94.
 linux-generic-pae dépend de linux-headers-generic-pae (= 3.2.0.79.93) ; cependant :
  La version de linux-headers-generic-pae sur le système est 3.2.0.80.94.
dpkg : erreur de traitement de linux-generic-pae (--configure) :
 problèmes de dépendances - laissé non configuré
Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                                Des erreurs ont été rencontrées pendant l'exécution :
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Additionnal infos:
```
# df
Sys. de fichiers     1K-blocs  Utilisé Disponible Uti% Monté sur
/dev/mapper/CCC-root 78201808 27191148   47038156  37% /
udev                   111508       12     111496   1% /dev
tmpfs                   24052      500      23552   3% /run
none                     5120        0       5120   0% /run/lock
none                   120256        0     120256   0% /run/shm
/dev/sda1              233191   179305      41445  82% /boot

```
```
# dpkg -l linux-* | awk '/^ii/{ print $2}'
linux-firmware
linux-headers-3.2.0-67
linux-headers-3.2.0-67-generic-pae
linux-headers-3.2.0-68
linux-headers-3.2.0-68-generic-pae
linux-headers-3.2.0-69
linux-headers-3.2.0-69-generic-pae
linux-headers-3.2.0-70
linux-headers-3.2.0-70-generic-pae
linux-headers-3.2.0-72
linux-headers-3.2.0-72-generic-pae
linux-headers-3.2.0-74
linux-headers-3.2.0-74-generic-pae
linux-headers-3.2.0-75
linux-headers-3.2.0-75-generic-pae
linux-headers-3.2.0-76
linux-headers-3.2.0-76-generic-pae
linux-headers-3.2.0-77
linux-headers-3.2.0-77-generic-pae
linux-headers-3.2.0-79
linux-headers-3.2.0-79-generic-pae
linux-headers-3.2.0-80
linux-headers-3.2.0-80-generic-pae
linux-headers-generic-pae
linux-image-3.2.0-67-generic-pae
linux-image-3.2.0-68-generic-pae
linux-image-3.2.0-69-generic-pae
linux-image-3.2.0-70-generic-pae
linux-image-3.2.0-72-generic-pae
linux-image-3.2.0-74-generic-pae
linux-image-3.2.0-75-generic-pae
linux-image-3.2.0-76-generic-pae
linux-image-3.2.0-77-generic-pae
linux-image-3.2.0-79-generic-pae
linux-image-3.2.0-80-generic-pae
linux-image-generic-pae
linux-libc-dev
```

I don't have a physical access to this server and I'm sure the new kernels (79 & 80) are not installed correctly, so a "reboot to test" is not possible.

Could you please assist a bit with this ?
Thanks a lot in advance.
Nicolas

---

### Post by Doug S on 2015-04-16
> **electronico_nc said:**
> I made some space on /boot by manually removing 3.2.0.67 3.2.0.68 3.2.0.70 files, What do you mean by "manually"? Do you mean:```
sudo dpkg -r linux-headers-3.2.0-67-generic-pae
sudo dpkg -r linux-headers-3.2.0-67
sudo dpkg -P linux-image-3.2.0-67-generic-pae
sudo dpkg -r linux-headers-3.2.0-68-generic-pae
sudo dpkg -r linux-headers-3.2.0-68
sudo dpkg -P linux-image-3.2.0-68-generic-pae
sudo dpkg -r linux-headers-3.2.0-69-generic-pae
sudo dpkg -r linux-headers-3.2.0-69
sudo dpkg -P linux-image-3.2.0-69-generic-pae
sudo dpkg -r linux-headers-3.2.0-70-generic-pae
sudo dpkg -r linux-headers-3.2.0-70
sudo dpkg -P linux-image-3.2.0-70-generic-pae

```

---

### Post by electronico_nc on 2015-04-21
Sorry, for the late answer, I have not been informed of your answer via email.

I haven't used dpkg to remove files, just basic "rm".
I have now run the dpkg commands that you posted.
Unfortunately problem is still there :```
uname -a
Linux CCC 3.2.0-77-generic-pae #112-Ubuntu SMP Tue Feb 10 15:41:09 UTC 2015 i686 i686 i386 GNU/Linux
```
```
LANG="en_US" apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.79.93) but 3.2.0.80.94 is installed
                     Depends: linux-headers-generic-pae (= 3.2.0.79.93) but 3.2.0.80.94 is installed
E: Unmet dependencies. Try using -f.
``````
LANG="en_US" apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-72 linux-headers-3.2.0-74 linux-headers-3.2.0-75 linux-headers-3.2.0-76 linux-headers-3.2.0-72-generic-pae linux-headers-3.2.0-75-generic-pae
  linux-headers-3.2.0-76-generic-pae linux-headers-3.2.0-74-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae
The following packages will be upgraded:
  linux-generic-pae
1 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1730 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_CTYPE = "fr_FR.UTF-8",
    LC_COLLATE = "fr_FR.UTF-8",
    LC_MESSAGES = "fr_FR.UTF-8",
    LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Ne peut initialiser LC_ALL à la locale par défaut: Aucun fichier ou dossier de ce type
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.79.93); however:
  Version of linux-image-generic-pae on system is 3.2.0.80.94.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.79.93); however:
  Version of linux-headers-generic-pae on system is 3.2.0.80.94.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Thanks a lot for your time !
Nicolas

---

### Post by TheFu on 2015-04-21
Don't know how much any of this will help, but ... 

Manually removing files will break APT. Don't do it - ever. This is a valuable lesson.  I did over a decade ago. The system was never the same again, but I wasn't removing kernels and didn't keep track of what I removed to put it back.

There is a "feature" that leaves old kernels around. Around 2010 that "feature" appeared in Ubuntu (don't know about other distros).  They are never automatically removed. Perhaps in 14.04 and later, this "feature" has been removed? I'm in the habit of running a kernel-cleanup script now that keeps the last 3 kernels.

The default size for /boot is always too small, IMHO.  It only happens when LVM or encryption are selected during the installation process. Most people will NOT say "do something else" during the install and fix the partition sizes. It is further complicated by EFI. If LVM and encryption aren't selected, a separate /boot partition will not be created, so having 30 kernels isn't usually a problem with a 20G / partition.

So ... first task is to convince APT that everything is OK.  Perhaps the **apt-get --force remove {kernel-version} ** option will work with the remove commands?
Also, **aptitude** is smarter than apt-get about trying to resolve dependency issues. Don't think it will help you today, but for the future.

Going forward, it is important to [clean up old kernels]("http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt") and there are other things needed to [keep a Linux machine happy]("http://blog.jdpfu.com/linsysmaint").

---

### Post by matt_symes on 2015-04-21
Hi

Linux kernel headers are stored under /usr/src on a default Ubuntu install. This will be on your main LVM partition and not on the /boot partition.

You need to uninstall some of the kernel images to release space on /boot not the header files..

Let's delete a couple, fix your system and then look at deleting some more.

```
sudo dpkg -P linux-image-3.2.0-7{0,2,4,5}-generic-pae
```

If that goes well then to fix your current system...

```
sudo apt-get -f install
```

and to remove unneeded packages.

```
sudo apt-get autoremove
```

After that post back the output of 

```
uname -a
```

and we'll take a look to see where you are.

Kind regards

---

