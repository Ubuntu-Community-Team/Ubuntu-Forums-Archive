---
title: "login loops to login screen"
date: 2012-09-22
forum: Server Platforms
---

### Post by nralbers on 2012-09-22
I'm running into a frustrating issue in managing my ubuntu file and print server: any login attempt succeeds, but then goes straight back to the login prompt. This happens on the console, shh, webmin. I've tried the following:
[LIST]
[*]Tried a different password: bad login text shows. This means that the password isn't the problem.
[*]Started in recovery root prompt
[*]checked home directory permissions
[*]checked shell settings in /etc/passwd
[*]tried to use passwd as root to change user password. Fails with permission denied return code.
[/LIST]
The last actions I performed on the server before this problem showed up were to login via ssh and changed some settings in smb.conf to open up a file share as a public share on my LAN. I made the changes running in a sudo -s shell, so there could be a possible cause there, only I have no idea what.

Any suggestions? Obviously, at the moment I can only get into the machine via the recovery mode root console.

---

### Post by Habitual on 2012-09-22
> **nralbers said:**
> ... I can only get into the machine via the recovery mode root console.

How's your disk space free?
```
df -h /home
```

---

### Post by nralbers on 2012-09-23
> **Habitual said:**
> How's your disk space free?
```
df -h /home
```

The disk space was fine (3% used of 2 Tb)

I found the problem: I had been setting up samba using the configuration examples listed at [www.samba.org](www.samba.org) in the official howto. These settings create a config that doesn't play nice with the pam authentication modules as set up by ubuntu. I fixed the problem by logging in as root via the recovery console and restoring a backup of my previous configuration. After the fact I did a compare of the configuration by dumping the output of
$testparm -v <bad config>
and
$testparn -v <working config> 
and comparing the two.
The samba default configuration doesn't use pam authentication, while pam assumes that it does. Here are the defaults that were set differently on the bad configuration:
obey pam restrictions = No #should be yes
pam password change = No #should be yes
passwd program =  #should be /usr/bin/passwd %u
unix password sync = No #should be yes
security = share #Depricated, should be user
map to guest = Never # should probably be Bad user

---

