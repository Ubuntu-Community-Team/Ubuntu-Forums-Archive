---
title: "Network file server perhaps"
date: 2009-10-28
forum: Server Platforms
---

### Post by Yahtaa on 2009-10-28
I'm currently running Server 9.04 and I'm having difficulty getting access to the server through my linux mint, Vista, and XP computer.  I try to access the server and Mint will spit back an error saying it can't retrieve the servers share list.

SSH and Apache are running fine, and i'm using Shorewall as my firewall.
Slightly new to using Ubuntu...  Suggestions?

---

### Post by Ghostbear121 on 2009-10-28
This is a samba server right, for file sharing?

Open up your firewall real quick, try to connect.  :)  If you can, you're missing a firewall rule.  If not, then samba is misconfigured.  Don't forget to re-enable your rules right after though.

---

### Post by Yahtaa on 2009-10-28
brought down the firewall and still can't access from my linux mint machine.  

Host file
> 
127.0.0.1       localhost
127.0.1.1       ubuntu.hsd1.tn.comcast.net.     ubuntu
192.168.1.10    Server  WORKGROUP

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and this is my share info in smb.conf

> 
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755


not sure what i'm missing here.

---

### Post by Ghostbear121 on 2009-10-29
I see a typo in "browseable"  ;)

---

### Post by Yahtaa on 2009-10-29
I hoped that oversight would have been the end.  Still can't access the server through any of my machines

---

