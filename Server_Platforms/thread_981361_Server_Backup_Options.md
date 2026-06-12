---
title: "Server Backup Options"
date: 2008-11-13
forum: Server Platforms
---

### Post by wayne on 2008-11-13
Anyone who has gone down this path before could you give me any advice and or options on server backups?

I was looking into buying a new Dell server to be used as a file server for a small business and was sorta set back when seeing the price for a Dell PowerVault 100T backup drive (around $800).  I'll be installing Ubuntu server 8.04 LTS on the system.  Any suggestions on something that is less costly, like a cheaper drive? Are there backups to the Web available for Linux similiar to MozyPro for Windows?

Thanks for any suggestions in advance.
Wayne

---

### Post by Thirtysixway on 2008-11-13
For backups you could simply buy a 2nd harddrive and copy your data to it, a lot cheaper than 800 dollars.

---

### Post by wayne on 2008-11-13
That's a good plan but, I believe the company management wants to take the data off site in case of fire or natural disaster.

---

### Post by flashgc on 2008-11-13
These days I'm using IcyDock bay/enclosure pairs for backup when it's possible. We install the bay in a floppy bay. The enclosure soft mounts in the bay, uses laptop HDD which lets us pick capacity as needed, and the bay has access to IDE or SATA bus speeds so backups happen pretty quickly. Just have as many enclosures for the bay as your backup plan requires. We tend to favor three so two local can alternate while one is rotated off-site on a weekly basis.

---

### Post by wayne on 2008-11-13
Thanks flashgc, 

I'm not familiar with IcyDock.  I will take a look them.

---

### Post by freebeer on 2008-11-15
I have an arrangement where the file server daily runs backups to an off-site server via rsync.  So far it's working well.

---

