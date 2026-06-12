---
title: "VLC 2.1.2-2 not working with Ubuntu Studio Daily ISO"
date: 2014-02-14
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-02-14
Well the title says it all... 

Installed VLC (ver 2.1.2-2build1) from Ubuntu Software Centre and Synaptic, both times, whenever a video is played with VLC the system gets logged off, login screen is displayed, 

Didn't try using terminal, just removed VLC.

The same happens with Kubuntu 14.04 Alpha install.

Kernel 3.13.0-8 problem? I  have no idea.

Anyone else here facing any similar problems?

---

### Post by cariboo on 2014-02-14
We are here to help you solve problems, while running Trusty, if you can't supply us with enough information for us to take a stab at resolving your problem nobody benefits from your experience. If you reinstall VLC, and start it from a terminal, and post the output here, I'm sure that someone can come up with an answer for you.

---

### Post by su:bhatta on 2014-02-15
Ok, Reinstalled VLC, started from terminal :

```
~$ vlc
VLC media player 2.1.2 Rincewind (revision 2.1.2-0-ga4c4876)
[0x203e118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
```

But, when I tried to play a video in VLC, again, the session logged off. I was presented with the LightDM login screen.

If there is an error report where do I find it and how. Am not a pro at that. 

There was no 'System problem detected' message and no Apport window.

Also, before installing VLC I updated my system using 

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade
```

---

### Post by su:bhatta on 2014-02-24
Ok, as of now resolved it by turning off the 'Accelarated Video Output' option in the Video Tab of Preferences in VLC. 
A trick I read up from posts dating back to 12.04 if I remember correctly.

In case anyone faces a similar problem, thats what works.

---

