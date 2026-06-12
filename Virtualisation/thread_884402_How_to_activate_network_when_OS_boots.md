---
title: "How to activate network when OS boots"
date: 2008-08-09
forum: Virtualisation
---

### Post by divisortheory on 2008-08-09
Whew, so after about 5 hours I finally got Ubuntu HH up and running as a guest in VMWare Workstation 6.  The very last problem I have is activating the network interface.  I've installed VMWare Tools, which was successful, and currently I -can- activate my network interface and be able to use networking successfully if I do the following:

1) Run vmware-tools-config.pl
2) /etc/init.d/networking stop
3) rmmod vmxnet
4) modprobe vmxnet
5) /etc/init.d/networking start
6) Right click my KNetworkManager icon in KDE and activate the connection.

Problem is, when I reboot, steps 2-5 don't seem to have been persisted.  So how do I make it so that whatever these commands are doing under the hood (which to be quite honest I completely don't understand, and probably don't want to) happens every time I boot.  

Ideally I would want it to happen at an early enough stage in the boot process that whenever the network tries to automatically activate the connection the above steps should have already been done.

Thanks for any advice

---

