---
title: "How can I increase the number of open files per process?"
date: 2016-02-26
forum: Server Platforms
---

### Post by david-sorber on 2016-02-26
I have a sever process (that runs as root) on Ubuntu 14.04.3 that sometimes needs to open several thousand files.  By default the max "soft" limit appears to be 1024 and the "hard" max appears to be 4096.

I have attempted to follow the instructions from here but nothing has worked:
[LIST]
[*][http://askubuntu.com/questions/162229/how-do-i-increase-the-open-files-limit-for-a-non-root-user](http://askubuntu.com/questions/162229/how-do-i-increase-the-open-files-limit-for-a-non-root-user)
[*][http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/](http://www.cyberciti.biz/faq/linux-increase-the-maximum-number-of-open-files/)
[*][http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/](http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/)
[/LIST]

Here is what I've done specifically:

[LIST=1]
[*]Edited /etc/sysctl.conf and added this at the bottom: ```
fs.file-max = 8192
```
[*]Edited /etc/security/limits.conf and added this at the bottom:
[/LIST]
[INDENT]```
root            hard    nofiles         8192
root            soft    nofiles         8192
```[/INDENT]

[LIST=1]
[*]Edited /etc/pam.d/common-session and /etc/pam.d/common-session-interactive and added this to the bottom:
[/LIST]
[INDENT]```
session required pam_limits.so
```
[/INDENT]

[LIST=1]
[*]Reboot.
[/LIST]

After reboot:
```
user@system:~$ sudo su
[sudo] password for user: 
root@system:/home/user# ulimit -Sn
1024
root@system:/home/user# ulimit -Hn
4096

```

Clearly my attempt to increase the limit to 8192 has not "taken".  I'm stuck on this any help would be greatly appreciated.

---

### Post by Doug S on 2016-02-26
All I have ever done is this:
```
doug@s15:~/config/etc/security$ diff -u limits.conf limits.conf.original
--- limits.conf 2015-06-30 13:28:29.681513667 -0700
+++ limits.conf.original        2015-06-30 07:13:11.170777196 -0700
@@ -1,6 +1,5 @@
 # /etc/security/limits.conf
 #
-# Smythies.com specific edits. 2011.01.06
 #Each line describes a limit for a user in the form:
 #
 #<domain>        <type>  <item>  <value>
@@ -25,8 +24,7 @@
 #        - data - max data size (KB)
 #        - fsize - maximum filesize (KB)
 #        - memlock - max locked-in-memory address space (KB)
-#        - nofile - max number of open files (smythies.com - so Samba will not complain)
-* - nofile 16384
+#        - nofile - max number of open files
 #        - rss - max resident set size (KB)
 #        - stack - max stack size (KB)
 #        - cpu - max CPU time (MIN)

```which gives me this:
```
doug@s15:~/config/etc/security$ sudo su
root@s15:/home/doug/config/etc/security# ulimit -Sn
16384
root@s15:/home/doug/config/etc/security# ulimit -Hn
16384

```

---

### Post by david-sorber on 2016-02-29
Thanks for the reply.  It looks like my problem was just a silly typo: "nofiles" instead of "nofile" in /etc/security/limits.conf.  Thanks again.

---

