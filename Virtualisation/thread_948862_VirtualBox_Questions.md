---
title: "VirtualBox Questions"
date: 2008-10-15
forum: Virtualisation
---

### Post by Shippou on 2008-10-15
Hello guys...

I would like to ask the following:
1. Is drag and drop possible in VirtualBox? (Host: Linux Mint, guest, Windows XP)
2. How do I install drivers (audio, video, etc.) in my XP guest OS? (The installer CD says that the motherboard is not supported, and refuses to install.)

Good day to all.

---

### Post by howefield on 2008-10-15
> **Shippou said:**
> 1. Is drag and drop possible in VirtualBox? (Host: Linux Mint, guest, Windows XP)

If you mean between host and guest, then no you cannot drag and drop. You can use shared folders between the two. 
> 2. How do I install drivers (audio, video, etc.) in my XP guest OS? (The installer CD says that the motherboard is not supported, and refuses to install.)The drivers are installed by Virtualbox, the guest doesn't have access to the hardware directly.

---

### Post by Shippou on 2008-10-16
Sorry for the late reply.

Do virtualbox install codecs and drivers by default? I can't hear XP boot sound, in the first place.

Also, how do I use shared folders? I do know there is a shared folder option in virtualbox, but I don't know how to use it correctly. (Sorry for being a noob at this. ;))

Thanks for helping.

---

### Post by Shippou on 2008-10-16
Fixed the audio. There are only two problems:

1. Shared Folders
2. Network.

Thanks for the help.

---

### Post by Shippou on 2008-10-18
Hello there.

Would someone kindly post a how-to on enabling network access on the guest OS? 

And also how to fix this error:
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

```

I found a guide at the internet, but it keeps frying my net connection in my host OS.

[http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/](http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/)

Host OS: Linux Mint
Guest OS: Windows XP SP3

---

