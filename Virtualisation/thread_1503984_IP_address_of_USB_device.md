---
title: "IP address of USB device"
date: 2010-06-07
forum: Virtualisation
---

### Post by xefix on 2010-06-07
Hi, all

I'm trying to work with a radio device, which I've connected to my computer via a USB port. On my host WinXP machine, the device has a set IP address and responds to ping. However, I am having a hard time figuring out what its IP address would be once I connect it to my Ubuntu guest. It appears in the device list output by the lsusb command, but I don't know where to find the IP address/port that it is connected to. I am using VirtualBox.
Thanks!

---

### Post by xefix on 2010-06-08
I'll try to clarify - maybe this will help. When I connect the device in Windows, it shows up under network connections as a local area connection. I also see it in the command line when I type ipconfig. It is not there when I try ifconfig in Ubuntu, however. I am using NAT as my network option, but I am not really as concerned about internet as I am about being able to communicate with the device. Can I use bridging or a host-only network to somehow enable my Ubuntu guest to recognize the USB device and be able to ping it?

---

### Post by pricetech on 2010-06-08
If XP is your host and Ubuntu your guest, your Ubuntu install is receiving an IP from XP.  Whatever that IP is, your XP host should NAT to everywhere else.

Therefore, whatever IP is assigned to the device by XP should be the IP you point to from Ubuntu and let XP do the translation.

Theoretically.

---

