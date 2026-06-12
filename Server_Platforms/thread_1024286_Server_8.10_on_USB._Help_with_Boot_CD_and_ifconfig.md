---
title: "Server 8.10 on USB. Help with Boot CD and ifconfig?"
date: 2008-12-28
forum: Server Platforms
---

### Post by Rapture2k4 on 2008-12-28
Hello,

I recently installed Ubuntu Server 8.10 on a spare thumb drive to be used on an old Dell Dimension 4500. Unfortunately, this machine does not have a hard drive, will not boot from USB via BIOS, and I don't have a 1.44MB floppy disk laying around (yet I have a 5.25" floppy disk.. go figure).

Is there any way to make a boot CD to load USB drivers? I know you can from the LiveCD, but it only works for the desktop versions. About that, if I try to load server using that Boot CD, I can use GRUB's command line to manually load the USB stuff and boot from it:

```

root (hd0)
chainloader +1
boot

```

So this tells me the BIOS sees the USB drive and is treating it as a hard disk, but cannot boot from it? Also, this is a tedious task and doesn't really help if I have a power outage and I'm not home... my wife will never figure out how to get the machine up and running. 

I'm looking for an OS independent ISO that will load only what it needs to boot from USB. Since I have grub installed on the flash drive already, I don't need anything fancy. Any suggestions?

####################

Now, for the fun one. When I did get into server by manually booting from grub, I noticed I didn't have a connection to my network. The machine has an ethernet NIC in it and I know it works on the LiveCD. The server install doesn't even show anything when I do an ifconfig. How would I begin to troubleshoot this?

--Edit: Fixed it, I was referencing the wrong interface. The D-Link adapter is on PCI, so it was eth1, not eth0.

Thanx

---

### Post by shunthemask on 2009-02-08
Howdy,

It looks as though this link has the info that you require as far as booting a Ubuntu 8.10 system, but unfortunately isn't OS independent:

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")

I have a question in kind: how did you go about installing Ubuntu server to a USB thumb drive?

---

