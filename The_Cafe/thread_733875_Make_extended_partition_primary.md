---
title: "Make extended partition primary"
date: 2008-03-24
forum: The Cafe
---

### Post by zoopzoop on 2008-03-24
I just digged out an old laptop to test something (accessing my files under Gutsy, which are shared through Hamachi, from Win XP) and noticed that I left that laptop when I installed WIn 98(!) on it to play some old games...
The current partition configuration is:

/dev/sda1 - fat32 - 10gb - contains Win 98
/dev/sda2 - extended - 45.89gb
/dev/sda5 - ntfs - 45.89gb - contains Win XP

whereby /dev/sda5 is a logical partition in the extended partition /dev/sda2.

I want to get rid of Win 98 (managed to get the games going under WIn XP :) ) and get Win XP back... right now it's not bootable, I have no idea how it ended up in a logical partition.
Can I somehow make the extended Win XP partition a primary partition so that it's bootable again?
I don't want to reinstall, I had all my stuff nice and handy in that XP installation...

---

### Post by LeoSolaris on 2008-03-24
Ultimate Boot CD or System Rescue may be able to manage the trick. I have not played with them a whole lot, but if anything can manage it, they could. Also, another alternative would be to see if you can access anything in the XP partition at all, and just pull it out piece by piece then put it back into a fresh install. I would try the SR or UBCD first, just in case. 

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) (Ultimate Boot CD)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) (System Rescue CD)

Leo

---

