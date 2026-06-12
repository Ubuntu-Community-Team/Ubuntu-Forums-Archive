---
title: "Only 8bit color hwinfo --framebuffer"
date: 2008-11-03
forum: Server Platforms
---

### Post by vuser1 on 2008-11-03
Hello all, 

I read ALL documentation and posts about enabling vesafb and using vga=... option. None helped. I run 8.04 in VMWare.

Last mouth I suddenly configured 8.04 server-virtual so that it boot with 1024x786 16bit console and X11. After some update and today reboot I see that fnkg "Unknown video mode" at boot.

hwinfo --framebuffer shows only 8-bit modes. But they also doesn't work, if I use vga=... option! It always says "Unknown" and force me to boot standard vga. 

X11 also run in 256 colors. 

Why it shows only 8-bit modes? Why they also don't work? Someone, please, help me. I have no idea what to do/read/etc/modprobe.d/blacklist/grub/so on...

---

### Post by Vegan on 2008-11-03
We don't use GUI's in the server area. We use console.

:guitar:

---

### Post by vuser1 on 2008-11-04
> **Vegan said:**
> We don't use GUI's in the server area. We use console.

:guitar:

Thank you for the most stupid answer I ever get. Did I ask what _you_ use? Is installation of X11 is prohibited on server or what?

Nevertheless, I also don't use GUI in server. I need BIG CONSOLE, but I can only get 25 lines VGA.

---

