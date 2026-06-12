---
title: "Getting mdadm monitor to send E-mail"
date: 2006-08-16
forum: Server Platforms
---

### Post by Slim Backwater on 2006-08-16
I have installed Dapper Drake on a Software Raid (/dev/md0 and /dev/md1) and I've found that mdadm is running in Follow mode, which should to send me an E-mail if the raid fails; but I'm not receiving the E-mail.

I get these errors When I try this:
$ sudo mdadm -F --scan -t
sh: /usr/sbin/sendmail: No such file or directory
sh: /usr/sbin/sendmail: No such file or directory
sh: /usr/sbin/sendmail: No such file or directory
sh: /usr/sbin/sendmail: No such file or directory

most obviously because sendmail doesn't exist.

How do I install sendmail to get mdadm to send E-mail?  Or is there another way to configure mdadm to get around the lack of sendmail?

I have already edited /etc/mdadm/mdadm.conf and added the line MAILADDR with my E-mail address, and edited /etc/init.d/mdadm to set MAIL_TO to my address (from root), but I'm not sure what to do next.

Thanks!

._.

---

### Post by scandyna on 2006-08-18
Hi,

I have installed sendmail

I have edited /etc/default/mdadm and added this line:
MAIL_TO="xx@yy.z"

then
sudo /etc/init.d/mdadm restart

It works for me (Ubuntu Dapper)

---

### Post by gscaglia on 2006-08-27
Hi,
the file /etc/default/mdadm is automatically generated (in Ubuntu 6.06 LTS Server - Dapper Drake).

Run 

dpkg-reconfigure mdadm

for change the default sysadmin e-mail address (usually root),  configure and start the mdadm monitor service.

Bye,
Luca

---

