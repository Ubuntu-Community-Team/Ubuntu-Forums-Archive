---
title: "Postfix master.lock: permission denied"
date: 2013-03-19
forum: Server Platforms
---

### Post by lcssanches on 2013-03-19
Hi guys,
I'm triyng setup the postfix, but with no success.

I am using webmin to configure.

my problem is that postfix won't start, always with the same message:


```
Mar 19 19:21:13 site postfix/postfix-script[1247]: starting the Postfix mail system
Mar 19 19:21:13 site postfix/master[1248]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Mar 19 19:21:14 site postfix/postfix-script[1318]: warning: group or other writable: /var/lib/postfix
Mar 19 19:21:14 site postfix/postfix-script[1325]: warning: not set-gid or not owner+group+world executable: /usr/sbin/postqueue
Mar 19 19:21:14 site postfix/postfix-script[1326]: warning: not set-gid or not owner+group+world executable: /usr/sbin/postdrop
Mar 19 19:21:14 site postfix/postqueue[1357]: warning: Mail system is down -- accessing queue directly

```
I'm going crazy with this... really! I don't know more what to do...I already tried to create the file master.lock, set permission, delete file, reboot server...

See the permissions:```
[INDENT]drwx-wx--- 2 postfix postdrop 4096 Mar 19 18:04 /var/spool/postfix/maildrop[/INDENT]
[INDENT]drwx--s--- 2 postfix postdrop 4096 Mar 19 17:54 /var/spool/postfix/public[/INDENT]
[INDENT]drwx------ 2 postfix root 4096 Mar 19 17:54 /var/spool/postfix/private[/INDENT]
[INDENT]-rwxrwS--- 1 root postdrop 13624 Feb 20 23:38 /usr/sbin/postdrop[/INDENT]
[INDENT]-rwxrws--- 1 root postdrop 13608 Feb 20 23:38 /usr/sbin/postqueue
**drwxrws--- 2 postfix   postdrop 4096 Mar 19 19:11 ****var/lib/postfix**[/INDENT]
[INDENT]

[/INDENT]

```It seems, obviously, its a permission problem, but I don't know how to fix it...

I have spent about 4 hours researching and triyng all I've found... but with success

thanks

---

