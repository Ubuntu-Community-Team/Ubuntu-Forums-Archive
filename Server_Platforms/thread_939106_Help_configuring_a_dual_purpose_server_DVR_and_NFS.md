---
title: "Help configuring a dual purpose server: DVR and NFS"
date: 2008-10-05
forum: Server Platforms
---

### Post by GISuser on 2008-10-05
I am planning on to build myself a server using Hardy 8.04 (no gui) to act as a DVR server using [zoneminder]("http://www.zoneminder.com/") and a NFS using Samba.  Below are my initial thoughts.  I would appreciate any suggestions or guidance so I do not go down the wrong path.

Prior Experience: one-year with Ubuntu 7.10 Desktop and one-month building a GIS server with Hardy 8.04 server (no gui) in a virtual machine.  Other than this, I am new to Linux.

Planned core equipment:
[LIST]
[*]Intel Core 2 Quad 2.4Ghz CPU
[*]Gigabyte mobo with NVIDIA video chipset
[*]4GB RAM DDR2 800
[*]Two Western Digital 500GB HD (SATA)
[/LIST]

Conceputal Model:
[LIST]
[*]The server will be headless and be secured in a DVR lock box
[*]The server will be LAN hard wired to the router
[*]The server will store files that I do not want to reside on two laptops
[*]The server will backup critical files off-site every night
[*]Two laptop computer users will access the server; one laptop running Ubuntu 7.10 and the other laptop running Windows XP.
[*]Use SAMBA to connect the Windows XP machine to the server.
[*]The Ubuntu laptop occasionally runs Windows XP in a VMware Workstation 6.5 virtual machine.  The Windows XP VM needs to access the server as well.
[*]The two laptops will backup local files to the server at power on/off (see below question about LDAP).
[*]Laptop users will also be able to backup local files to a USB hard drive
[*]One HD (Disk 1) will be used for /, /swap, /zoneminder, /sharedfiles and /home, the other HD (Disk 2) for recording surveillance video.
[*]Zoneminder will be accessed from the intranet and internet
[/LIST]

Knowledge Shortfall:
[LIST]
[*]After reading numerous server howto's I am confused whether I need to use a DNS server and/or BIND
[*]I have a limited knowledge of how Active Directory works on Windows Server 2003.  I am confused what LDAP can provide me
[*] Not sure whether 32 or 64-bit Ubuntu server will be best.  Nervous about 64-bit and trying to get Zoneminder to work.
[*]Not sure if I can have Zoneminder binaries and configuration files on Disk 1 and the recordings on Disk 2.
[/LIST]

Questions:
[LIST=1]
[*]Would it be better to build a LDAP.  And if so, can file synchronization be set so the laptop user will have their working files stored locally as well as on the server?  Critical files will be stored on server only.
[*]Are my thoughts on hard drive partition fine.  Recall that each drive is 500GB.  Drive one: / = 103GB, /swap = 2GB, /zoneminder = 15GB, /sharedfiles = 60GB, and /home = 320GB.  Drive 2: /video = 500GB (this is where video for surveillance is recorded; assuming that video and binaries can be on different disks)
[/LIST]

My first order is to get Zoneminder working.  I will then worry about the NFS.

I am planning to order hardware within the next few days.

Thanks for the comments, precautions, and ....
 

Found these post regarding using another partition to store recorded data.  Hope it helps others.
[http://www.zoneminder.com/forums/viewtopic.php?t=12259&highlight=seperate+separate+partition]("http://www.zoneminder.com/forums/viewtopic.php?t=12259&highlight=seperate+separate+partition")
[http://www.zoneminder.com/forums/viewtopic.php?t=11482&highlight=partition]("http://www.zoneminder.com/forums/viewtopic.php?t=11482&highlight=partition")


~andrew

---

### Post by Nxion on 2008-10-09
/

---

