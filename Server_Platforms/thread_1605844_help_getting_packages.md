---
title: "help getting packages"
date: 2010-10-25
forum: Server Platforms
---

### Post by Amdahl1 on 2010-10-25
I have created my first linux server using Ubuntu 10.04 server edition.
My only experience with linux has been the desktop edition.

The initial trouble I'm having is that this server is on an isolated network without Internet access. I'd like to use a Gnome desktop like I'm used to in order to get up to speed quickly.

How do I get additional packages for a system that is not on the Internet?

The end goal for this machine is a simple file depository for a W98 network using Samba shares. To boot from an IDE drive and share a 5 drive software RAID5 for data storage.

ANY tips would be most welcome!

---

### Post by arrrghhh on 2010-10-26
If you want Gnome, just install ubuntu-desktop.  There's no reason whatsoever to install the server edition if you want a DE (desktop environment).

As to your question, it's not easy... probably the easiest way would be to get the debs you need and install them manually with dpkg from a usb key or something.

---

### Post by hobatter on 2010-10-26
You ever consider a NAS server? OpenNAS  or Freenas? Might be a littel more practical for you.

---

### Post by Amdahl1 on 2010-10-27
Only reason for not using Ubuntu-Desktop is I want to do shared file storage to RAID5.

OpenNAS? I'm unfamiliar. need to do more reading...

---

### Post by arrrghhh on 2010-10-27
> **Amdahl1 said:**
> Only reason for not using Ubuntu-Desktop is I want to do shared file storage to RAID5.

OpenNAS? I'm unfamiliar. need to do more reading...

You can do the RAID setup with ubuntu-desktop, nothing should be holding you back there.

With that said, FreeNAS is a great solution if you just need it for storage.  No Gnome, but the web interface is pretty robust.

To that end, there's also several webUI's available for configuring Ubuntu server - webmin and ebox come to mind here.

---

