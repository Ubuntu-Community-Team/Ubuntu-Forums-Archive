---
title: "I Need Server Advice."
date: 2008-02-19
forum: Server Platforms
---

### Post by leroy_30 on 2008-02-19
I'm in the process of building a new server:

C2D, 4Gig DDR2 6400 Ram, 2 - 400Gig SATA-II HDD in Linux Software Raid 1, Cheap PCI Graphix. 

I will be replacing a AMD Athlon 1Ghz machine w/ 768 MB Ram & 5 40 Gig IDE HDD Configured in a hacked SW Raid 5 under Win 2k Pro. (And yes I'm violating all those raid rules about not connecting more than 1 drive to 1 channel. :oops:

Anyway, now that we're past that.

Currently I'm running Apache, MySQL, hMailServer with Squirrelmail Web interface & IMAP for Thuderbird access &  zFTPServer, and File Serving on this old machine. (Amazingly stable for windoze)

My thoughts currently are to install a basic Ubuntu Server and then use VMWare to Do the rest of this stuff.

My initial plans were to do something like this

1. Web Server - Apache
2. MySQL Server - w/ PHPmyAdmin
3. Zimbra Server
4. FTP Server
5. File Server
6. Windows OS For 4th Dimension Server & Maybe MS SQL Server Express (for software development purposes).

The more I think about it though I'm not sure whether that makes sense and I just need some direction.

I definitely want to separate my Zimbra from the other stuff but I don't know if i should setup 2 different ftp servers 1. for the Web Server and 1 for the File Server (For remote access) or if it is possible to do this with 1 ftp server???????

I also don't think it makes sense to separate the MySQL Server from The Apache Server????](*,)

If you can't tell this is my first real linux server and I'm just a little on the lost side, I just want to config it right the 1st time and not spend weeks doing it over & over again. ;-)

---

### Post by Rogers on 2008-02-19
Do it all on one box.  Don't use FTP use SSH/SFTP for files.

I run a single box Athlon x2 4200 with 2 gigs of ram on a 320 gig SATA drive... it hosts 15 websites, about 60 email accounts, MySQL databases for the CMS on the websites.  I have Tomcat/ Apache2 with VHOSTS running and it hits 5% utilization all day.

I also route and do a DHCP sever on this box as well. My blog has some details: [www.runithard.com]("http://runithard.com")

I would virtualize the windows box, but run the rest of the linux stuff on that box.  You only lose CPU if you virtualize the linux applications for now reason.

---

### Post by leroy_30 on 2008-02-19
> **Rogers said:**
> 
I would virtualize the windows box, but run the rest of the linux stuff on that box.  You only lose CPU if you virtualize the linux applications for now reason.

Thanx. I'll check it out. I was kinda leaning that way.

On a side note. I've decided to install the base system on a separate HDD and want all the data & VM stored on the RAID 1. Will putting jsut /home & /var there save all my critical data or ????

---

