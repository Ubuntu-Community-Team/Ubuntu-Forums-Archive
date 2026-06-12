---
title: "Can you update to the next Ubuntu release from the CD?"
date: 2010-09-15
forum: Ubuntu Studio
---

### Post by djwkd on 2010-09-15
I have the Ubuntu Studio alternate install disc for 10.10 beta. Can I insert that into my drive and just update my existing release to the next with a command, or going to the sources window? If not, can I do it with the ordinary Ubuntu disc?

---

### Post by Totalchaos on 2010-09-16
Yes and it will update to beta. it's nice to have an internet connection

---

### Post by djwkd on 2010-09-17
Ok. How do I do it?

---

### Post by JBAlaska on 2010-09-17
Use this method if the system being upgraded is not connected to the Internet.

1-Download the alternate installation CD from
[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

2-Burn the ISO to a CD and insert it into the CD-ROM drive of the computer to be upgraded.

**If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:**
```
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0
```
A dialog will be displayed offering you the opportunity to upgrade using that CD.
Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:
```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by djwkd on 2010-09-17
Ok. Cheers!
 
I shall mark as [RESOLVED] once I've installed.

---

