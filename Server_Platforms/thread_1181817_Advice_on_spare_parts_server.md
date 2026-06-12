---
title: "Advice on spare parts server"
date: 2009-06-08
forum: Server Platforms
---

### Post by The Real Dave on 2009-06-08
If this is in the wrong place, please move it :lolflag:

Ok, so my question is this. I wish to make a FTP, NAS and Bittorrent server, out of spare parts that I have lying around. 

I have already attempted this, first in W2K Pro and then in FreeNAS. FreeNAS in theory was a much better OS choice, but kept crashing, freezing and destroying my data. So I reverted back to using W2K Pro, in this set up;

-Pentium II 450 Mhz
-128 Mb RAM
-W2K Pro on a 6Gb IDE Drive, with Bittorrent and RealVNC installed.
-250x2Gb SATAII Drives, in a Raid controller card, in RAID0 (not aiming for redundancy here)

Bittorrent was set to run at start up, and the whole system could be controlled headlessly via RealVNC. The RAID0 was configured with W2K's built in Dynamic Disks feature, the RAID then shared on my Windows network, mapped to the local machines. 

This setup works pretty much fine for me, however, I am worried that knowing W2K's pathetic security, and the fact that I have no anti-virus or firewalls installed on the machine (its behind my routers built in firewall, although I dont know how good that is, and is scanned once a week for viruses and malware, by a networked PC)

Can any advise another OS to use for this setup, or show me where Im going wrong and how to impove? Preferably without the need to purchasing anything BTW.

---

### Post by cariboo on 2009-06-08
By asking your question here, you have partially answered your own question. I would suggest using Ubuntu 8.04 LTS server. You can do everything you need with the server version, and 8.04 is a long term support version, and will be supported with security updates until 2013.

---

### Post by windependence on 2009-06-09
I think the trouble you had with FreeNAS was the fact that you have barely any memory on that box. You don't need much, but 512 would be much better. I don't think any system will function well for you with the amount you have. FreeBSD takes much less resources than Linux, and if it was a problem there, I'm sure it will be bigger with another OS. FreeNAS has been very stable for me, but I am running 1GB RAM on that box with 1.5TB storage.

-Tim

---

### Post by The Real Dave on 2009-06-09
Thanks for the advice guys, Im gonna give both of them a try :D Been meaning to upgrade its parts a bit for a while now

---

