---
title: "how do I test my webserver on a VM?"
date: 2012-07-06
forum: Virtualisation
---

### Post by zoomiest on 2012-07-06
I have Ubuntu Server loaded on a  VMware Player/Windows Vista host.

I have installed the LAMP stack. How can I test the webserver? Where in Windows Vista can I go to see if my webserver is serving up page?

I have gone to the Network area, and also the Computer area (my apologies for mentioning Windows here...) to see if there is anything new nothing.

This installation is to test my backups for a web app I am having built, and so I just need a place to load the backups... and rest a couple of tests every time major backup.

Thanks in advance.

---

### Post by zoomiest on 2012-07-06
Whew - found my own answer here:
[http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode](http://superuser.com/questions/245156/how-can-i-connect-to-a-web-server-running-in-a-vm-when-the-vm-is-in-nat-mode)

---

### Post by CharlesA on 2012-07-07
Another alternative is to just use bridged networking instead of NAT, that would put both machines on the same subnet, and allow them to talk to each other.

---

