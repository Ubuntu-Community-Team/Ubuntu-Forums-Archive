---
title: "cli mode screen resolution problem"
date: 2010-06-21
forum: Server Platforms
---

### Post by mchlor on 2010-06-21
Upon upgrading to 10.04 server, I've discovered an interesting feature.  It ups the resolution sky high, making the text extremely tiny and painful to read.

I've tried to lower the resolution by changing grub gfxmode800x600  in /etc/default/grub.cfg.  then doing update-grub. then rebooting but it's not working.

any help?

---

### Post by sjinks on 2010-06-21
hwinfo --framebuffer | grep 'Mode 0x'

Then add 'vga=hexadecimal_mode_number' (say, vga=0x0322) to the kernel command line and see if it helps.

---

### Post by sjinks on 2010-06-21
Or you can try adding vga=ask to the kernel's command line to see all available VESA modes.

---

