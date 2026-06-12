---
title: "VMware 1.0.8 won't upgrade in 8.10"
date: 2008-11-18
forum: Virtualisation
---

### Post by fester225 on 2008-11-18
I've been running VMware Server for about a year now, and every few months it quits. The solution has been to re-install it with the latest version.

1.0.8 was installed as per the instructions in;
[http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_server.3.13.html](http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_server.3.13.html)

    tar zxf VMware-server-<xxxx>.tar.gz 
    cd vmware-server-distrib
    ./vmware-install.pl

At the end of the install there was a message indicating 1.0.8 was successfully installed. The VMware icon located on the Kubuntu taskbar no longer shows the VMware supplied icon, and when I click on what's still there, Kubuntu shows it to be loading for several seconds, then no VMware.

How do I get VMware 1.0.8 installed?

---

### Post by fester225 on 2008-11-18
Scratch the 8.10, I'm running Hardy.

---

### Post by veloce on 2008-11-18
Try starting it in a terminal using the "vmware" command.  This will allow you to see vmware's error message.

It sounds like it didn't install properly but the error message will confirm.

---

