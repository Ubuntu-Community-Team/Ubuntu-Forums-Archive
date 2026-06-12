---
title: "script to add botnet IPs from access_log automatically"
date: 2009-01-29
forum: Security
---

### Post by flowersrj on 2009-01-29
Hi,

Can anyone recommend an automated solution/script to automatically add IPs to iptables to drop them by reading the access logs?

Thanks,
Rich

---

### Post by wirelessmonkey on 2009-01-29
denyhosts...

---

### Post by hyper_ch on 2009-01-30
or fail2ban

however denyhosts also allows you to incorporate a common published IP list of considered bad IPs... so you might want to have a look at the config there.... not sure if fail2ban uses such a thing.

---

### Post by flowersrj on 2009-01-30
Hi,

Thanks for the replies.  I don't seem to have a problem with SSH but rather repeated GETs to non-existent folders and files for my website.  anyone know of a program/script to manage abuse of a website?  Or, a site dedicated to handling that issue?

Thanks,
Rich

---

