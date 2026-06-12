---
title: "console resolution in server 11.10"
date: 2012-03-14
forum: Server Platforms
---

### Post by servern00b on 2012-03-14
Hi everyone, I just migrated my server from Debian Squeeze to Ubuntu server 11.10. I'm using a 15" rackmount console to controll it, that has a native resolution of 1024x768. It also has sort of a compatibility mode, so it does display input in 1280x1024. The Ubuntu installer obviously thought it to be a great idea to use the maximum available resolution but it really hurts my eyes to look at the microscopic font.

So the question is: How do I change the resolution?

What I tried so far without any success:

 - appendig (text) vga=X to the grub kernel command line
   X beeing some hex numbers as provided by vbeinfo and some decimal numbers I got off diverse forum posts on this topic. I also tried with and without the "text" option.

 - as grub told me, the vga=X parameter is deprecated and I was to use gfxpayload instead. I did this.
   I set gfxpayload and/or the GRUB_GFXMODE/GRUB_GFXPAYLOAD_LINUX to 1024x768, I also tried uncommenting the GRUB_TERMINAL=console line in /etc/default/grub to no avail. (of course I alwas update-grub2 after any changes and I tried it directly in grub). Also setting gfxpayload=text doesn't have any effect.

There is a rather troublesome looking description of a last way to do it at [http://ubuntuforums.org/showthread.php?t=1654503](http://ubuntuforums.org/showthread.php?t=1654503) that does not only involve the deprecated vga=X but also some blacklisted driver modules and rebuilding the initramfs. I didn't try that yet. But seriously, this is a very basic thing to change the screen resolution, it cannot be that complicated, can it? :(

As it is the server version, there is no X server or gui available and I intend to keep it that way.

I was also told, the type of my videocard may matter which I feel it should not, since the problem is not a too low resolution but a too high resolution, so I suppose the appropriate driver is loaded and working. It just needs to be told what to do. Anyways, the card's some integrated Intel thing identifying itself as "VGA compatible controller: Intel corporation 82945G/GZ Integrated Graphics Controller (rev 02)" in lspci.

Any further ideas?

---

### Post by lancet on 2012-04-21
Try the [Fix/Workaround] from this [http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/).  I did it on 11.10 desktop and it works beautifully.  I have an HP EliteBook 8560w with Nvidia Quadro 2000M graphics card.

---

