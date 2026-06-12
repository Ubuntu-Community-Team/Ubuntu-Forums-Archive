---
title: "Samba installation broken after removing eBox?"
date: 2009-07-27
forum: Server Platforms
---

### Post by nerr on 2009-07-27
Hey everybody, I was experimenting with eBox yesterday, and installed its Samba module to play around with, only to realize that it didn't mesh right with the Samba setup I had already created.  I got bored messing with eBox, and figure I won't really need any other form of remote administration besides an SSH connection, so I removed eBox.

The problem now is that my Samba installation appears to be broken and inaccessible from any Windows machine in the house.  I've tried stopping and restarting the daemons, disabling the ufw firewall to make sure that wasn't the culprit, and all I can figure is that removing eBox caused some sort of issue with the machine.  I can roll back to a backup of a few days ago if that might help me out, but I'd prefer to avoid that if possible at this point.  Could removing eBox have damaged my existing Samba installation, and if so, how can I fix it?

Here's my smb.conf file, if it's any help.  Thank you!
[http://files.getdropbox.com/u/1362547/smb.txt](http://files.getdropbox.com/u/1362547/smb.txt)

---

### Post by swerdna on 2009-07-28
I suggest turning off any lainux firewall tempoarrily (diagnostic measure) and abcking up smb.conmf and then trying this overwrite of the [global] stanza:
```
[global]
workgroup = mylastname
netbios name = servnerr-1
server string = Home server running on mylastname network
name resolve order = bcast host lmhosts wins
passdb backend = tdbsam
map to guest = Bad User
local master = yes
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```
Leave the shares as is, they look OK.

Re-add your users to the samba user database. Then reboot.

If you really have set your xp boxes to report to a wins server, report that here and we'll reconsider, otherwise go ahead.

Reference: [Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

