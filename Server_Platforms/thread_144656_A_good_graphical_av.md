---
title: "A good graphical av"
date: 2006-03-14
forum: Server Platforms
---

### Post by sudomania4 on 2006-03-14
Hiya, I am somewhat new to ubuntu, and have been searching for a graphical antivirus app for ubuntu. I understand ubuntu doesn't get viruses, but i have a windoze partition and would like to scan certain files before transferring them from my ubuntu partition to my windoze partition. I tried clam, but it said something about only operating at level 6. On my windoze partition, i used avast and avg, but the linux versions are both rpms which i had trouble converting and updating. Anything native? Thanx!

---

### Post by KingBahamut on 2006-03-14
You can Try aegis virus scanner, but in a previous post noted -- [http://ubuntuforums.org/showthread.php?p=825120#post825120](http://ubuntuforums.org/showthread.php?p=825120#post825120) -- it was found to be a little too sensitive. If you find that this is the case, then try clamav with avscan (a gtk front end for clamav). Ive had a problem with neither and both are pretty aggreeable.

---

### Post by JoWilly on 2006-03-14
Avast has a gtk2 ui:
[http://avast.com/eng/avast-for-linux-workstation.html]("http://avast.com/eng/avast-for-linux-workstation.html")

Convert the rpm to deb with "alien -d --scripts" , (alien is in the repos).

Updating and everything else works fine here (I start it with "sudo avastgui"; don't know if sudo is needed though).

---

### Post by sudomania4 on 2006-03-17
I tried aegis and, like you said, it was to sensitive. Should I download the RPM package or the TAR GZ package (of the avast) to convert with alien?

---

### Post by Xian on 2006-03-17
I would also suggest trying the Avast 4 Linux product.
It works great on Ubuntu and is completely free for home use.

---

### Post by majikstreet on 2006-03-18
or f-prot -- there's a howto somewhere and it's probably on doc.gwos.org too.

---

