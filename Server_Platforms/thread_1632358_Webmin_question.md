---
title: "Webmin question"
date: 2010-11-27
forum: Server Platforms
---

### Post by Painguy on 2010-11-27
I am planning to setup my own webserver using webmin, but from what i've read i apprently need two harddrives. one for the OS & one for the data. can i just partition my harddrive into two because i dont have another hdd lying around. i also just want to note that this is my first time trying to do something like this sooo :P any advice or alternative solutions is appreciated. I rly want to try to set up my own server :D. As a side note ill list the specs of the comp i plan to use as a server. Pentium 4 2.8ghz, 1gb DDR, 80GB 7200RPM HDD

---

### Post by iNsOmNiOuS on 2010-11-27
Whoever told you that you need 2 hds was lieing....

I have webmin running absolutely fine on a VPS with 1 Hard drive and only one partition

---

### Post by eeffoc on 2010-11-27
> **iNsOmNiOuS said:**
> Whoever told you that you need 2 hds was lieing....

I have webmin running absolutely fine on a VPS with 1 Hard drive and only one partition

x2

You definitely do not need two hard drives; I'm using webmin on my 50GB Ubuntu 10.10 Server...VMware image. ;)

---

### Post by Painguy on 2010-11-27
haha ok. i was worried for a sec. thx guys appreciate the help.

---

### Post by James78 on 2010-11-28
I'm running Webmin from a server that has 3 hard drives all in RAID 0 mounted at / . Really sweet since it combines all my hard drives into 1 huge drive.

---

### Post by Vegan on 2010-11-28
I use it on my Linux box along with a SSL terminal. 

I use Linux on bare metal fine, I can also virtualize it fine but I have lots of machines so I am not hard up.

---

### Post by windependence on 2010-11-28
>  I'm running Webmin from a server that has 3 hard drives all in RAID 0 mounted at / . Really sweet since it combines all my hard drives into 1 huge drive.

Make sure you have good backups because now you have three times as many chances of hardware failure. RAID 0 provides no redundancy so if one drive fails you're screwed without backups. This is extremely risky IMHO. 
 
-Tim

---

### Post by Vegan on 2010-11-28
I hate software RAID, its a sure fire way to trashing everything.

I have automated backups, this way I am safe. I used a bash script but there are packages available for more complex needs.

I like USB disks for backups but they are a tad dodgy as we have seen data loss on them in the past. I have 2 USB disks so I have an extra copy and I plan to get more USB disks.

Up the food chain is another server, possible remote to backup to.

---

