---
title: "MOTD problems"
date: 2012-08-14
forum: Server Platforms
---

### Post by junkyhlm on 2012-08-14
I'm having som trouble with the motd of my ubuntu server 12.04.
It seems like the motd wont fetch any new script i add to /etc/update-motd.d/ and when i have the files "00-header" and "10-help-text" activated the motd is double.
 
```
holmen@filserver:~$ ls -Al /etc/update-motd.d/
totalt 20
-rw-r--r-- 1 root root 1220 aug 14 08:43 00-header
-rw-r--r-- 1 root root 1358 aug 14 08:43 10-help-text
-rwxr-xr-x 1 root root  149 aug 14 08:35 90-updates-available
-rwxr-xr-x 1 root root  129 aug 14 08:35 91-release-upgrade
-rwxr-xr-x 1 root root  144 aug 14 08:35 98-reboot-required
```
 
I have tried with deleting /etc/motd.tail but that do not help. And when deactivating ALL scripts in /etc/update-motd.d/ i still get a mots when logging in:
 
```
holmen@filserver:~$ sudo chmod -x /etc/update-motd.d/*
```
 
```
login as: holmen
holmen@filserver's password:
No mail.
Last login: Tue Aug 14 09:14:33 2012 from <deleted>
holmen@filserver:~$

```
 
Anyone got an idea of what i'm encountering?

---

### Post by junkyhlm on 2012-08-14
Solved this with some googling.
 
Turns out that the /etc/ssh/sshd_config file wad the villain.
 
Just disabled motd in ssh config:
```
PrintMotd no
```

---

