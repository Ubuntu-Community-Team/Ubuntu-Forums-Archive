---
title: "How to Backup and Restore a LAMP system?"
date: 2007-02-23
forum: Server Platforms
---

### Post by cocotu on 2007-02-23
Here at work we have a small LAMP server for our wikipedia intranet. I wanted to know how to make an image of the HD so in case the system crashes or burns I'm able to install that HD image in another machine. I have seen many options such as: Partimage, Gparted, dd command, etc. We just want something simple and easy for beginners. Thanks..

---

### Post by GoBieN on 2007-02-23
How about Norton ghost ? granted its not free or open source, but it is easy ;)

---

### Post by Velvet Elvis on 2007-02-23
I don't think you really want to make a disk image unless you have an identical hard drive to back it up on to.  

More likely what you want to do is is regular database backups and incremental backups of the web directory.  

Look here for a comparison of different tools available:

[http://deb.riseup.net/backup/](http://deb.riseup.net/backup/)

I use backup-ninja.

---

### Post by madmetal on 2007-02-23
i am not an expert but i think you can also use rsync.

---

### Post by GoBieN on 2007-02-24
For backup i use Dar (or Kdar as a GUI), wich does 1 full backup/month and a differential backup every day to an extra disk in the server.  

For easier restore and selection i have 3 different backup selections. A single one for my /var/www directory, a single one for all my /mnt stuff, and off course one for my whole system (excl. the /mnt and /var/www since i do those separately).

Thats the backup to disk part !

But i'm very freaky in backups, so i also have a DDS4 tape drive and do a full backup of my system (excl. the /mnt dir because thats a file share with 60GB of ISO's and stuff in it) weekly. For the tape backup i use HP Data Protector Express Single Server edition (not free, but a very good backup solution).

So i think i'm covered, with disk backups and tape backups !:lolflag: 

And all that for a simple home server which acts as a webserver to the internet and a fileserver for my home network.

See for yourself:
[http://ares.gobien.be:8080/ls.php](http://ares.gobien.be:8080/ls.php)

---

### Post by esaym on 2007-02-25
> **madmetal said:**
> i am not an expert but i think you can also use rsync.

Yea if he has the hard drive space on a remote computer using a script is very convenient

Here is my script, modify it for your computer:
```
#!/bin/bash

rsync -acv --delete --stats --progress --rsh='ssh' root@10.36.38.1:/ /home/storage/BackUp/Serverback/webserve --exclude="/proc/" --exclude="/lost+found/" --exclude="/var/squid/cache/" --exclude="/mnt/" --exclude="/dev/"
```

As you can see it logs in through ssh and then copies the root (10.36.38.1:/ ) of 10.36.38.1 to /home/storage/BackUp/Serverback/webserve

---

