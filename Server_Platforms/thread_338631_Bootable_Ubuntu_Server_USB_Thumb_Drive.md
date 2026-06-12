---
title: "Bootable Ubuntu Server USB Thumb Drive"
date: 2007-01-14
forum: Server Platforms
---

### Post by SuperMike on 2007-01-14
This request is about how do I create a bootable USB Thumb Drive with Ubuntu Server on it?

I'm thinking of releasing some PHP/PostgreSQL software as free and open source. However, I want users to consider purchasing a USB thumb drive from me and booting up from it so that they could try it out without having to learn Linux or the few steps necessary to configure it. These users might be unaware of how to use Linux and might be just a business analyst trying to make product decisions for a company. (Of course, I could make some slight extra pocket change on the ol' thumb drives, tee hee.)

The Ubuntu Server needs the following features, so if you have an idea how small of a memory stick I could use, let me know.

* PHP5
* Apache2 Web Server
* OpenSSH Server (sshd)
* Standard GNU/Linux tools -- tr, cat, vi, pspell, du, df, cp, mv, rm, mkdir, mount, etc.
* Iptables script
* apt tools
* 'ne' text editor
* dhcp client

It does not need a GUI whatsoever -- could boot up straight to console login.

---

### Post by jd65pl on 2007-01-14
I'm not sure how willing someone would be to use linux CLI when they wouldn't have to learn any linux?!?! would probably require some sort of gui for this type of user to try.

---

### Post by SuperMike on 2007-01-14
Oh, they won't have to do CLI. They just boot up on it and it sits there at a login screen and identifies on the screen what it's IP address is currently set at as a DHCP client. Then, they connect on a separate PC in their office to the website on this IP address and go to town using this web app, trying it out, evaluating it, seeing if it's the one they want.

Anyway, it took me a good while, but I think I found the article that will help me best:

[http://www.ubuntuforums.org/showthread.php?t=308027&highlight=install+external+drive](http://www.ubuntuforums.org/showthread.php?t=308027&highlight=install+external+drive)

I also see he recommends a 20GB partition, but I think it could be had for 4GB. I have a fairly healthy workstation with several bells and whistles and I put my /HOME partition into a separate partition than root (/) partition. My workstation shows I only consume 3GB. Therefore, it's likely that one could initially build this thing on 4GB and even shrink it down with a series of 'apt-get --purge remove x' to remove all the x's one doesn't want on the system.

---

### Post by msgyrd on 2007-01-15
I don't know much about this personally, but I've seen projects with similar functions. Check out [http://www.vmware.com/vmtn/appliances/directory/520](http://www.vmware.com/vmtn/appliances/directory/520)  It's a VMware image, but it does exactly what you're talking about (boots to a CLI, displays it's current IP and is accessible without logging in).  You could dissect it and see what they did to make it work.  It's pretty small and should fit on a 1 or 2 gb drive.

---

