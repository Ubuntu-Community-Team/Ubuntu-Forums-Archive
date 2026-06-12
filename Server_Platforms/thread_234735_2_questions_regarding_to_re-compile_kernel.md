---
title: "2 questions regarding to re-compile kernel"
date: 2006-08-11
forum: Server Platforms
---

### Post by shawn_ning on 2006-08-11
[SIZE="3"]Hi, guys, can you help on this issues?

since there is no compiler on the server and I don't want install them there, I compiled the kernel on another machine (ubuntu desktop). I followed the procedure to make the new kernel and end up with a new kernelxxx_customxxx.deb file. Then I copy the deb file back to the server and use dpkg to install it, It says no initrd-tools availble.

so question 1, [COLOR="Blue"]do I have to install initrd-tools on the server[/COLOR]? I mean, I want the server be as lean as possible. Can I mkinitrd on the desktop machine, copy the initrd.img manaully to the server, will it work? (please note that the ubuntu desktop is running under a diffirent kernel version). And When I run dpkg -i newkernel.deb on the server side, how I get around the mkinitrd part?

question 2, [COLOR="blue"]How I use the existing initrd.img as a template to make the new initrd[/COLOR]? I guess I can mount the old initrd.img and find out what modules are included and what linuxrc and init looks like, but is there a better way to do this?

Thanks a lot![/SIZE]

---

