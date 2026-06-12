---
title: "Server internet dependancy"
date: 2009-03-17
forum: Server Platforms
---

### Post by kchakrak on 2009-03-17
I've had an issue with a couple of servers I have built regarding what seems to be a dependancy on the internet. 

Last night I rebooted a server with my router off (as part of an investigation into a different problem) but the server did not come back up correctly with the ubuntu splash screen just scrolling across the botttom. As soon as I rebooted it with the router on the server reboots as I would expect it to. This is the second time that has happened to me, anyone got any ideas why this would be?

OS: Ubuntu 8.04 LTS desktop 32bit edition.
Server runs as DC and DNS server with what appears to be dynamic DNS.

---

### Post by askreet on 2009-03-17
First of all, disable usplash so you can at least *see* what it's trying to do.  It's probably stuck trying to do some DNS checks, etc.

If you can boot into single user mode (recovery mode), edit /boot/grub/menu.lst and remove "splash" from the boot options.  You could also do this at boot-time by catching grub before it boots your kernel.

Once this is done you'll have a better idea what it's trying to do, hopefully.

---

### Post by kchakrak on 2009-03-18
> **askreet said:**
> First of all, disable usplash so you can at least *see* what it's trying to do.  It's probably stuck trying to do some DNS checks, etc.

If you can boot into single user mode (recovery mode), edit /boot/grub/menu.lst and remove "splash" from the boot options.  You could also do this at boot-time by catching grub before it boots your kernel.

Once this is done you'll have a better idea what it's trying to do, hopefully.

Brilliant, I have been wondering how to do that. Thanks for your advice. I'll do that, try and replicate it and have a look.

---

