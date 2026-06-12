---
title: "Why can't I update ?"
date: 2011-04-27
forum: Server Platforms
---

### Post by NarsilAnduril on 2011-04-27
Hi folks,

I never noticed this strange issue :

At login (thru ssh  on a Ubuntu 10.04 server), I get a :

```
120 packages can be updated.
74 updates are security updates.
```

but then :
```
pinguin@cerise:~$ sudo apt-get update && sudo apt-get upgrade
...
0 mis à jour, 0 nouvellement installés, 0 à enlever et 4 non mis à jour.
```

Nothing's updated !

What's wrong with me ? Could someone help please ?

Thanks

Diego

---

### Post by arrrghhh on 2011-04-27
Post your /etc/apt/sources.list.  Also, could you post the complete list of what happens after that apt-get update command?  Don't snip, thanks!

---

### Post by NarsilAnduril on 2011-04-27
Ok, here we go :

sources.list :

```
# 
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ch.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ch.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ch.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

```
diego@desktop:~$ ssh pinguin@172.26.155.2
pinguin@172.26.155.2's password: 
Linux cerise 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed Apr 27 21:26:50 CEST 2011

  System load:    0.0              Memory usage: 3%   Processes:       89
  Usage of /home: 0.0% of 1.79TB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Wed Apr 27 18:44:33 CEST 2011

  System load:    1.01             Memory usage: 1%   Processes:       109
  Usage of /home: 0.0% of 1.79TB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at https://landscape.canonical.com/

120 packages can be updated.
74 updates are security updates.

Last login: Wed Apr 27 20:18:15 2011 from 172.26.155.17
pinguin@cerise:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for pinguin: 
Atteint http://ch.archive.ubuntu.com lucid Release.gpg
Atteint http://ch.archive.ubuntu.com/ubuntu/ lucid/main Translation-fr
Atteint http://ch.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-fr
Atteint http://ch.archive.ubuntu.com/ubuntu/ lucid/universe Translation-fr
Atteint http://ch.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-fr
Réception de*: 1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-fr
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-fr                          
Réception de*: 2 http://ch.archive.ubuntu.com lucid-updates Release.gpg [198B]                           
Atteint http://archive.canonical.com lucid Release.gpg                                                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-fr  
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-fr
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-fr
Réception de*: 3 http://security.ubuntu.com lucid-security Release [44.7kB]                              
Atteint http://archive.canonical.com lucid Release                                                       
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-fr                         
Atteint http://archive.canonical.com lucid/partner Packages        
Atteint http://archive.canonical.com lucid/partner Sources         
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-fr
Réception de*: 4 http://security.ubuntu.com lucid-security/main Packages [183kB]
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-fr
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-fr
Atteint http://ch.archive.ubuntu.com lucid-backports Release.gpg
Réception de*: 5 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Réception de*: 6 http://security.ubuntu.com lucid-security/main Sources [54.2kB]                
Réception de*: 7 http://security.ubuntu.com lucid-security/restricted Sources [14B]             
Réception de*: 8 http://security.ubuntu.com lucid-security/universe Packages [70.1kB]       
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-fr                
Réception de*: 9 http://security.ubuntu.com lucid-security/universe Sources [20.5kB]
Réception de*: 10 http://security.ubuntu.com lucid-security/multiverse Packages [4'433B]     
Réception de*: 11 http://security.ubuntu.com lucid-security/multiverse Sources [1'753B]     
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-fr        
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-fr
Ign http://ch.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-fr
Atteint http://ch.archive.ubuntu.com lucid Release
Réception de*: 12 http://ch.archive.ubuntu.com lucid-updates Release [44.7kB]
Atteint http://ch.archive.ubuntu.com lucid-backports Release  
Atteint http://ch.archive.ubuntu.com lucid/main Packages      
Atteint http://ch.archive.ubuntu.com lucid/restricted Packages
Atteint http://ch.archive.ubuntu.com lucid/main Sources
Atteint http://ch.archive.ubuntu.com lucid/restricted Sources
Atteint http://ch.archive.ubuntu.com lucid/universe Packages
Atteint http://ch.archive.ubuntu.com lucid/universe Sources
Atteint http://ch.archive.ubuntu.com lucid/multiverse Packages
Atteint http://ch.archive.ubuntu.com lucid/multiverse Sources
Réception de*: 13 http://ch.archive.ubuntu.com lucid-updates/main Packages [486kB]
Réception de*: 14 http://ch.archive.ubuntu.com lucid-updates/restricted Packages [3'267B]
Réception de*: 15 http://ch.archive.ubuntu.com lucid-updates/main Sources [188kB]
Réception de*: 16 http://ch.archive.ubuntu.com lucid-updates/restricted Sources [1'443B]
Réception de*: 17 http://ch.archive.ubuntu.com lucid-updates/universe Packages [198kB]
Réception de*: 18 http://ch.archive.ubuntu.com lucid-updates/universe Sources [73.2kB]
Réception de*: 19 http://ch.archive.ubuntu.com lucid-updates/multiverse Packages [10.4kB]
Réception de*: 20 http://ch.archive.ubuntu.com lucid-updates/multiverse Sources [5'055B]
Atteint http://ch.archive.ubuntu.com lucid-backports/main Packages
Atteint http://ch.archive.ubuntu.com lucid-backports/restricted Packages
Atteint http://ch.archive.ubuntu.com lucid-backports/universe Packages
Atteint http://ch.archive.ubuntu.com lucid-backports/multiverse Packages
Atteint http://ch.archive.ubuntu.com lucid-backports/main Sources
Atteint http://ch.archive.ubuntu.com lucid-backports/restricted Sources
Atteint http://ch.archive.ubuntu.com lucid-backports/universe Sources
Atteint http://ch.archive.ubuntu.com lucid-backports/multiverse Sources
1'390ko réceptionnés en 2s (562ko/s) 
Lecture des listes de paquets... Fait
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été conservés*:
  landscape-common linux-headers-server linux-image-server linux-server
0 mis à jour, 0 nouvellement installés, 0 à enlever et 4 non mis à jour.
pinguin@cerise:~$ 

```

---

### Post by arrrghhh on 2011-04-27
Ok, thank you.

Nothing is jumping out at me - it seems you can hit ch.archive.ubuntu.com, I was thinking there might be some network issues and you can't reach the repo server - that doesn't seem to be the case.

I wonder if it's related to the 4 packages that were held back - ```
landscape-common linux-headers-server linux-image-server linux-server
```

I was hoping it was a simple network issue, but that doesn't appear to be the case.  I'll keep poking around, hopefully someone more knowledgeable than I responds ;).

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **arrrghhh said:**
> I wonder if it's related to the 4 packages that were held back - ```
landscape-common linux-headers-server linux-image-server linux-server
```

@arrrghhh me too (wondering if it's related to the 4 packages that were held back)..  But about to network issue ..? Not to sure, system is able to connect, read the packages.. with a useful respond.. **Edited**: (it seems that the repositories to which he is pointing  source.list, are down...?

@NarsilAnduril Try this:

```
sudo apt-get dist-upgrade
```

.. apply a kernel upgrade or some big changes.. that will require a restart to take effect.

---

### Post by NarsilAnduril on 2011-04-27
Well, a dist-upgrade did some work and updates the four 
```
landscape-common linux-headers-server linux-image-server linux-server
```
but the set of 120 updates to do is still here (after reboot).

```
pinguin@cerise:~$ sudo apt-get dist-upgrade
[sudo] password for pinguin: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
Les NOUVEAUX paquets suivants seront installés*:
  bc linux-headers-2.6.32-31 linux-headers-2.6.32-31-server linux-image-2.6.32-31-server
Les paquets suivants seront mis à jour*:
  landscape-common linux-headers-server linux-image-server linux-server
4 mis à jour, 4 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 42.6Mo dans les archives.
Après cette opération, 214Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? O
Réception de*: 1 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-31-server 2.6.32-31.61 [31.5MB]
Réception de*: 2 http://ch.archive.ubuntu.com/ubuntu/ lucid/main bc 1.06.95-2 [112kB]                                                              
Réception de*: 3 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main landscape-common 1.5.5.1-0ubuntu0.10.04.0 [226kB]                         
Réception de*: 4 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-31 2.6.32-31.61 [9'913kB]                            
Réception de*: 5 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-31-server 2.6.32-31.61 [791kB]                       
Réception de*: 6 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-server 2.6.32.31.37 [4'522B]                                
Réception de*: 7 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-server 2.6.32.31.37 [4'522B]                                        
Réception de*: 8 http://ch.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-server 2.6.32.31.37 [4'528B]                                  
42.6Mo réceptionnés en 19s (2'136ko/s)                                                                                                             
Préconfiguration des paquets...
Sélection du paquet linux-image-2.6.32-31-server précédemment désélectionné.
(Lecture de la base de données... 47611 fichiers et répertoires déjà installés.)
Dépaquetage de linux-image-2.6.32-31-server (à partir de .../linux-image-2.6.32-31-server_2.6.32-31.61_amd64.deb) ...
Done.
Sélection du paquet bc précédemment désélectionné.
Dépaquetage de bc (à partir de .../bc_1.06.95-2_amd64.deb) ...
Préparation du remplacement de landscape-common 1.5.0.1-0ubuntu0.10.04.0 (en utilisant .../landscape-common_1.5.5.1-0ubuntu0.10.04.0_amd64.deb) ...
Dépaquetage de la mise à jour de landscape-common ...
Sélection du paquet linux-headers-2.6.32-31 précédemment désélectionné.
Dépaquetage de linux-headers-2.6.32-31 (à partir de .../linux-headers-2.6.32-31_2.6.32-31.61_all.deb) ...
Sélection du paquet linux-headers-2.6.32-31-server précédemment désélectionné.
Dépaquetage de linux-headers-2.6.32-31-server (à partir de .../linux-headers-2.6.32-31-server_2.6.32-31.61_amd64.deb) ...
Préparation du remplacement de linux-headers-server 2.6.32.21.22 (en utilisant .../linux-headers-server_2.6.32.31.37_amd64.deb) ...
Dépaquetage de la mise à jour de linux-headers-server ...
Préparation du remplacement de linux-server 2.6.32.21.22 (en utilisant .../linux-server_2.6.32.31.37_amd64.deb) ...
Dépaquetage de la mise à jour de linux-server ...
Préparation du remplacement de linux-image-server 2.6.32.21.22 (en utilisant .../linux-image-server_2.6.32.31.37_amd64.deb) ...
Dépaquetage de la mise à jour de linux-image-server ...
Traitement des actions différées («*triggers*») pour «*install-info*»...
Traitement des actions différées («*triggers*») pour «*man-db*»...
Paramétrage de linux-image-2.6.32-31-server (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-server
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-server
Found initrd image: /boot/initrd.img-2.6.32-31-server
Found linux image: /boot/vmlinuz-2.6.32-21-server
Found initrd image: /boot/initrd.img-2.6.32-21-server
Found memtest86+ image: /boot/memtest86+.bin
done

Paramétrage de bc (1.06.95-2) ...

Paramétrage de landscape-common (1.5.5.1-0ubuntu0.10.04.0) ...

Paramétrage de linux-headers-2.6.32-31 (2.6.32-31.61) ...
Paramétrage de linux-headers-2.6.32-31-server (2.6.32-31.61) ...

Paramétrage de linux-headers-server (2.6.32.31.37) ...
Paramétrage de linux-image-server (2.6.32.31.37) ...
Paramétrage de linux-server (2.6.32.31.37) ...
Traitement des actions différées («*triggers*») pour «*python-central*»...

```

---

### Post by arrrghhh on 2011-04-27
> **NarsilAnduril said:**
> Well, a dist-upgrade did some work and updates the four 
```
landscape-common linux-headers-server linux-image-server linux-server
```
but the set of 120 updates to do is still here (after reboot).

```
sudo apt-get update
``` does the same as it did before...?

---

### Post by elico on 2011-04-27
dont use the dist-upgrade!!
you have 10.04 TLS this command will lead to upgrade the version to 10.10.
so it's only a very very last resort.

---

### Post by KegHead on 2011-04-27
Hi!

This is what I use;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

Advise

KegHead

---

### Post by egpetrich on 2011-04-27
This looks like a known side effect of a recent update. Your file /etc/motd.tail has acquired some bogus text. (The update copied /etc/motd to /etc/motd.tail, so now you see the real system status, followed by old system status including a message that you have pending updates.)

Just delete /etc/motd.tail, or replace it with more useful text. Man, this is turning into an annoying issue. Hardly a day goes by that someone doesn't report a problem tracing back to this issue.

---

### Post by NarsilAnduril on 2011-04-28
> **elico said:**
> dont use the dist-upgrade!!
you have 10.04 TLS this command will lead to upgrade the version to 10.10.
so it's only a very very last resort.

Don't confuse "atp-get dist-upgrade" and "do-release-upgrade".

[QUOTE=egpetrich]This looks like a known side effect of a recent update. Your file /etc/motd.tail has acquired some bogus text. (The update copied /etc/motd to /etc/motd.tail, so now you see the real system status, followed by old system status including a message that you have pending updates.)

Just delete /etc/motd.tail, or replace it with more useful text. Man, this is turning into an annoying issue. Hardly a day goes by that someone doesn't report a problem tracing back to this issue.[/QUOTE]

Didn't knew this file, deleting it solved the problem :

```
diego@desktop:~$ ssh pinguin@172.26.155.2
pinguin@172.26.155.2's password: 
Linux cerise 2.6.32-31-server #61-Ubuntu SMP Fri Apr 8 19:44:42 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

  System information as of Thu Apr 28 08:15:05 CEST 2011

  System load:    0.0              Processes:           89
  Usage of /home: 0.0% of 1.79TB   Users logged in:     0
  Memory usage:   3%               IP address for eth0: 172.26.155.2
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

Last login: Wed Apr 27 23:07:55 2011 from 172.26.155.17
pinguin@cerise:~$ 

```

Thanks everybody for your help !

---

### Post by Sal33m on 2011-04-28
It could be a proxy issue.

Have you tried using a direct connection?

If you are using a proxy, you'll need to check the 'Manual proxy configuration' box, type in your proxy and port and then authenticate. You can find this in Synaptic Package Manager -> Settings -> Preferences -> Network.

---

### Post by pinballwizard on 2011-04-28
> **elico said:**
> dont use the dist-upgrade!!
you have 10.04 TLS this command will lead to upgrade the version to 10.10.
so it's only a very very last resort.

I'm almost certain you have this wrong.

---

### Post by arrrghhh on 2011-04-28
> **egpetrich said:**
> This looks like a known side effect of a recent update. Your file /etc/motd.tail has acquired some bogus text. (The update copied /etc/motd to /etc/motd.tail, so now you see the real system status, followed by old system status including a message that you have pending updates.)

Just delete /etc/motd.tail, or replace it with more useful text. Man, this is turning into an annoying issue. Hardly a day goes by that someone doesn't report a problem tracing back to this issue.

I didn't know about this either, thanks!  Very odd issue...  Durn false positives!  ;)

---

### Post by elico on 2011-04-29
webmin sometimes showed me something like that and it wasnt updated.

edit:
posted about it  here
[http://ubuntuforums.org/showpost.php?p=10750282&postcount=3](http://ubuntuforums.org/showpost.php?p=10750282&postcount=3)

---

