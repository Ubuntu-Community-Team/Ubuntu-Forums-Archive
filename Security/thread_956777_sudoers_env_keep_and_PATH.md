---
title: "sudoers env_keep and PATH"
date: 2008-10-23
forum: Security
---

### Post by paul.p.carey on 2008-10-23
Hi

I would have expected env_keep to preserve my PATH when I sudo, but that doesn't seem to be happening. I'd be very grateful if someone could tell me what I'm doing wrong. 

Paul


paul@domU:~$ sudo cat /etc/sudoers 
Defaults        env_reset
Defaults        env_keep = "HOME USER PATH"

%sudo ALL=NOPASSWD: ALL

root	ALL=(ALL) ALL

paul@domU:~$ echo $PATH
/opt/ruby-enterprise/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
paul@domU:~$ sudo -s
root@domU:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@domU:~# cat /etc/lsb-release | grep REL
DISTRIB_RELEASE=8.04

---

### Post by cdenley on 2008-10-23
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651)

---

### Post by paul.p.carey on 2008-10-23
Great, thanks for the link.
Paul

---

