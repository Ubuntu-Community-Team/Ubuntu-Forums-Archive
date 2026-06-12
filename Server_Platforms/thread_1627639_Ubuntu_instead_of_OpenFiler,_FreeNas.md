---
title: "Ubuntu instead of OpenFiler, FreeNas"
date: 2010-11-21
forum: Server Platforms
---

### Post by ebs16 on 2010-11-21
I am building a NAS for a fraternity house. The current system specs are: dual core 2ghz Celeron, 2gb ram, a 640 GB RAID1 for the OS and a ~4TB RAID5 for data. I am looking to have the machine serve files over samba and music over iTunes/DAAP. Most shares are to be open while others are to be password protected. Having the server work as a VPN endpoint would also be a plus.

I have tried FreeNAS and OpenFiler. I have issues with both. FreeNAS proved to be unstable -- neither RAIDZ or RAID worked properly. It also would not give me granular enough control over access permissions. OpenFiler would not install on the hardware -- there are some compatibility issues with certain Intel chipsets -- and I can't spend any more time trying to get it to run (3 days + already).

I am just considering going with a regular install of Ubuntu Desktop or Ubuntu Mint Desktop and running the required services manually. I would replace the web interface of OpenFiler and FreeNAS with a VNC server, allowing the admin to just remote in.

I don't expect a lay person to be able to administer the machine, but I don't want to make things too difficult for whomever takes over admin responsibilities. Ideally, they should be able to maintain the machine without resorting to a terminal session.


I am worried about a full blown user OS being overkill, but the system should be able to handle it without degrading performance. I am also worried about the OS going ahead an updating itself, breaking something (why I'm considering mint).

Is this a good idea? Why or why not? Any constructive input would be appreciated.

---

### Post by Joe of loath on 2010-11-21
Ubuntu server would be more appropriate, although personally I'd choose Debian. You can't even install to RAID using the regular desktop CD, at least not last time I checked.

---

### Post by ebs16 on 2010-11-21
Any specifics as to why you would use Debian over Ubuntu?

Also, using a server build would require using shell for updating, which does not meet my spec.

---

### Post by rubylaser on 2010-11-21
I'd encourage the shell as well for a server, but if you don't want to admin from the cli, you can adminstrate everything from webmin via the web if you'd like or use a Desktop install (I'd go webmin).  I'd also encourage using Debian Lenny (current stable), it's not as current as Ubuntu's packages, but it's rock solid (not that Ubuntu isn't).

You'll just want to 
```
sudo apt-get install mdadm samba openldap
```
To get samba sharing, software raid, and user permissions.  Then add OpenVPN if you'd like, but I'd much rather run this at the firewall, via Tamato or DD-WRT firmware on a router, Cisco's IPSEC VPN, or IPCOP's OpenVPN.

Finally, you'll want to use forked-daapd (mt-daapd replacement), because iTunes 10 broke mt-daapd.

Good luck.

---

### Post by ebs16 on 2010-11-22
Does anyone have experience with Zentyal?

---

### Post by stefan73 on 2010-11-22
why not run ubuntu server for filesharing and pfsense (with built-in vpn server) in a virtual machine to do the firewalling? Or ubuntu server as host and virtual machines for all the rest? 

And webmin seems indeed a good choice, makes administration a lot easier if you don't like them to use cli.

---

### Post by chenier on 2011-01-23
to ebs16, my experience with Zentyal so far is pretty good.  Not everything is perfect yet, but a lot of pieces are coming together in a very nice, easy to use package.  It is built on Ubuntu server, which is a plus.

---

### Post by ebs16 on 2011-01-23
> **chenier said:**
> to ebs16, my experience with Zentyal so far is pretty good.  Not everything is perfect yet, but a lot of pieces are coming together in a very nice, easy to use package.  It is built on Ubuntu server, which is a plus.

I've been using Zentyal for over a month now. It's great, and is far better than the other solutions I tried out originally.

---

### Post by Vegan on 2011-01-23
I use SAMBA for file server purposes and it is satisfactory.

WEBMIN is fine for most administration tasks, but I still use a terminal frequently.

---

