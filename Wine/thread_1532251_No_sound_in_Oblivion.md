---
title: "No sound in Oblivion"
date: 2010-07-16
forum: Wine
---

### Post by Nick_Jinn on 2010-07-16
So I have Oblivion playing on Ultra High settings in Linux. Awesome. It looks great and the playing is fairly smooth. I might downgrade to High settings, but that is great for playing in WINE.

I have no sound. Also it says that dll something failed and had to stop every time I launch the game, and it says that the wine server is unavailable when I play around with the settings.

It also says there is an updated version of playonlinux, but I seem to have the most updated one that I can find...

---

### Post by asdfoo on 2010-07-17
> **Nick_Jinn said:**
> So I have Oblivion playing on Ultra High settings in Linux. Awesome. It looks great and the playing is fairly smooth. I might downgrade to High settings, but that is great for playing in Wine.

I have no sound. Also it says that dll something failed and had to stop every time I launch the game, and it says that the wine server is unavailable when I play around with the settings.

It also says there is an updated version of playonlinux, but I seem to have the most updated one that I can find...

Just use regular wine from winehq.org.

wine-1.2 is the most recent.

---

### Post by spoons on 2010-07-17
Using regular Wine I have found this works absolutely perfectly.

---

### Post by Nick_Jinn on 2010-07-18
So I think someone told me about this in the other thread....So how do I install these with regular wine without play on Linux?

---

### Post by Nick_Jinn on 2010-07-18
> sudo apt-get install wine1.2
[sudo] password for djinn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.06) ...
Running mktexlsr. This may take some time... done.
No packages found matching texlive-base.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winefish:
 winefish depends on tetex-bin | texlive-base-bin | latex; however:
  Package tetex-bin is not installed.
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
  Package latex is not installed.
dpkg: error processing winefish (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
               No apport report written because the error message indicates its a followup error from a previous failure.
                              Errors were encountered while processing:
 tex-common
 texlive-binaries
 winefish
E: Sub-process /usr/bin/dpkg returned an error code (1)





There is a 'deficiency' problem with wine.

---

### Post by asdfoo on 2010-07-18
> **Nick_Jinn said:**
> There is a 'deficiency' problem with wine.

I don't see any problem with Wine here, it says it's already installed, however you have problems with texlive and winefish which is another tex program - not Wine.

---

### Post by Nick_Jinn on 2010-07-18
Could that be causing my problems? How do I resolve this?

---

### Post by Nick_Jinn on 2010-07-18
So I tired installing with Wine Doors instead of PlayonLinux.....install went smooth until the very end where it asks me where is the data9.cab.

I have no idea what this is or why its not on my disk.

---

