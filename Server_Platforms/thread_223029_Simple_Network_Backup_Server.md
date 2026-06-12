---
title: "Simple Network Backup Server"
date: 2006-07-25
forum: Server Platforms
---

### Post by Flashstar on 2006-07-25
I just built a multi-purpose Ubuntu server and I was wondering if there is a simple program out there to backup 5 different windows machines onto a relatively large hard disk in the Ubuntu server. It would be great if this program had scheduling options as well. Does anyone know of such software?

Thank you

---

### Post by chippa on 2006-07-26
What OS are the client PCs running?


If it's Windows 2000/XP, you could make a shared drive on the server using Samba, and on the client PCs schedule NT Backup to back up the desired data to this shared drive.

edit: this might be worth reading too
[http://www.linuxplanet.com/linuxplanet/tutorials/6271/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6271/1/)

---

### Post by Jeffrey SomeBody on 2006-07-26
I'm in the process of setting up a Ubuntu server and have a few WinXP and a few Linux machines that will be backed up.

I've searched around and found a solution that meets my needs, WinXP and Linux clients available and a server that runs on a Linux box.

This program is called "Bacula", need more info, goggle Bacula...

---

### Post by Flashstar on 2006-07-26
Thanks for the replies. I think that I will just set up a shared samba folder and configure the clients (windows xp) to backup to it every week. I looked at Bacula, but you need several seperate servers for different things, and I only have 1 box.

---

### Post by lamego on 2006-07-26
An easy way would be to setup shares as suggested and then just use rsync or rdiff-bacup to perform the backups from a cron job.

---

### Post by baastie on 2006-07-26
Hi,

Bacula is a great backup tool and you can run the server ( dir, sd and ( fd ) ) all on the same server. For your linux or xp clients you can use a the bacula client ( fd )...

Grtz..

---

