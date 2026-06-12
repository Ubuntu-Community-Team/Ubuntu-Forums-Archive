---
title: "LTSP dhcpd.conf for running multiple chroot"
date: 2011-08-17
forum: Server Platforms
---

### Post by kragsterman on 2011-08-17
Hi!

 I have some experience of LTSP, been running it for some yrs now. What I want to do is to run at least three different choot's, and I need some help to configure the dhcpd.conf for the different clients to find their right way to the proper chroot environment.

 I'm going to have one i386 chroot, that is going to be the default, and then an x86_64 to be controlled by mac adresses, and as well another specialized i386 as well to be controlled by mac adress.

 I'm going to run a DVB steaming server(VLC) as the specialized i386 chroot, and the x86_64 clients as HD TV stations.

 As for your information I can also add that I'm going to permit local app's at the x86_64 clients, to be able to run a DVB client locally.

 I'd appreciate some help with the design of the dhcpd.conf for this!

 Thanks in advance!

 Rgrds Johan

---

