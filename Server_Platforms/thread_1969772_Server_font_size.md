---
title: "Server font size"
date: 2012-04-30
forum: Server Platforms
---

### Post by jasonlyle88 on 2012-04-30
Hey guys, I am running server 12.04 and want to edit the font size displayed.  I've done the following:

[INDENT]dpkg-reconfigure console-setup[/INDENT]
[INDENT]update-initramfs -k all -u[/INDENT]
[INDENT]update-grub[/INDENT]

However, as soon as i reboot my system the font is back to the original size and i have to run setupcon again to get it back.  From what i understood, the reconfigure would change my initramfs so that it loaded with the new font I have selected.  Am I missing something?  What do I have to do so that when i boot up, the font size is what i have specified when running "dpkg-reconfigure console-setup"

Thanks!

---

### Post by d4m1r on 2012-04-30
Are you connecting through Putty, Terminal, or? It might be better just to change the font in what you are accessing the server with versus changing the font on the server itself.

---

### Post by jasonlyle88 on 2012-04-30
I will eventually be accessing via PuTTY, at which point I will configure the display via PuTTY, but for when I am working on the server directly, it would be nice to have this working so that the font size is set automatically.  It looked like there was a hook for initramfs to console-setup, so i dont understand why the font is not being set when the image is loaded from GRUB.

---

### Post by jasonlyle88 on 2012-05-05
Bump.  I'm noticiing 82 views but only the 1 response... I know this isn't that big of an issue, as I can just run setupcon and it is fine, but i'd like to understand it, and understand why the hook to console-setup inside initramfs isn't working as I expected it to

---

