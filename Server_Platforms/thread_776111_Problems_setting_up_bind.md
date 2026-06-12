---
title: "Problems setting up bind"
date: 2008-04-30
forum: Server Platforms
---

### Post by spark01 on 2008-04-30
Hello, I am very new with Linux and servers and am trying to set up a mail server for clients. I am currently running Ubuntu 7.10 and have installed the newest version of bind from the ics website. I am following the following guide to create an internal and external chroot'ed environment [http://www.ecst.csuchico.edu/~dranch/LINUX/TrinityOS/cHTML/TrinityOS-c-24.html](http://www.ecst.csuchico.edu/~dranch/LINUX/TrinityOS/cHTML/TrinityOS-c-24.html)

I have followed the guide exactly, but changed the ip addresses and domain names to match my own. I am confused a bit with the part titled "24.12 Fixing SYSLOGing to understand the new CHROOTed setup" I was not able to execute the command 
"daemon syslogd -a /home/chroot-dns-int/dev/log -a /home/chroot-dns-ext/dev/log -m 0". 
when i do, it gives me this error "Invalid --acceptable argument: 0 (less than 10)"
I was told this is not very important if it runs or not so i moved on and encountered more problems i the section "24.13 Starting up and testing BIND"
when i run this command "/home/chroot-dns-int/usr/sbin/named -u chroot-dns-int -t /home/chroot-dns-int -f" it appears to do nothing. 

I was also confused with the named script file. The bgining of the file starts with this
# Source function library.
. /etc/rc.d/init.d/functions

# Source networking configuration.
. /etc/sysconfig/network

But i do not know where to find these files in Ubuntu! I believe this guide is for redhat.

Anyone know what i could have done wrong? :)

---

