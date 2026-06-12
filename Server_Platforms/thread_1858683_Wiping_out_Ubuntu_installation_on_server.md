---
title: "Wiping out Ubuntu installation on server"
date: 2011-10-12
forum: Server Platforms
---

### Post by Lakeside5 on 2011-10-12
I have a big rack mount style server that a friend had custom built, it has 4 hard drives and raid installed. If you need any more specs just ask and I can tell you.  I have had wamp and lamp intalled on an old desktop before, to learn but that is as far as my knowledge goes. I paid a local tech shop quite a lot to try and get vm-ware and ubuntu OS installed, but this server seemed to reject it, it never would work. Then someone else tried, for free (he maintains servers for a big company here, so knows what he is doing.)Still didn't work and I don't know why, and the company  that built it won't take responsibility for that, they said some machines aren't meant to run linux???  So, I tried to load a trial verson of Windows Server 2008 available for download. I put it on a USB stick and the machine boots from the usb but even that didnt' work. I thought it would overwrite the Ubuntu, and load the windows.  It just brings up the purple ubuntu screenn still (10.10) then goes to the screen with the cursor and code, basically saying that it  can't load the root or whatever.  My friend says I need to do this, in order to wipe things clean and load windows, but I don't know how to do it:  "  ,  if you know how to delete the Master Boot Record from your Ubuntu installation.  That should reset it so windows will install and load normally.  Im actually surprised that windows 2008 sees the hard drives and does the installation considering how weird your RAID controller is."  Does anyone know how I would do this?  Thanks in advance!

---

### Post by kevinthecomputerguy on 2011-10-12
You could try Proxmox. Download their VE iso and give it a try.
Burn it, boot off of it, install, then manage it over a webpage.

[http://proxmox.com/products/proxmox-ve](http://proxmox.com/products/proxmox-ve)

---

