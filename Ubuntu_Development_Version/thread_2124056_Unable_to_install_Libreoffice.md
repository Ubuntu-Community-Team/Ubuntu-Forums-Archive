---
title: "Unable to install Libreoffice"
date: 2013-03-09
forum: Ubuntu Development Version
---

### Post by dshad69 on 2013-03-09
Juste upgraded from 12.10 to 13.04 and I lost Libreoffice.

So first of all I did: apt-get purge libreoffice*

So, after adding Libreoffice PPA, I tried to install and got this:

[INDENT=2]sudo apt-get install libreoffice

Lecture des listes de paquets... Fait[/INDENT]
[INDENT=2]Construction de l'arbre des dépendances       [/INDENT]
[INDENT=2]Lecture des informations d'état... Fait[/INDENT]
[INDENT=2]Certains paquets ne peuvent être installés. Ceci peut signifier[/INDENT]
[INDENT=2]que vous avez demandé l'impossible, ou bien, si vous utilisez[/INDENT]
[INDENT=2]la distribution unstable, que certains paquets n'ont pas encore[/INDENT]
[INDENT=2]été créés ou ne sont pas sortis d'Incoming.[/INDENT]
[INDENT=2]L'information suivante devrait vous aider à résoudre la situation : [/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Les paquets suivants contiennent des dépendances non satisfaites :[/INDENT]
[INDENT=2] libreoffice : Dépend: libreoffice-base mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-calc mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-core (= 1:4.0.1-0ubuntu1) mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-draw mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-impress mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-math mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-report-builder-bin mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: libreoffice-writer mais ne sera pas installé[/INDENT]
[INDENT=2]               Dépend: python3-uno (>= 4.0~) mais ne sera pas installé ou[/INDENT]
[INDENT=2]                        python-uno mais ne sera pas installé[/INDENT]
[INDENT=2]               Recommande: libreoffice-gnome mais ne sera pas installé ou[/INDENT]
[INDENT=2]                           libreoffice-kde mais ne sera pas installé[/INDENT]
[INDENT=2]E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état ».[/INDENT]

Please help.

---

### Post by cariboo on 2013-03-09
Why not just install the version in the repositories?

---

### Post by dshad69 on 2013-03-09
> **cariboo907 said:**
> Why not just install the version in the repositories?

Forgot to tell you that before doing all that, I did try to install from repositories...

Marc

---

### Post by QIII on 2013-03-09
I'm installing it on RR from the repo right now.  I'll let you know what I see.

Edit:

OK.  Installed just fine from the repo for me.

Did you have Raring fully updated when you tried this?

---

### Post by dshad69 on 2013-03-09
Seems I'm the only one stuck like this... :(

Is there any other way to purge and install Libreoffice without any dependancies problem?

---

### Post by mc4man on 2013-03-09
I don't do upgrades so only a guess - 
if you upgrade with -proposed source enabled then possibly your new sources list will have -proposed enabled 
(in this case raring-proposed

If that's true & the are incomplete source packages in raring-proposed that could cause an issue (as is currently the case with LO

So ck. your sources, if proposed is enabled then disable. Remove any LO packages, update your sources then re-install LO as seen fit. 

Or just wait for new LO to get complete

---

### Post by QIII on 2013-03-09
> **mc4man said:**
> I don't do upgrades so only a guess - 

A guess with pretty good insight!

---

### Post by dshad69 on 2013-03-09
> **mc4man said:**
> I don't do upgrades so only a guess - 
if you upgrade with -proposed source enabled then possibly your new sources list will have -proposed enabled 
(in this case raring-proposed

If that's true & the are incomplete source packages in raring-proposed that could cause an issue (as is currently the case with LO

So ck. your sources, if proposed is enabled then disable. Remove any LO packages, update your sources then re-install LO as seen fit. 

Or just wait for new LO to get complete


You got it!

Thanks a lot!

---

### Post by mc4man on 2013-03-09
Well that's 2 recent cases of upgrade with proposed enabled ([http://ubuntuforums.org/showthread.php?t=2123696](http://ubuntuforums.org/showthread.php?t=2123696)), so I'd say that it's a poor idea to do so when upgrading to a dev version & in general.
Either way, users that have proposed enabled at any time should refrain from updating without control & or paying attention
(as in some terminal command & typing y without reading back or using software-updater & accepting a partial ect.

synaptic is best for such activities if marking individually or in small groups

---

### Post by Harry33 on 2013-03-10
This is the reason for the installing issues from RR repos right now:

The new release version 4.0.1 is here (but only partly in RR repos):
[https://launchpad.net/ubuntu/raring/+source/libreoffice/1:4.0.1-0ubuntu1](https://launchpad.net/ubuntu/raring/+source/libreoffice/1:4.0.1-0ubuntu1)

The 64-bit packages are all in repos, but the complete installation needs also a few architecture independent packages, like:
- fonts-opensymbol-2:102.2+LibO4.0.1-0ubuntu1_all.deb
- libreoffice-common-1:4.0.1-0ubuntu1_all.deb
- libreoffice-style-human-1:4.0.1-0ubuntu1_all.deb (or alternatively one other style package)

Without these, the intallation is broken.
This is what happens now.
All the 64-bit packages are being upgraded to version 4.0.1, but because the *all.deb packages are not yet in repo, the installation gets broken.

Well there are two things you can do, if you ended up having a broken LO:
1. disable the proposed repo, remove LO completely and then reinstall old LO. Without proposed repo enabled you get the working old installation back.
     Then sit back and wait for a few days until all the new LO packages are in the repos.
2. if you want the new 4.0.1 now, then manually download the necessary packages from the link above and install them from terminal (or console) with dpkg.
    Now sit back and enjoy the new working LO.

If you get warnings when installing manually with dpkg (sudo dpkg -i *.deb), repeat the command.
You can also install the easier (less dependencies) packages first (libreoffice-style-human, libreoffice-common, uno-libs3, ure, fonts-opensymbol).
Also see that the package libcmis-0.3-3 is installed.

---

### Post by serdotlinecho on 2013-03-11
LibreOffice 4.0.1(i386) is here with proposed enabled :D

```
~&#10095; apt-cache policy libreoffice-core
libreoffice-core:
  Installed: 1:4.0.0~beta2-0ubuntu2
  Candidate: 1:4.0.1-0ubuntu1
  Version table:
     1:4.0.1-0ubuntu1 0
        500 http://my.archive.ubuntu.com/ubuntu/ raring/main i386 Packages
 *** 1:4.0.0~beta2-0ubuntu2 0
        100 /var/lib/dpkg/status
```

---

