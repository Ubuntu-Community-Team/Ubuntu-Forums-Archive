---
title: "Is Ubuntu update server affected by rootkit?"
date: 2008-12-18
forum: Security
---

### Post by chunchengch on 2008-12-18
There were some updates yesterday, including login (system login tools), passwd (change and administer password and group data) and xulrunner-1.9 etc, after that I ran command 'sudo rkhunter -c' and found some executable files seemed to be affected, such as /bin/login, /bin/su, /usr/bin/newgrp, /usr/bin/passwd, /usr/sbin/groupadd etc.

I restore the whole system with Clonezilla and run command 'sudo rkhunter -c' again this morning, no files are affected, than I download all the updates, unfortunately, the rkhunter still warns the affection of those files I mentioned above.

How could this happen in Ubuntu update server? and will these affections do the harm to my personal data? I really worry about it. thanks for any comment.

[ATTACH]96830[/ATTACH] [ATTACH]96831[/ATTACH] [ATTACH]96832[/ATTACH] [ATTACH]96833[/ATTACH]

---

### Post by Chayak on 2008-12-18
There's nothing wrong.  It's just flagging files that have changed which happens during an update.

---

### Post by kostkon on 2008-12-18
> **Chayak said:**
> There's nothing wrong.  It's just flagging files that have changed which happens during an update.
+1
False positives.

---

### Post by chunchengch on 2008-12-19
Thanks a lot, but I have two more questions,

1. If these warnings remain for days after the update, how can I tell if they are exact affections or just false positives?

2. Is rkhunter reliable?

---

### Post by cariboo on 2008-12-20
If you don't understand the results you are getting, I would suggest you have a look [here]("http://sourceforge.net/docman/display_doc.php?docid=35179&group_id=155034"). scroll down to:

```
3. USAGE QUESTIONS
```

Jim

---

### Post by chunchengch on 2008-12-22
I check the permissions of these files below, and find permissions of some files are lrwxrwxrwx, is that normal?

-rwxr-xr-x 1 root root 725136 2008-05-13 02:48 /bin/bash
-rwxr-xr-x 1 root root 30196 2008-06-27 08:31 /bin/cat
-rwxr-xr-x 1 root root 46664 2008-06-27 08:31 /bin/chmod
-rwxr-xr-x 1 root root 50792 2008-06-27 08:31 /bin/chown
-rwxr-xr-x 1 root root 75492 2008-06-27 08:31 /bin/cp
-rwxr-xr-x 1 root root 58960 2008-06-27 08:31 /bin/date
-rwxr-xr-x 1 root root 50812 2008-06-27 08:31 /bin/df
-rwxr-xr-x 1 root root 5468 2008-09-25 21:08 /bin/dmesg
-rwxr-xr-x 1 root root 26048 2008-06-27 08:31 /bin/echo
-rwxr-xr-x 1 root root 40560 2008-02-29 15:19 /bin/ed
-rwxr-xr-x 1 root root 96216 2008-07-17 17:47 /bin/egrep
-rwxr-xr-x 1 root root 55156 2008-07-17 17:47 /bin/fgrep
-rwxr-xr-x 1 root root 22536 2007-11-23 18:15 /bin/fuser
-rwxr-xr-x 1 root root 100312 2008-07-17 17:47 /bin/grep
-rwxr-xr-x 1 root root 199468 2008-05-30 04:37 /bin/ip
-rwxr-xr-x 1 root root 13748 2008-10-30 12:11 /bin/kill
-rwxr-xr-x 1 root root 35080 2008-12-08 17:17 /bin/login
-rwxr-xr-x 1 root root 96216 2008-06-27 08:31 /bin/ls
-rwxr-xr-x 1 root root 5464 2008-10-14 23:52 /bin/lsmod
-rwxr-xr-x 1 root root 9556 2008-06-02 00:17 /bin/mktemp
-rwxr-xr-x 1 root root 30316 2008-09-25 21:08 /bin/more
-rwsr-xr-x 1 root root 92584 2008-09-25 21:08 /bin/mount
-rwxr-xr-x 1 root root 83732 2008-06-27 08:31 /bin/mv
-rwxr-xr-x 1 root root 105068 2008-07-17 17:13 /bin/netstat
-rwxr-xr-x 1 root root 79636 2008-10-30 12:11 /bin/ps
-rwxr-xr-x 1 root root 30200 2008-06-27 08:31 /bin/pwd
-rwxr-xr-x 1 root root 38452 2008-06-27 08:31 /bin/readlink
-rwxr-xr-x 1 root root 42900 2008-05-03 14:53 /bin/sed
[COLOR="Red"]lrwxrwxrwx 1 root root 4 2008-11-21 21:37 /bin/sh -> dash[/COLOR]
-rwsr-xr-x 1 root root 31012 2008-12-08 17:17 /bin/su
-rwxr-xr-x 1 root root 46616 2008-06-27 08:31 /bin/touch
-rwxr-xr-x 1 root root 26052 2008-06-27 08:31 /bin/uname
-rwxr-xr-x 1 root root 946 2008-09-04 03:46 /bin/which
-rwxr-xr-x 1 root root 87924 2008-06-21 00:07 /bin/dash
[COLOR="Red"]lrwxrwxrwx 1 root root 21 2008-11-21 21:38 /usr/bin/awk -> /etc/alternatives/awk[/COLOR]
-rwxr-xr-x 1 root root 26052 2008-06-27 08:31 /usr/bin/basename
-rwxr-xr-x 1 root root 9612 2008-10-13 21:10 /usr/bin/chattr
-rwxr-xr-x 1 root root 38364 2008-06-27 08:31 /usr/bin/cut
-rwxr-xr-x 1 root root 62716 2007-05-05 00:41 /usr/bin/diff
-rwxr-xr-x 1 root root 26052 2008-06-27 08:31 /usr/bin/dirname
-rwxr-xr-x 1 root root 371244 2008-09-03 20:03 /usr/bin/dpkg
-rwxr-xr-x 1 root root 100212 2008-09-03 20:03 /usr/bin/dpkg-query
-rwxr-xr-x 1 root root 75436 2008-06-27 08:31 /usr/bin/du
-rwxr-xr-x 1 root root 26052 2008-06-27 08:31 /usr/bin/env
-rwxr-xr-x 1 root root 13744 2008-07-11 18:22 /usr/bin/file
-rwxr-xr-x 1 root root 141952 2008-07-04 04:08 /usr/bin/find
[COLOR="Red"]lrwxrwxrwx 1 root root 11 2008-11-21 21:38 /usr/bin/GET -> lwp-request[/COLOR]
-rwxr-xr-x 1 root root 2248 2008-06-27 08:31 /usr/bin/groups
-rwxr-xr-x 1 root root 38428 2008-06-27 08:31 /usr/bin/head
-rwxr-xr-x 1 root root 30188 2008-06-27 08:31 /usr/bin/id
-rwxr-xr-x 1 root root 14696 2007-11-23 18:15 /usr/bin/killall
-rwxr-xr-x 1 root root 13716 2008-10-14 21:02 /usr/bin/last
-rwxr-xr-x 1 root root 9620 2008-12-08 17:17 /usr/bin/lastlog
-rwxr-xr-x 1 root root 5862 2008-09-29 18:40 /usr/bin/ldd
-rwxr-xr-x 1 root root 120884 2008-02-02 11:51 /usr/bin/less
[COLOR="Red"]lrwxrwxrwx 1 root root 24 2008-11-21 21:38 /usr/bin/locate -> /etc/alternatives/locate[/COLOR]
-rwxr-xr-x 1 root root 10000 2008-09-25 21:08 /usr/bin/logger
-rwxr-xr-x 1 root root 9604 2008-10-13 21:10 /usr/bin/lsattr
-rwxr-xr-x 1 root root 112872 2008-05-03 14:54 /usr/bin/lsof
[COLOR="Red"]lrwxrwxrwx 1 root root 22 2008-11-22 00:14 /usr/bin/mail -> /etc/alternatives/mail[/COLOR]
-rwxr-xr-x 1 root root 34336 2008-06-27 08:31 /usr/bin/md5sum
-rwxr-sr-x 1 root mlocate 30260 2008-06-26 22:17 /usr/bin/mlocate
-rwsr-xr-x 1 root root 26728 2008-12-08 17:17 /usr/bin/newgrp
-rwsr-xr-x 1 root root 32988 2008-12-08 17:17 /usr/bin/passwd
-rwxr-xr-x 1 root root 1269408 2008-07-24 17:20 /usr/bin/perl
-rwxr-xr-x 1 root root 14272 2007-11-23 18:15 /usr/bin/pstree
-rwxr-xr-x 1 root root 339189 2008-10-01 19:41 /usr/bin/rkhunter
-rwxr-xr-x 1 root root 30348 2008-06-27 08:31 /usr/bin/runcon
-rwxr-xr-x 1 root root 38432 2008-06-27 08:31 /usr/bin/sha1sum
-rwxr-xr-x 1 root root 26376 2008-10-09 22:33 /usr/bin/size
-rwxr-xr-x 1 root root 71376 2008-06-27 08:31 /usr/bin/sort
-rwxr-xr-x 1 root root 46652 2008-06-27 08:31 /usr/bin/stat
-rwxr-xr-x 1 root root 195996 2008-05-27 17:50 /usr/bin/strace
-rwxr-xr-x 1 root root 26360 2008-10-09 22:33 /usr/bin/strings
-rwsr-xr-x 1 root root 115136 2008-09-01 21:17 /usr/bin/sudo
-rwxr-xr-x 1 root root 50792 2008-06-27 08:31 /usr/bin/tail
-rwxr-xr-x 1 root root 26120 2008-06-27 08:31 /usr/bin/test
-rwxr-xr-x 1 root root 72600 2008-10-30 12:11 /usr/bin/top
[COLOR="Red"]lrwxrwxrwx 1 root root 10 2008-11-21 21:39 /usr/bin/touch -> /bin/touch[/COLOR]
-rwxr-xr-x 1 root root 42516 2008-06-27 08:31 /usr/bin/tr
-rwxr-xr-x 1 root root 34284 2008-06-27 08:31 /usr/bin/uniq
-rwxr-xr-x 1 root root 26076 2008-06-27 08:31 /usr/bin/users
-rwxr-xr-x 1 root root 21964 2008-10-30 12:11 /usr/bin/vmstat
[COLOR="Red"]lrwxrwxrwx 1 root root 19 2008-11-21 21:39 /usr/bin/w -> /etc/alternatives/w[/COLOR]
-rwxr-xr-x 1 root root 9912 2008-10-30 12:11 /usr/bin/watch
-rwxr-xr-x 1 root root 34348 2008-06-27 08:31 /usr/bin/wc
-rwxr-xr-x 1 root root 230168 2008-07-25 15:27 /usr/bin/wget
-rwxr-xr-x 1 root root 93680 2008-07-11 23:02 /usr/bin/whatis
-rwxr-xr-x 1 root root 9856 2008-09-25 21:08 /usr/bin/whereis
[COLOR="Red"]lrwxrwxrwx 1 root root 10 2008-11-21 21:39 /usr/bin/which -> /bin/which[/COLOR]
-rwxr-xr-x 1 root root 38472 2008-06-27 08:31 /usr/bin/who
-rwxr-xr-x 1 root root 26052 2008-06-27 08:31 /usr/bin/whoami
-rwxr-xr-x 1 root root 100564 2008-05-06 18:03 /usr/bin/mawk
-rwxr-xr-x 1 root root 14821 2008-05-03 14:06 /usr/bin/lwp-request
-rwxr-xr-x 1 root root 87968 2008-05-10 01:45 /usr/bin/bsd-mailx
-rwxr-xr-x 1 root root 13780 2008-10-30 12:11 /usr/bin/w.procps
-rwxr-xr-x 1 root root 34644 2008-10-14 23:52 /sbin/depmod
-rwxr-xr-x 1 root root 65648 2008-07-17 17:13 /sbin/ifconfig
-rwxr-xr-x 1 root root 34668 2008-10-13 06:18 /sbin/ifdown
-rwxr-xr-x 1 root root 34668 2008-10-13 06:18 /sbin/ifup
-rwxr-xr-x 1 root root 104364 2008-09-30 07:52 /sbin/init
-rwxr-xr-x 1 root root 5480 2008-10-14 23:52 /sbin/insmod
[COLOR="Red"]lrwxrwxrwx 1 root root 7 2008-11-21 21:38 /sbin/ip -> /bin/ip
lrwxrwxrwx 1 root root 10 2008-11-21 21:38 /sbin/lsmod -> /bin/lsmod[/COLOR]
-rwxr-xr-x 1 root root 9780 2008-10-14 23:52 /sbin/modinfo
-rwxr-xr-x 1 root root 22432 2008-10-14 23:52 /sbin/modprobe
-rwxr-xr-x 1 root root 9736 2008-10-14 23:52 /sbin/rmmod
-rwxr-xr-x 1 root root 38444 2008-09-30 07:52 /sbin/runlevel
-rwxr-xr-x 1 root root 13748 2008-10-14 21:02 /sbin/sulogin
-rwxr-xr-x 1 root root 13732 2008-10-30 12:11 /sbin/sysctl
-rwxr-xr-x 1 root root 31632 2008-08-30 08:40 /sbin/syslogd
-rwxr-xr-x 1 root root 34022 2008-06-26 16:33 /usr/sbin/adduser
-rwxr-xr-x 1 root root 26056 2008-06-27 08:31 /usr/sbin/chroot
-rwxr-xr-x 1 root root 35744 2008-09-10 03:46 /usr/sbin/cron
-rwxr-xr-x 1 root root 34240 2008-12-08 17:17 /usr/sbin/groupadd
-rwxr-xr-x 1 root root 28876 2008-12-08 17:17 /usr/sbin/groupdel
-rwxr-xr-x 1 root root 34188 2008-12-08 17:17 /usr/sbin/groupmod
-rwxr-xr-x 1 root root 32968 2008-12-08 17:17 /usr/sbin/grpck
-rwxr-xr-x 1 root root 5440 2008-12-08 17:17 /usr/sbin/nologin
-rwxr-xr-x 1 root root 28860 2008-12-08 17:17 /usr/sbin/pwck
-rwxr-xr-x 1 root root 5492 2008-05-03 15:14 /usr/sbin/tcpd
-rwxr-xr-x 1 root root 68572 2008-12-08 17:17 /usr/sbin/useradd
-rwxr-xr-x 1 root root 43612 2008-12-08 17:17 /usr/sbin/userdel
-rwxr-xr-x 1 root root 68412 2008-12-08 17:17 /usr/sbin/usermod
-rwxr-xr-x 1 root root 35336 2008-12-08 17:17 /usr/sbin/vipw

---

### Post by cariboo on 2008-12-22
Those are files that symlinked to commands in other directories. For more info on symlinks, in a terminal type:

```
man symlink
```

Jim

---

### Post by chunchengch on 2008-12-22
> **cariboo907 said:**
> Those are files that symlinked to commands in other directories...

Thank you Jim.

---

### Post by chunchengch on 2008-12-23
one more question, I find some files have the permission -rw[COLOR="Red"]s[/COLOR]r-xr-x, 

-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 92584 2008-09-25 21:08 /bin/mount
-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 31012 2008-12-08 17:17 /bin/su
-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 26728 2008-12-08 17:17 /usr/bin/newgrp
-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 32988 2008-12-08 17:17 /usr/bin/passwd
-rw[COLOR="Red"]s[/COLOR]r-xr-x 1 root root 115136 2008-09-01 21:17 /usr/bin/sudo


then I search on the web and find this warning in this document [http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm), now, what should I do? thanks for reply. 

[COLOR="Blue"]...

Suppose we change the view program to have the SUID bit on:

   -rw[COLOR="Red"]s[/COLOR]--x--x    1 root    bin         4515 Aug 14 13:08 view

Now, when Jane runs this SUID program, the access to memo.txt is permitted.  When view attempts to read() the file, the system doesn't think Jane is attempting to read, it thinks "root" is the user.  So the access is allowed.

A similar substitution occurs if the SGID bit is set and any execute bits are set.  The group ID checked is not the current user, but the group of the program. 
...
[/COLOR]
[COLOR="Red"]
...
WARNING:   SUID and SGID programs can be dangerous.  They are not usually needed.  SUID and SGID scripts are incredibly dangerous and can easily allow evil-doers super-user access to your system!!  *Never* allow a SUID or SGID writable program on you system for even a minute! 
...[/COLOR]

---

### Post by bodhi.zazen on 2008-12-23
I do not mean to be rude, or discourage learning, but you really need to be willing to do some reading / research on your own.

By that, why are you trusting security to a bunch of clowns on the Ubuntu forums ? This is not even a security focused site :lolflag:

Start by assuming your system is secure as you just did a fresh install and have not installed anything outside of the repos.

If you do not trust the Ubuntu repos, then you really need to move to something like LFS or similar.

Second you need to learn what is "Normal". What is the normal logs ? What programs are normally set SUID ?

HIDS, such as rkhunter and others, will detect system files which change. These files change when you edit them or update. You should not be surprised when these changes show up when you scan yoru box after updates.

The applications you named normally run as suid. If you change them you will not be able to log in for example.

If you are not sure, use google to see what they are and how they work.

IMO learning to self learn is the best security practice I can suggest to you.

---

### Post by chunchengch on 2008-12-23
> **bodhi.zazen said:**
> ...
By that, why are you trusting security to a bunch of clowns on the Ubuntu forums ? This is not even a security focused site...

I don't think Chayak, kostkon, and cariboo907 are "a bunch of clowns", I appreciate their kindness to help me.

If it is not appropriate to ask security problem in Ubuntu forum, maybe category "Security Discussions" should be removed.

> **bodhi.zazen said:**
> ...
If you do not trust the Ubuntu repos, then you really need to move to something like LFS or similar...

I asked a question concerning security of Ubuntu update server does not mean that I don't trust Ubuntu, how could you get this conclusion? if you were right, no one can ask question here.

> **bodhi.zazen said:**
> ...
Second you need to learn what is "Normal". What is the normal logs ? What programs are normally set SUID ?...

yes, you are right, that is what I am doing.

> **bodhi.zazen said:**
> ...
HIDS, such as rkhunter and others, will detect system files which change. These files change when you edit them or update. You should not be surprised when these changes show up when you scan yoru box after updates.

The applications you named normally run as suid. If you change them you will not be able to log in for example...

thanks a lot for your explanation.

> **bodhi.zazen said:**
> ...
but you really need to be willing to do some reading / research on your own...

maybe I asked some stupid questions, but I do really learn hard enough to understand Linux and Ubuntu, however I am too dumpish to know everything, so I need help here.

> **bodhi.zazen said:**
> I do not mean to be rude, or discourage learning,...
I am sorry to say that you are really too rude to be an Ubuntu Guru.

---

