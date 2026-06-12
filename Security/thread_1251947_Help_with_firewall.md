---
title: "Help with firewall"
date: 2009-08-28
forum: Security
---

### Post by Syntax. on 2009-08-28
Hi all :-)

I've set up a nice little home server on Ubuntu running a FTP server, VNC and SSH. This is just for me to be able to share files and access the box without a screen - around the home. I'm just wondering If anyone could tell me how I can deny any WAN packets from accessing them? I understand there is a built in firewall in Ubuntu but I have absolutely no idea how to get this thing setup to only allow users from 192.168.*.* to access my services. Oh and I plan to run a torrent program to seed some Ubuntu ISOs so I obviously want to keep that port open.

Thanks :)

---

### Post by cdenley on 2009-08-28
The TCP port used for torrents vary, so will will need to substitute "[port#]" with the correct TCP port.
```

sudo ufw default deny
sudo ufw allow from 192.168.0.0/16
sudo ufw allow proto tcp from any to any port [port#]
sudo ufw enable

```

---

