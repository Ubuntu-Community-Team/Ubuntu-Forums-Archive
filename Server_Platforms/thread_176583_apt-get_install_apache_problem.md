---
title: "apt-get install apache problem"
date: 2006-05-15
forum: Server Platforms
---

### Post by paulur on 2006-05-15
I've tried to install sth. using apt-get install, but there's error, like follows:

root@paul:/var/tmp/sft# apt-get install apache
Reading package lists... Done
Building dependency tree... Done
Package apache is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache has no installation candidate

Thank you so much!

Regards,
Paul

---

### Post by schweitzereffect on 2006-05-15
apt-get install apache2

---

### Post by paulur on 2006-05-15
[QUOTE=schweitzereffect]apt-get install apache2[/QUOTE]
That works!

But only for apache. I've got another package micro-httpd , which is download from [http://packages.ubuntulinux.org/breezy/web/micro-httpd](http://packages.ubuntulinux.org/breezy/web/micro-httpd) 

I put the packege in /var/tmp/sft, in that dir, when i run
apt-get install xxxx.deb

there's the same error.

Paul

---

### Post by schweitzereffect on 2006-05-15
dpkg -i xxx.deb

---

