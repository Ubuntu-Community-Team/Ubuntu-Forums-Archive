---
title: "How to setup Samba with AD on 14.04"
date: 2014-06-26
forum: Server Platforms
---

### Post by Romu on 2014-06-26
Hi,
I've successfully setup a 13.04 server with Samba and Active Directory.  But after few tries, I always fail on 14.04. My information sources are these posts:
[http://phreek.org/guides/ubuntu-samba-active-directory-member-server]("http://phreek.org/guides/ubuntu-samba-active-directory-member-server")
[http://community.spiceworks.com/topic/387677-ubuntu-server-13-04-samba-and-windows-7-8]("http://community.spiceworks.com/topic/387677-ubuntu-server-13-04-samba-and-windows-7-8")

My 14.04 server is well recorded into the AD. I can join the AD with "kinit Administrator", show my new ticket with "klist", or display users and groups with "wbinfo".

Here is my smb.conf:

```
[global]
workgroup = MYCOMPANY
server string = Samba Server Version %v
security = DOMAIN
realm = MYCOMPANY
domain master = no
local master = no
preferred master = no
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=131072 SO_SNDBUF=131072
use sendfile = true
# read raw = yes # Should provide a performance increase but currently untested, YMMV
# write raw = yes # Should provide a performance increase but currently untested, YMMV
unix password sync = yes
os level = 65
create mode = 777
syslog = 0
usershare allow guests = yes
max log size = 1000
directory mode = 777
pam password change = yes
 
idmap config * : backend = tdb
idmap config * : range = 100000-299999
idmap config TEST : backend = rid
idmap config TEST : range = 10000-99999
winbind separator = +
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind nested groups = yes
winbind refresh tickets = yes
template homedir = /home/%D/%U
template shell = /bin/bash
 
client use spnego = yes
client ntlmv2 auth = yes
encrypt passwords = yes
restrict anonymous = 2
log file = /var/log/samba/log.%m
max log size = 50

[dev]
comment = Dev
path = /shares/dev
writable = yes
valid users = @"MYCOMPANY"
#force group = "dev"
#directory mode = 0770
#force directory mode = 0770
#create mode = 0660
#force create mode = 0660
# Hide share from users who don't have access
#access based share enum = yes
# Hide files/directories if user doesn't have read access
#hide unreadable = yes

[admin]
comment = Dev
path = /shares/admin
writable = yes
valid users = @"MYCOMPANY\administratif"
write list = @"MYCOMPANY\administratif"
```

As you can see, there are 2 shares, one is restricted to a specific domain group, the other is not and is "open" to the whole domain. The behaviour is the same on both shares: always asking and a password. Any idea?

Thanks.

---

### Post by collisionystm on 2014-06-26
I know this is not the reply you are looking for but have you heard of Zentyal? It believe it may make your life a bit easier. Based on Ubuntu. Free. Option for paid support (like ubuntu). [http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by houstonbofh on 2014-06-29
I am finding a lot of new issues with 14.04...  If this is a new server, it may be better to drop back to 12.04 or to set it up from 12.04 and upgrade.

---

### Post by Romu on 2014-06-30
Switching to something like Zentyal is my next step, but currently, I just want to setup a nas.

---

### Post by darkoaus on 2014-09-12
I'm the guy who actually wrote that Ubuntu SAMBA guide and the reason you're having trouble is because 14.04 switched to SAMBA 4.1. Previously they used SAMBA 3.6 and there are some configuration changes required to get SAMBA 4.1 to play nice. I've been working on updated guides for the latest versions of most distros for a fair while now (time permitting) and am fairly close to having new guides available but in the meantime if you just want to build a basic NAS I'd recommend sticking with 13.04.

I might have been able to help sooner if you'd contacted me through the site :)

---

