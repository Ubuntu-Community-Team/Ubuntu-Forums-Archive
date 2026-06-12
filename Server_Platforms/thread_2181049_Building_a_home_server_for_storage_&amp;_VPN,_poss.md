---
title: "Building a home server for storage &amp; VPN, possible?"
date: 2013-10-16
forum: Server Platforms
---

### Post by NAPbKrX on 2013-10-16
[SIZE=2]Hi, do not be mad at me for my total emptiness of knowledge in this field, anyway, I would like to know if it is possible to build a home server for storage and for VPN. I currently use two externals HDD's (2TB+3TB) for storage and have a subscription for a VPN. I will for sure get another HDD (3TB) and a SSD. My budget is 500$ for hardware, plan to use Ubuntu as OS on this server, however I am wondering if there could be compatibility issues (my Ex. HDD's are formatted in HFS+), my main computer is under OS X, in the future, my next computer will run Linux, two other computers at home use Ubuntu. I would like these three computers to reach files on the server and of course use it as a VPN as well and if possible restrict access to certain files form the two Ubuntu computers and access files on the server from anywhere in the world. 

As for hardware correct me if I am wrong but here is the list of parts I think I may need; 
Case; 
PSU; 
Motherboard; 
Processor; 
HDD; 
SSD, 
correct me if I miss something. I never build a computer by myself. 

Thank you.[/SIZE]

---

### Post by houstonbofh on 2013-10-16
Your requirements are kind of all over the place.  So let me go one at a time.

Ubuntu as a file server - Easy and mature.  You can serve files with Samba, or NFS easily. (Or SCP or...)  However, your HFS formated drives are a problem. While you can mount them r/w, there is no journeling.  This means a power outage is likely to corrupt the drives. [http://askubuntu.com/questions/16811/how-well-is-the-hfs-filesystem-supported](http://askubuntu.com/questions/16811/how-well-is-the-hfs-filesystem-supported)

VPN support - Are you wanting to host VPN access to your internal network, or connect to an external VPN provider?  Both are possible, but are very different setups.  Also, you hosting VPN is dependent on your router.  Unless you want the server to be a router, which is some additional complexity.

Hardware - You left out memory.  And if you will be routing you will need an aditoona nic.  Also you do not need both Solid state and spinning hard drives.

---

### Post by mörgæs on 2013-10-16
There's very small workload on a file server and consequently no need for fast hardware. 

I would recommend that you don't buy anything to begin with; just use whatever old hardware you have around. Setting up a server is mainly a question of software.

---

