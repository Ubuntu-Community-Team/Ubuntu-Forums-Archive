---
title: "No Internet on Guest (please help...)"
date: 2008-05-02
forum: Virtualisation
---

### Post by yssida on 2008-05-02
I just installed WinXP inside an Ubuntu Hardy host. No matter what I did, there didn't appear to be an internet connection. Also, I can't mount my USB drive, spewing out this message:

> 
Not permitted to open the USB device, check usbfs options.


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Regards,
y

---

### Post by yssida on 2008-05-02
I installed it on Virtual Box.

---

### Post by yssida on 2008-05-02
bump?

---

### Post by Princey on 2008-05-02
I'm having an issue with no Internet in the windows guest on virtual box. Here's what's happening.

I installed the Personal use one from Innotek's website on a fresh install of AMD 64 bit Hardy Heron (Kubuntu 8.04). Installation went smooth, so did the usb support, but no internet. I've tried all three adapters (had to download the intel drivers for it) but nothing under NAT which is the default. I made sure to reboot just in case. When I tried host networking, I'm thrown an error message  > 
Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

  on start up and the vm doesn't load at all. The only setting that gets me a successful boot is NAT but no internet. I thought perhaps it was my XP install, so I used another XP OEM CD that I got with an Acer Laptop purchase some years ago. Still, no INTERNET. Any ideas as to what I should do? Just as a side note, not sure if that helps, when I installed virtual box, one of the last notes was "setting up host networking". Is that what's messing up NAT from working? It does that with both 1.56 and the 1.6 versions. Should I follow the instructions somewhere around here to set up host networking instead?

Edit: Finally got it working, had to setup bridge networking for it to work.

---

