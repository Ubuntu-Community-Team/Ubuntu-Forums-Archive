---
title: "LTSP Help"
date: 2011-07-22
forum: Server Platforms
---

### Post by adz13 on 2011-07-22
Hi, I am trying to install and configure LTSP on a server for a HP thin client to boot off. The version of Ubuntu that I am using is 11.04 x86 and it is a fresh install on a dual core system with 2GB RAM. I followed a guide which comprised of these commands.

sudo apt-get install ltsp-server-standalone openssh-server
sudo ltsp-build-client or if your on a 64-bit system with 32-bit machines do sudo ltsp-build-client –arch i386
for editing the server’s IP values use /etc/ltsp/dhcpd.conf
after that you need to restart DHCP server  – sudo /etc/init.d/dhcp3-server restart
and update sshkeys -sudo ltsp-update-sshkeys
and if you updated dhcpd.conf then you need to update you image also by typing in terminal ltsp-update-image

Everything seemed to install as it should but when I try to boot from the thin client it just times out and says no DHCP or proxy invites received. I turned DHCP off on the router and even tried another router, but I still get nothing. I am at a bit of a loose end and I hope someone on here can point me in the right direction of where I am going wrong.

Thanks :)

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
Firstly, natty uses DHCP4, which is:

sudo service isc-dhcp-server restart

And is there any chance you could post your subnet information(Gateway, Range, DNS, Mask) and the dhcpd.conf? 

That would help in debugging.

---

