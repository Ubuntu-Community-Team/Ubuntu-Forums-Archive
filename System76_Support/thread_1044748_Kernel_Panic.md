---
title: "Kernel Panic"
date: 2009-01-19
forum: System76 Support
---

### Post by louis-e on 2009-01-19
Hello I own a Pangolin perfomance since july 2008. Recently (after the last kernel upgrade i believe) I started having kernel panic (caps and scroll lock light start flashing and you ubuntu freeze completly) and browsing around the internet I cant seem to find a solution to this.

I am under hardy 8.04. The kernel panic seem to occur with internet browsing (firefox) but it also happened when I was using writer and bibus bibliographic database manager. 

Things I have tried so far

Reinstalling linux-backport-modules-hardy (with command apt-get --reinstall install linux-backport...)

Looked at the var\log\messages (included in this message) the last kernel panic occurred January 19th at 18h18. No obvious error message is present

Any ideas what might causes this? And how to fix it...

cheers
Louis

---

### Post by thomasaaron on 2009-01-20
Wow! Thank you for including all of the necessary info! I'll have a look at your logs and see what I can divine. :popcorn:

---

### Post by thomasaaron on 2009-01-20
> an 14 17:17:18 ubuntu pulseaudio[6114]: pstream.c: Failed to import memory block.
Jan 14 17:43:41 ubuntu -- MARK --
Jan 14 18:03:41 ubuntu -- MARK --
Jan 14 18:23:41 ubuntu -- MARK --
Jan 14 18:43:41 ubuntu -- MARK --
Jan 14 19:03:41 ubuntu -- MARK --
Jan 14 19:20:06 ubuntu kernel: [16301.118060] flyingtoasters[15035]: segfault at 164 rip 7f5dfc8a8d19 rsp 7fff08234310 error 4

There's nothing at 18:18 per se. However, I think your screensaver (Flyingtoasters) caused it. You probably have your screensaver set as random or flying toasters. Whichever, it is, change it.

Try "Ant Spotlight" for a while and see if the panic occurs again. I've never had any problems with that one.

If it does, include syslog, and we'll have a deeper look.

---

### Post by louis-e on 2009-01-20
But I found the flying toaster so funny :(

Ok I will try this and see what happens

thanks for the reply

Louis

---

### Post by louis-e on 2009-02-09
Hello, its me again. I seem to still be requiring some help with a few problems 

Well I set my screensaver to ant spotlight, but the kernel panic started to happen again after a few days. So I switched to blank, same thing

Right now I deactivated screen saver completely. I will see what happen next but it is starting to get annoying especially when I am working. I also noticed that the kernel panic ALWAYS happen at work which tend to lead me to think that it might be an issue with my connection to the wireless network or the proxy I use with it. Possible??

Another thing starting to happen more frequently is the shut down protocol sometime breaks completely. Meaning that when I shut down all I get is a black screen with a bunch of vertical color bars and I have to 'pull the plug' to shut down my computer. I unfortunately did not remember to note the time when it happened last...

So I included the system message logfile with this message. Last kernel panic, february 9th 2009 @ 14h46 

cheers
Louis

---

### Post by thomasaaron on 2009-02-09
This is in there twice...

> Feb  9 12:57:25 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Feb  9 13:16:29 ubuntu -- MARK --
Feb  9 13:36:29 ubuntu -- MARK --
Feb  9 13:54:09 ubuntu kernel: [  694.891287] npviewer.bin[8226]: segfault at f5a9d030 rip f7898540 rsp ffb50d3c error 4
Feb  9 14:16:29 ubuntu -- MARK --
Feb  9 14:36:29 ubuntu -- MARK --
Feb  9 14:58:44 ubuntu syslogd 1.5.0#1ubuntu1: restart.

...and looks like the flash plugin in firefox freezing up. Does the freeze happen only when you are in firefox?


This is in there once...

> Feb  6 16:48:03 ubuntu -- MARK --
Feb  6 17:08:03 ubuntu -- MARK --
Feb  6 17:28:03 ubuntu -- MARK --
Feb  6 17:33:08 ubuntu kernel: [ 3243.804344] qtiplot[8777]: segfault at 8 rip 7f3e349bdb43 rsp 7fff40380cd0 error 4
Feb  6 17:48:03 ubuntu -- MARK --
Feb  6 18:08:03 ubuntu -- MARK --
Feb  6 18:28:03 ubuntu -- MARK --

...and it must be the QTIPlot program you were using when it crashed? Has it ever crashed before when you were using it?

---

### Post by louis-e on 2009-02-11
Flash might be the problem. I am pretty sure firefox is always open when it freezes, but i will try to notice at the next one. I do know that flash does not display properly in firefox. Should i reinstall the drivers for flash? if yes I got these one:

In synaptic:
flashplugin-nonfree
libflashsupport

In firefox adds-on
Shockwaveflash 9.0 r152
and a bunch of other adds-on like realplayer, mplayer, Quicktime which might conflict 

any others?


For QTIplot often crashes since it is a beta. I use it only for specific stuff like plotting boxplots. So i can probably uninstall it or close everything else when using it


Any ideas on what I should look for with the vertical color bar on shut down problem?? I have not found anything on the internet on that specific issue

cheers
Louis

---

### Post by thomasaaron on 2009-02-11
Try...

sudo apt-get --purge-remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree


As for the vertical lines: Do they, by chance, only happen when shutting down AFTER resuming from suspend/hibernate.

---

### Post by louis-e on 2009-02-11
I will try those commands and see what happens.

As for vertical color bars I do not use suspend/hibernate function. I know there are some issues with that under ubuntu... Unless my computer suspend itself automatically like for example when I work on battery power and I rarely do that. 

Thanks for the support. I really appreciate your promptness.

cheers

---

### Post by thomasaaron on 2009-02-11
My best guess is there is some configuration somewhere that is messing up the shutdown process. I don't see anything in your logs that shows what it is. 

Does it do that every time you shut down, or is it intermittent?

---

### Post by louis-e on 2009-02-14
The color bars on shutdown appear on an intermitent frequency, but is happening more often now than before. I manage to get a syslog of when the problem happened. It was on february 13th around 20h00

---

### Post by thomasaaron on 2009-02-16
Yours is an nVidia machine, right?

If so,let's try re-installing the nVidia drivers. Since you're running Hardy...

sudo apt-get --reinstall install nvidia-glx-new

If that doesn't fix it, it may be time for a fresh image.

---

### Post by louis-e on 2009-02-18
Well I just reinstalled my nvidia driver but now the graphic card does not work at all. I cannot get more than a resolution of 800x600. I tried to configure it manually but the screen resolution will not go any higher. If i click on administrateur>hardware driver it says that the nvidia drivers are in use.  

This is a problem known to me and i did communicate on this forum to help solve the issue. Initially I installed a program called Envy and it allowed me to configure the x server setting. Seem to have worked but i am not sure if this is a good solution due to the shut down problem described above.

---

### Post by thomasaaron on 2009-02-18
Envy isn't a great way to go in my opinion.

Try setting your resolution via...

```
sudo nvidia-settings
```

If it isn't installed, install it with...

```
sudo apt-get install nvidia-settings
```

If that doesn't work, try the following commands...

```
sudo apt-get --purge remove nvidia-glx-new
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg #Use all default settings
sudo apt-get install nvidia-glx-new
```

Now go to hardware drivers and try to enable it and reboot.

If that doesn't work, run...

```
sudo nvidia-xconfig
```

...and reboot.

---

### Post by louis-e on 2009-02-18
Sorry to report that none of the above worked out

sudo nvidia-settings send me to administrateur>Nvidia X Server settings
and return a message saying 'you do not appear to be using an Nvidia X driver please run nvidia-xconfig

I try desintall (through synaptics) and install with terminal, it gives the same output


here is also the terminal ouput of the rest of the commands


louis@ubuntu:~$ sudo apt-get install nvidia-settings
[sudo] password for louis: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires*:
  libavahi-qt3-1 libjaxp1.3-java libarts1c2a kdesudo-kde4 kdelibs4c2a
  libxerces2-java libpthread-stubs0 libservlet2.4-java libxalan2-java
  libgl1-mesa-dev liblualib50 x11proto-kb-dev kdesudo mesa-common-dev
  xtrans-dev x11proto-input-dev libxcb-xlib0-dev bsh libglu1-mesa-dev
  libxau-dev libx11-dev kdelibs-data liblua50 libxcb1-dev libjline-java
  x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
Veuillez utiliser «*apt-get autoremove*» pour les supprimer.
Les NOUVEAUX paquets suivants seront installés*:
  nvidia-settings
0 mis à jour, 1 nouvellement installés, 0 à enlever et 70 non mis à jour.
Il est nécessaire de prendre 0o/697ko dans les archives.
Après cette opération, 1561ko d'espace disque supplémentaires seront utilisés.
Sélection du paquet nvidia-settings précédemment désélectionné.
(Lecture de la base de données... 225476 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-settings (à partir de .../nvidia-settings_1.0+20080304-0ubuntu1.1_amd64.deb) ...
Paramétrage de nvidia-settings (1.0+20080304-0ubuntu1.1) ...

louis@ubuntu:~$ sudo nvidia-settings
louis@ubuntu:~$ sudo apt-get --purge remove nvidia-glx-new
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires*:
  libavahi-qt3-1 libjaxp1.3-java libarts1c2a kdesudo-kde4 kdelibs4c2a
  libxerces2-java libpthread-stubs0 libservlet2.4-java libxalan2-java
  libgl1-mesa-dev liblualib50 x11proto-kb-dev kdesudo mesa-common-dev
  xtrans-dev x11proto-input-dev libxcb-xlib0-dev bsh libglu1-mesa-dev
  libxau-dev libx11-dev kdelibs-data liblua50 libxcb1-dev libjline-java
  x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
Veuillez utiliser «*apt-get autoremove*» pour les supprimer.
Les paquets suivants seront ENLEVÉS*:
  nvidia-glx-new*
0 mis à jour, 0 nouvellement installés, 1 à enlever et 70 non mis à jour.
Après cette opération, 28,3Mo d'espace disque seront libérés.
Souhaitez-vous continuer [O/n]*? o
(Lecture de la base de données... 225482 fichiers et répertoires déjà installés.)
Suppression de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Purge des fichiers de configuration de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
louis@ubuntu:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
louis@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg #Use all default settings
md5sum: /etc/X11/xorg.conf: No such file or directory
louis@ubuntu:~$ sudo apt-get install nvidia-glx-new
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires*:
  libavahi-qt3-1 libjaxp1.3-java libarts1c2a kdesudo-kde4 kdelibs4c2a
  libxerces2-java libpthread-stubs0 libservlet2.4-java libxalan2-java
  libgl1-mesa-dev liblualib50 x11proto-kb-dev kdesudo mesa-common-dev
  xtrans-dev x11proto-input-dev libxcb-xlib0-dev bsh libglu1-mesa-dev
  libxau-dev libx11-dev kdelibs-data liblua50 libxcb1-dev libjline-java
  x11proto-core-dev libxdmcp-dev libpthread-stubs0-dev
Veuillez utiliser «*apt-get autoremove*» pour les supprimer.
Paquets suggérés*:
  nvidia-new-kernel-source
Les NOUVEAUX paquets suivants seront installés*:
  nvidia-glx-new
0 mis à jour, 1 nouvellement installés, 0 à enlever et 70 non mis à jour.
Il est nécessaire de prendre 0o/9372ko dans les archives.
Après cette opération, 28,3Mo d'espace disque supplémentaires seront utilisés.
Sélection du paquet nvidia-glx-new précédemment désélectionné.
(Lecture de la base de données... 225431 fichiers et répertoires déjà installés.)
Dépaquetage de nvidia-glx-new (à partir de .../nvidia-glx-new_169.12+2.6.24.16-23.56_amd64.deb) ...
Paramétrage de nvidia-glx-new (169.12+2.6.24.16-23.56) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
louis@ubuntu:~$ 

cheers
Louis

---

### Post by thomasaaron on 2009-02-18
HOLY MACKERAL!!!
Je ne parle pas français!

If the installation of nvidia-glx-new went well and it is not showing up in hardware drivers, I suspect it is because the binaries from envy (or some other attempt to install the binary nvidia drivers) is still lurking around in there.

If this is the case, I've not been able to solve it in the past. Fresh install.

---

### Post by louis-e on 2009-02-18
Well the nvidia driver is showing in the hardware drivers and I can enable it, it just doesnt seem to detect it on start up. but it does stay enabled and showing a working status in the hardware drivers

Anyway what do you mean by a fresh install? of the entire ubuntu?

That problem started after a kernel update which is why i used envy to make the nvdia card work properly. I am not sure if a full reinstallation will improve this.

This might be simplistic but if you say that envy has left some binaries Would you think that removing everything related to nvidia in the synaptic manager might also remove any of those file. When I purged the nvidia-glx-new it left some other files in the synaptics. I also got these error message in the terminal

Suppression de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Purge des fichiers de configuration de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty

So I am wondering if this might not be related to the problem

---

### Post by thomasaaron on 2009-02-18
Earlier, you said...
> sudo nvidia-settings send me to administrateur>Nvidia X Server settings and return a message saying 'you do not appear to be using an Nvidia X driver please run nvidia-xconfig
...and yet Hardware Drivers says that the driver is enabled. 

This leads me to believe that nvidia-glx-new isn't being detected properly, probably becuase something from the old envy install is interfering. 

Envy is probably what got hosed during the update you mentioned. And now, your machine is very confused and unable to activate the nvidia-glx-new driver.

This...
> Suppression de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
Purge des fichiers de configuration de nvidia-glx-new ...
rmdir: failed to remove `/usr/lib/nvidia': Directory not empty
...tells me that the above --purge remove command didn't work because /usr/lib/nvidia isn't empty.

You might try manually deleting that directory and then re-running the commands. You can delete it with...
```
sudo rm -r /usr/lib/nvidia
```

At this point, you probably should make sure you're well backed up in case something gets seriously hosed and you end up being forced to re-install.

I don't recommend a re-install lightly, but this isn't the first time I've seen a machine hosed by envy. At some point, it becomes more time-effective to just re-install than try to sort out damages caused by third-party applications.

---

### Post by mtopro on 2009-02-18
Have you tested your memory?  I have had similar issues lately and it was because as my memory was writing to the hard-drive data was being corrupted..  This can cause all sorts of issues.  Perhaps you should run a memtest.

At the grub login you should see a way to test memory, try running it at least through one pass..

---

