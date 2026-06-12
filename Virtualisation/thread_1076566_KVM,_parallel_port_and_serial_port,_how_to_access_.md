---
title: "KVM, parallel port and serial port, how to access a host's modem and printer?"
date: 2009-02-21
forum: Virtualisation
---

### Post by Tasu on 2009-02-21
As for the subject, it looks like there's little to none documentation about this subject, even on google... 
What I need is to use into the guest a serial (attached to ttyS0 on the host) modem and a parallel printer.
Thanks to google, I found that the old qemu comand can be invoked using the -console /dev/ttyS0 and -parallel /dev/parport0, but there are no infos about permissions or other configs, moreover, before making changes to the production server, I need to be sure that trying these commands can't lead to problems...
I assume that, if the qemu command can understand those switches, so can kvm, am I wrong here?
This issue goes further, since all my guests are managed by virsh (thus libvirt) and to define the domains I must use an XML file.. what do I have to write in that file to have the serial and parallel ports available to the guest I choose?

Thanks,
G.

---

### Post by Tasu on 2009-03-13
Bump...
°_° sorry, but I need an answer...

---

