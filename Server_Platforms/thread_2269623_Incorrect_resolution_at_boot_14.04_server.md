---
title: "Incorrect resolution at boot 14.04 server"
date: 2015-03-17
forum: Server Platforms
---

### Post by tmontney on 2015-03-17
Just installed Ubuntu 14.04 Server. Everything about the installation went fine until I had to reboot. As soon as POST finishes, I get a message saying video can't be displayed due to incorrect resolution. I don't see the boot loader or anything. I was connected to a 1024x768 monitor, so I switched to a 1280x1024 one with the same result. Nothing I've found has worked, and most results are for version 12 (usually desktop, not server).

Edit: Connected it to a monitor that supports up to 1920x1080, still no luck.

---

### Post by tmontney on 2015-03-17
I tried editing /etc/default/grub but that didn't work. I'm just going to reinstall with SSH. I don't really need local access anyway.

---

