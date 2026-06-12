---
title: "minimum server requirments"
date: 2008-05-31
forum: Server Platforms
---

### Post by bcn17 on 2008-05-31
I have been thinking about summer lately and in my plans are to set up a server. I have an old computer sitting at home running a 1.2 GHz 32 bit athalon ( i think athalon XP) on an old Iwill motherboard with a 32 MB geforece agp video card and a standard lynksys 10/100 network card- I think I also have a 200  GB HD I can plug in to amend the 40GB inside of it. OH yeah, it has 512MB of ram. 

The main things im worried about are the cpu and ram. Will these be powerful enough/ enough to allow me to save files and backup from remoted locations? I plan on having the computer sit in my families house and using it to backup my stuff 250 miles away. It would also be nice to be able to upload things (securley) to the server so that I could access things wherever I go via a browser. I could also set up a folder on my families computers so that they could use it also. Does this seem to hard or impossible with my hardware? -Thanks.

---

### Post by quelx on 2008-05-31
Your needs seem modest enough that what you have will work very well.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Whatever you do make sure you have a backup plan (once you get that far, feel free to ask here).

> allow me to save files and backup from remoted locations? 

for this start with **rsync** (remote file sync).

> I plan on having the computer sit in my families house and using it to backup my stuff 250 miles away.

**rsync**, again, and **ssh** for remote administration.

> It would also be nice to be able to upload things (securley) to the server so that I could access things wherever I go via a browser.

stay away from **ftp** (unless its **sftp**) for uplaods, **apache2** is the typical webserver on Ubuntu, though there are others that are more lightweight if you find it takes too many resources.
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

> I could also set up a folder on my families computers so that they could use it also.

again **sftp** (ftp over ssl)

An overview of what Ubuntu offers
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by kerry_s on 2008-05-31
that's good enough.
you do know ubuntu server is no gui? you can add 1 but it's not needed.

debian is known to be a much better server.
net installer:
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

---

### Post by bcn17 on 2008-06-03
Thanks so much, won't have time to try till mid june but I got this page saved!

---

### Post by Sporkman on 2008-06-03
> **kerry_s said:**
> 
debian is known to be a much better server.
net installer:
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

Ubuntu is a perfectly good & stable server, and it's easier to setup & maintain IMO.

---

### Post by dmizer on 2008-06-04
my storage server works plenty quick.

500mhz pII with 256 meg of ram, and 500 gig of hdd storage. in addition to being a file/storage server, it also hosts an intranet web based database. handles gigabit local access, and i use ssh/rsync to run backups from remote.

i think you'll be fine.

---

### Post by TurboRush on 2008-06-04
You should be fine. I have a junky p3 800 with 200m of RAM running my website, running backup jobs for my other computers, etc and it's fine. It has been extremely resiliant even when pushed to its limits.

---

