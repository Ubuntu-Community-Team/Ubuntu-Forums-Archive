---
title: "Samba BDC W/W2k8 PDC"
date: 2010-01-14
forum: Server Platforms
---

### Post by tlsarles on 2010-01-14
I have a Windows 2k8 server acting as my domain controller. My goal is to have my Ubuntu 9.10 Server box share some folders via Samba, which should be authenticated via the PDC.

So far, it seems to be mostly working. The Ubuntu machine has joined the domain, and is browse-able to domain users. The only problem at this point, is that the shares are not writable. Would appreciate advice is anyone is familiar with this specific situation.

```

[global]
workgroup = smatech
netbios name = smalinux001
security = domain
idmap uid = 15000-20000
idmap gid = 15000-20000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
password server = 10.10.10.2
domain master = no
local master = yes

[www]
path = /var/www
writable=yes

```

---

### Post by neoanderthal on 2010-01-14
The default permissions for Samba as distributed with Ubuntu Server 8.04 is to make the shares read-only. You'll nead to add either 'read-only = no' or 'writable = yes' to your shares to enable your users to write to it. Also double-check your directory permissions to make sure they have write access also.

**edit** I forgot to mention that I believe the read-only permission is the samba default for all installations, but that I haven't tried anything newer than 8.04 on the server.

---

### Post by tlsarles on 2010-01-14
You will note the writable=yes in the config file :D

---

### Post by Iowan on 2010-01-14
Dunno if it needs a "write list=" option - or if it should default to all.

---

### Post by tlsarles on 2010-01-15
I figured out my problem. The config was actually OK, altho I am glad to learn of the write list option. The problem actually ended up being file system permissions. I just chowned the folder to my domain user

---

### Post by neoanderthal on 2010-01-15
> **tlsarles said:**
> You will note the writable=yes in the config file :D

I notice it now that you mention it *sheepish look*

I'm glad you got it squared away :)

---

