---
title: "Ubuntu Server - Resolution too low"
date: 2008-06-25
forum: Server Platforms
---

### Post by robgolding63 on 2008-06-25
Hi,

I am playing around with a new install of Ubuntu Server 8.04, on my existing Windows Server box - I am looking to migrate when I get these little issues ironed out.

Mainly, the resolution is too low when using X Server. I need X and gnome, as it is a VMware server - so I need access to the Vmware console. Unfortunately I cannot see the Cancel and OK buttons, as the resolution is stuck on 800x600. The server has a Rage 128 card, but I have tried a completely different card with no luck at all.

I have added the depths 8, 16, and 24 to the xorg.conf, and set defaultdepth to 16, with 1024x768 in the modes of each - but have had no luck.

Using dpkg-reconfigure xserver-xorg just asks questions about the keyboard, nothing to do with monitor/resolution, so that's no help. I installed the server O/S, then ran:

```

sudo apt-get install gnome-core xorg ubuntu-artwork gnome-system-monitor

```

To get a basic GUI. Is there anything else I can install to get a higher resolution. Obviously I'm not concerned with Direct rendering or anything like that - I don't really need Compiz on the server!

Thanks,

Rob

---

### Post by Titan8990 on 2008-06-26
I think that you may not have got all the dependencies needed for the gnome desktop. If you do:

#apt-get install ubuntu-desktop

It will grab everything you need.

---

### Post by hyper_ch on 2008-06-27
why do you want to add a gui on a server???

---

### Post by robgolding63 on 2008-06-27
As I said, it's for the VMware Server Console. That's all I need it for - and that's the only reason the low resolution is a problem. I can't see the damn OK/Cancel buttons as it's so low - so I have to guess with the keyboard.

**Titan8990**, thanks for the suggestion and I believe that would work - but I don't want the entire desktop on my server. So far I just have gnome-core, xorg, and the artwork to make it look like Ubuntu.

Rob

---

### Post by Titan8990 on 2008-06-27
Install it, see if it works then uninstall it. This way if it works then you are able confirm that there are packages that you are missing in order for it to function properly.

---

