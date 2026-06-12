---
title: "Ubuntu 10.4 LTSP Thin Cient failed Boot"
date: 2010-10-02
forum: Server Platforms
---

### Post by jsmith7735 on 2010-10-02
I've installed Ubuntu 10.4 via the alternate cd, with all standard options within a virtual machine using virtualbox. The thin client is also a virtual machine within virtualbox.

The Problem

After booting the thin client it finds the dhcp server and begins to load the pxelinux.0 file then gets to the ubuntu splash screen. It then goes to Busybox terminal with Error: failed to connect to NBD Server.

I've done the same setup using 9.04 inside a VM and it work perfectly.

I'm a newbie when it comes to linux any help would greatly be appreciated.

Ran sudo ltsp-update-sshkeys
      sudo ltsp-update-image

Rebooted the LTSP server and reboot the thin client I no longer get the Failed to connect to NBD server messsage but the system just hangs.

After reboot of the Host system and Ltsp server then running a thin client from another xp machine the system now boots up but takes about 10 minutes.

I wonder if its my host system for the LTSP Server which is Dell Dimension 3000 P4 2.8ghz 1gb ram 80gb system drive, 1tb data drive

---

