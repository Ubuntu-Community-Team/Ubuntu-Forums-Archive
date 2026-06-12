---
title: "Request:Folding@Home"
date: 2005-09-27
forum: Ubuntu Backports
---

### Post by jc87 on 2005-09-27
Can you include Folding@home at the Backports??? i check it out and it appears there is no repositories that contain it (and since is a program designed to help hummanity there is no reason not to).

Besides most people (like me) since they have the first taste at Apt-Get then can´t Stop;-) .

---

### Post by Zelut on 2005-09-27
Folding isn't really something that 'installs' so much as just runs.  If you download the FAH502-Console.exe from the folding site & set that to autostart in your 'sessions' thats about as much as you need to do.

I have it in my home folder & it auto-runs at login... thats about all you can do with it.

---

### Post by jdong on 2005-09-27
That'd require tweaking of the FAH binary, which is closed-source.

---

### Post by strikeforce on 2005-09-27
[QUOTE=jdong]That'd require tweaking of the FAH binary, which is closed-source.[/QUOTE]

I thought it was open source?  Anyways you know better so yeah I just heard it was open source from their forums.

---

### Post by jdong on 2005-09-27
no; the calculation cores are more or less open source (GPL/BSD), but the actual client is not -- they argue that'd compromise the validity of the results (understandable)

---

### Post by strikeforce on 2005-09-28
[QUOTE=jdong]no; the calculation cores are more or less open source (GPL/BSD), but the actual client is not -- they argue that'd compromise the validity of the results (understandable)[/QUOTE]

Thats where I got confused.  Thanks for clarifying btw :)

---

### Post by jpkotta on 2005-10-09
I have written an install script for Folding@Home.  Please get it in the [Wiki]("https://wiki.ubuntu.com/FoldingAtHome").  It is based off of the Gentoo FAH install.  It installs the executable to /opt/foldingathome, and creates a client for every CPU.  It installs a startup script to /etc/init.d, and adds it to runlevel 2.

---

### Post by BoredOutOfMyMind on 2005-11-12
There is a kicker app located at 

[http://members.shaw.ca/khessels/kfolding/index.html#About](http://members.shaw.ca/khessels/kfolding/index.html#About)

the app is a nightmare to attempt to install in Kubuntu. 

anyone who could tweak this along and place in the Backports, it would add to those actually helping F@H.

---

### Post by andrewpmk on 2005-11-13
Could someone add the install script to multiverse backports?

---

