---
title: "Widescreen in VirtualBox"
date: 2009-02-18
forum: Virtualisation
---

### Post by u'b'u'n't'u on 2009-02-18
I would like a truly full screen virtual desktop, but when I run XP in Virtualbox, it only gives me 4:3 screen resolutions, and I have a 16:9 laptop. My question is: How can I get a true Full screen in Virtualbox


-u'b'u'n't'u

---

### Post by konqueror7 on 2009-02-18
install guest additions...go to *Devices > Install Guest Additions*, this will mount a 'CD-ROM' on your winxp machine, it should automatically install necessary drivers such as video card drivers and mouse integration for you virtualmachine...

---

### Post by HotShotDJ on 2009-02-18
> **u'b'u'n't'u said:**
> I would like a truly full screen virtual desktop, but when I run XP in Virtualbox, it only gives me 4:3 screen resolutions, and I have a 16:9 laptop. My question is: How can I get a true Full screen in VirtualboxWhat version of VirtualBox?  With the "official" Sun version, simply start up XP in VirutalBox, then from the VirtualBox menu bar, go to Devices --> Install Guest Additions.  Normally, the installer will start up automatically, but if it doesn't, just open the Windows XP "start" menu, go to "My Computer" and double click on the CD labeled "VirtualBox Guest Additions."

This method is SUPPOSED to work with the OSE version (the version in Ubuntu's standard repositories).  But some people have reported problems.  If you are using the OSE version (version 2.0.4) AND the above method doesn't work, you may have to manually download the iso from [http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso) then manually mount it as a CD image in VirtualBox.  Hopefully, you won't need to use this work-a-round.

---

### Post by konqueror7 on 2009-02-18
sorry, forgot to mention, mine is the official sun's version i downloaded directly from [virtualbox.org]("virtualbox.org")...if we have the same version, follow my method, else if you have the OSE version, follow his...;)

---

### Post by HotShotDJ on 2009-02-18
> **konqueror7 said:**
> sorry, forgot to mention, mine is the official sun's version i downloaded directly from [virtualbox.org]("virtualbox.org")...if we have the same version, follow my method, else if you have the OSE version, follow his...;)Actually, if s/he is using the OSE version, I would recommend upgrading to the offical Sun version.  Since most people install the guest additions, they end up agreeing the the Personal Use & Evaluation License (PUEL) anyway -- basically tainting the GPL license of the OSE version -- but don't get the advantage of using the full PUEL version of VirtualBox.  If people are going to do that, it seems silly to stick with the OSE version.

---

### Post by konqueror7 on 2009-02-18
yeah, i agree that the official version should be installed rather than the OSE version...

i don't even see any benefit in using the OSE version...:)

---

### Post by HotShotDJ on 2009-02-18
Ok... I just wrote a HowTo for getting the PUEL version of VirtualBox.  See: [http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

---

### Post by konqueror7 on 2009-02-18
that was fast...:D

nice guide by the way...

---

### Post by HotShotDJ on 2009-02-18
> **konqueror7 said:**
> that was fast...:D

nice guide by the way...Thank you for your kind words.

---

