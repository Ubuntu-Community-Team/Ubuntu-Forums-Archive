---
title: "VirtualBox on Hardy with Kubuntu as Guest ... Screen resolution"
date: 2008-05-05
forum: Virtualisation
---

### Post by jacrider on 2008-05-05
I have been running VirtualBox under Hardy for a while with great results to run WinXP.  Thought I would give Kubuntu 8.04 with KDE4 a go.  So, I downloaded the iso and installed a new virtual machine.  All works, except I can't resize the screen.  Any idea of what I have done wrong?

Thanks.

---

### Post by ACMarina on 2008-05-05
Did you install guest additions??  I had to do that in order to raise the resolution above 800x600..

---

### Post by jacrider on 2008-05-05
I did install the guestadditions.  It gave me better mouse/keyboard usage.  In my WinXP machine, I can get the higher resolutions and scale the display.  I just can't get it on my Kubuntu machine.

---

### Post by stealth.us on 2008-05-07
jacrider: How did you install guest additions? I clicked on Devices / Install Guest Additions but nothing happened (I waited 30mins)? My host is WinXP and guest is Kubuntu 8.04? (I was able to install Guest Additions on comp where Kubuntu is host and XP is guest).

(Ok, I saved the problem: Just had to mount VBoxAdditions.iso and run VBoxLinuxAdditions.run. Now everything works ok.)

---

### Post by deltaromeo on 2008-05-21
This worked for me:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=620828&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=620828&page=2)

:)

---

