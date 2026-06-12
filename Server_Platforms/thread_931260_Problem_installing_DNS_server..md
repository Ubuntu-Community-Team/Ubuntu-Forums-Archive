---
title: "Problem installing DNS server."
date: 2008-09-27
forum: Server Platforms
---

### Post by Tiersin on 2008-09-27
So I'm following the "perfect server" how-to and I've gotten to the DNS server and I'm having problems getting it to run. Everything up to the DNS server works. The how-to has me chroot bind9 to its own subdirectory, and somewhere in the process something goes wrong. I'm following all the steps in the [DNS section]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4") and when i get to the last step, where I need to restart bind9, i get a failure.

The syslog in /var/log records this after I try to restart it:

Sep 27 02:04:58 Neo named[14023]: starting BIND 9.4.2-P1 -u bind -t /var/lib/named
Sep 27 02:04:58 Neo named[14023]: found 1 CPU, using 1 worker thread
Sep 27 02:04:58 Neo named[14023]: loading configuration from '/etc/bind/named.conf'
Sep 27 02:04:58 Neo named[14023]: none:0: open: /etc/bind/named.conf: permission denied
Sep 27 02:04:58 Neo named[14023]: loading configuration: permission denied
Sep 27 02:04:58 Neo named[14023]: exiting (due to fatal error)
Sep 27 02:04:58 Neo kernel: [876550.941521] audit(1222502698.656:11): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=14024 profile="/usr/sbin/named" namespace="default"



I know it has something to do with the permissions, but i dont know what to change. Has anyone else had this problem?

---

### Post by amai on 2008-09-28
solution
run command
**sudo named -g -p 53**

it will tell you the COZ of the error
then just go correct it OR post results here

Chur 
Amai

---

### Post by Tiersin on 2008-09-28
I did that, its in the first post :)

---

### Post by jigsaws on 2008-09-28
It looks like problem with mandatory access control system, not with file permissions. Do you use selinux or apparmor?

---

### Post by jigsaws on 2008-09-28
Once more - check [http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893). It should solve your problem, I think.

---

### Post by Tiersin on 2008-09-28
Turns out apparmor was still running. Got it up and working now. I could have sworn that I stopped and removed it. Thanks for your help.

---

