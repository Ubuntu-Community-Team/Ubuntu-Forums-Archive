---
title: "samba 5-10 seconds delay"
date: 2007-03-19
forum: Server Platforms
---

### Post by flade on 2007-03-19
How when accessing from windows xp to samba server there is 5-10 seconds delay.
I mapped samba share to drive y: When I click drive Y: there is delay before folders are displayed. From here on there is no delay and sharing is just fine. 
I got feeling that windows is searching for samba server or does not get answer rightaway.

here is my samba conf:

```
#======================= Global Settings =======================

[global]

local master = yes
preferred master = yes
os level = 65
workgroup = mshome
server string = themachine
dns proxy = no
printcap name = /bin/false
winbind enum users = No
winbind enum groups = No
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

security = share
guest account = nobody
invalid users = root
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

[server-shareddata]
    comment = shares
    browseable = yes
    writeable = yes
    path = /media/data/sharedfolder
    public = yes

```

any help

---

### Post by alamba on 2007-03-19
Can you post a TCP dump of the network at the time when you first click the shared drive after a reboot? I typically use tethereal for this.

A

---

### Post by flade on 2007-03-19
I use Wireshark on windowsxp as Lnux command line gave a hude headache :)

I presume there's no difference.

Attachment below


regards:KS

---

### Post by Brazen on 2007-03-19
get rid of this line ```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```
This is an old parameter that was useful for the 2.4 kernel series, but actually slows things down on the latest 2.6 kernels.  Remove (or comment out with a #) this line and you WILL see better response times in Samba.  After making this change you will need to restart all your samba daemons (smbd, and maybe nmbd and winbind) or restart the server.

---

### Post by alamba on 2007-03-20
The network dump looks just about right. Like Brazen said, its probably the smb config option.

A

---

### Post by flade on 2007-03-20
Removed the line and delays are still there.

If I check witjh nmblookup -r servername i got no responce but if do that with client i get responce. How come.


regards,

---

