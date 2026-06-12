---
title: "is firewall needed with samba"
date: 2009-03-19
forum: Security
---

### Post by corkscrew on 2009-03-19
I'm a newbie'
I have a mixed home network set up with win xp and Hardy Heron,I am using samba to share folders across the network.
I connect to the internet via a router.
Do I need to install a firewall since I'm using router?

---

### Post by cdenley on 2009-03-19
Your router should function as a firewall, blocking outside computers from connecting to samba, but more importantly, you should have configured samba to only allow connections from your LAN.
[https://help.ubuntu.com/community/SettingUpSamba#/etc/samba/smb.conf](https://help.ubuntu.com/community/SettingUpSamba#/etc/samba/smb.conf)

---

### Post by bodhi.zazen on 2009-03-19
It depends on what you are wanting exactly.

I am running a samba server and I have some machines on my LAN I do NOT wish to allow access, so I use a firewall.

There are other solutions, but I firewall other things on that server anyways, so just as easy to use one tool form multiple tasks, gets the job done.

If you do not need to restrict your LAN then your router is sufficient.

IMO you should NOT use samba over the internet (if you need that, go for ssh).

---

### Post by Nxion on 2009-03-19
> **bodhi.zazen said:**
> 

IMO you should NOT use samba over the internet (if you need that, go for ssh).

To expand a little on what bodhi said, Yes for over the internet, Samba is NOT the way to go. SSH is safest and most secure. With ssh you can setup and configure [SSHFS]("https://help.ubuntu.com/community/SSHFS"). In essence, sshfs allows you to enable mounting of a remote filesystem on a local machine. It is pretty handy. I like it :)

---

### Post by corkscrew on 2009-03-19
thanks to all the replys feel a bit safer now!!!

---

