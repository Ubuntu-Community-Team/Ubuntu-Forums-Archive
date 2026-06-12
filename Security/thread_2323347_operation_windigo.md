---
title: "operation windigo"
date: 2016-05-04
forum: Security
---

### Post by steve253 on 2016-05-04
Hello there,

im pretty new to the linux scene but whenever i scan with chkrootkit i get a message i might be infected by operation windigo. after formatting and setting up ubuntu xenial, i still get the message. do i have to worry?

kind regards

---

### Post by Habitual on 2016-05-04
chkrootkit on a new install shows windigo?
Seems like that might be a false-positive.

upload the suspect file to virustotal.com and let them scan it.

---

### Post by steve253 on 2016-05-04
Used chkrootkit and the netstat command and they both report an infection. How do I get that report to upload ??

EDIT: ok i ran rkhunter, wich doesnt report any rootkit like operation windigo, but it does give a warning about suspicious file types found in /dev: /dev/shm/ pulse-shm- *numbers*

about 9 entries of them.

---

### Post by Habitual on 2016-05-04
> **steve253 said:**
> Used chkrootkit and the netstat command and they both report an infection. How do I get that report to upload ??

EDIT: ok i ran rkhunter, wich doesnt report any rootkit like operation windigo, but it does give a warning about suspicious file types found in /dev: /dev/shm/ pulse-shm- *numbers*

about 9 entries of them.

Yes, until you edit /etc/rkhunter.conf and[ make allowances for those Warnings]("http://ubuntuforums.org/showthread.php?t=2279382&p=13292801#post13292801") ;)
Summary of steps is at [http://ubuntuforums.org/showthread.php?t=2297227&p=13367123#post13367123](http://ubuntuforums.org/showthread.php?t=2297227&p=13367123#post13367123)

---

