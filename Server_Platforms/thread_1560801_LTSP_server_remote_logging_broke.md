---
title: "LTSP server remote logging broke"
date: 2010-08-25
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-08-25
I'm having frequent problems with my new LTSP setup and I'm trying to get logs from the clients.  I enabled rsyslog to listen to the network, and for a while I was getting log info from the clients.  Then I changed something (I think it was assigning a time server, since I noticed the clients were all over the map on what time or day (or month) they thought it was), and I'm not getting a single log packet from any client.

Here is my lts.conf
```

[default]
NBD_SWAP = True
LDM_AUTOLOGIN = True
LDM_DIRECTX = True
LDM_SYSLOG = True
LOCAL_APPS = False
SYSLOG_HOST=192.168.175.1
TIMESERVER=192.168.175.1
SERVER=192.168.175.1

#Local devices
#Disabled to free client resources
SOUND = False
LOCALDEV = False
LOCALDEV_DENY_CD = True
LOCALDEV_DENY_FLOPPY = True
LOCALDEV_DENY_INTERNAL_DISKS = True
LOCALDEV_DENY_USB = True
#X11 settings
X_MODE_0 = 1024x768
X_COLOR_DEPTH = 16
X_BLANKING = 0
#Screen sessions
SCREEN_01 = ldm

```

---

### Post by lykwydchykyn on 2011-05-05
Sadly, I've still never solved this problem.

I've completely rebuilt the client image with a default image.

I am getting no traffic on UDP or TCP port 514 on the server.  I checked on a client and it has a file called ltsp.conf in /etc/rsyslog.d/ with the following in it:
```

*.* @192.168.175.1

```

That's the correct IP of my LTSP server.  But no logs.

Anyone have any ideas?

EDIT: hang on, wait -- I do have logging, but I don't know how or what port it's going to.  It ends up in /var/log/syslog rather than the files it's supposed to split into, so I need to look into that...

---

### Post by lykwydchykyn on 2011-05-05
Ok, I think I have it all sorted now.

Apparently there is a bug in rsyslog that causes it to create files it cannot write to.

The solution was to change the rsyslog.conf so that it drops to user syslog but group adm (instead of group syslog).

Now it's logging properly.

Let's hope it stays that way!

---

