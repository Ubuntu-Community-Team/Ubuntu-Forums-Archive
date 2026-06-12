---
title: "Any reason not to add &quot;www-data&quot; to &quot;shadow&quot; group?"
date: 2009-03-21
forum: Server Platforms
---

### Post by christian.convey on 2009-03-21
I'm running Ubuntu 8.04 with apache2.  My customer wants the box's users' login passwords to stay in sync with the passwords they have to supply to that same computer's web pages.

I noticed that if I just add the user account used by apache2 ("www-data") to the "shadow" unix group, then apache2 can read the /etc/shadow file.  I also confirmed that if I then put this line into my apache2 config files:
      AuthUserFile /etc/shadow

Then the things work just as my customer requested.

Can anyone comment on the wisdom of this approach?

Thanks,
Christian

---

### Post by cariboo on 2009-03-21
I have a default LAMP install and www-data is already in /etc/shadow

```
cat /etc/shadow
root:!:14260:0:99999:7:::
daemon:*:14260:0:99999:7:::
bin:*:14260:0:99999:7:::
sys:*:14260:0:99999:7:::
sync:*:14260:0:99999:7:::
games:*:14260:0:99999:7:::
man:*:14260:0:99999:7:::
lp:*:14260:0:99999:7:::
mail:*:14260:0:99999:7:::
news:*:14260:0:99999:7:::
uucp:*:14260:0:99999:7:::
proxy:*:14260:0:99999:7:::
**www-data**:*:14260:0:99999:7:::
backup:*:14260:0:99999:7:::
list:*:14260:0:99999:7:::
irc:*:14260:0:99999:7:::
gnats:*:14260:0:99999:7:::
nobody:*:14260:0:99999:7:::
libuuid:!:14260:0:99999:7:::
syslog:*:14260:0:99999:7:::
klog:*:14260:0:99999:7:::
mysql:!:14260:0:99999:7:::
sshd:*:14260:0:99999:7:::
saned:*:14260:0:99999:7:::
landscape:*:14260:0:99999:7:::
messagebus:*:14260:0:99999:7:::
avahi:*:14260:0:99999:7:::
polkituser:*:14260:0:99999:7:::
haldaemon:*:14260:0:99999:7:::
hplip:*:14260:0:99999:7:::
jim:$1$DWZe//h6$5SA3WS3/HsoxCNx.iD5wN0:14260:0:99999:7:::
proftpd:!:14260:0:99999:7:::
ftp:*:14260:0:99999:7:::
Debian-exim:!:14261:0:99999:7:::
arpwatch:!:14293:0:99999:7:::
```

Jim

---

