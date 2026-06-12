---
title: "What size CF do I need for booting 8.04 LTS server"
date: 2009-04-11
forum: Server Platforms
---

### Post by whosmatt on 2009-04-11
I'm thinking of consolidating my three servers (debian, pfsense, and freenas) into one box.  Right now the freenas box has a highpoint rocketraid 454 card with a raid 5 array that has been quite reliable. I'd like to continue to use this for storage on the new box but i'm aware of the problems of booting from such a device under Linux (freenas boots from cd).  I have a pair of 120GB drives in the Debian box that are a mdadm mirror mounted as /home (the box boots from a single drive).  If i'm correct, I can't actually boot from a software raid device.... hence my interest in CF.  My plan is to get a IDE to CF adapter and a 4 or 8GB card, install the OS to it and have the arrays mounted as /home and /somebigstorage, you get the idea.  So 2 questions: how big?  This will not be a minimal install, the box will run Vmware Server, BIND, Apache, netatalk, samba at least.  Will I run into trouble if /var is on the CF?  I have heard stories of CF wearing out due to excessive writes. Also, i imagine I wouldn't want to have the swap partition on the CF.

So -- what do i need, and what should i look out for?

thanks,
-matt

---

### Post by BkkBonanza on 2009-04-11
I would think that even 4GB ought to be enough. Definitely don't put /var onto the CF drive - it has the logs and you get a constant stream of writing from apache, plus the worry of it filling up and causing issues. YOu really want the CF drive to be like a read only image of the base system except maybe /etc which has minimal changes.

On the other hand, with the cost of CF drives now why not use 8GB? It gives you a bit more expansion room if you need it.

---

### Post by doogy2004 on 2009-04-12
I use a 10GB drive to contains everything except my /home which is mounted on a software RAID5 array, I also use a swap file that I placed in my raid array.  This gives me plenty of room after installing LAMP, VMware, and other misc. software.  With all of my programs installed on the 10GB drive I am using 2.8GB.

Given that 4GB should be more than enough assuming you do not place your swap, data, and log files on the CF card.

When I rebuild my server I'll probably use an SSD drive to boot from and store my programs.  Given that 10GB SSD drives are getting cheap.

---

