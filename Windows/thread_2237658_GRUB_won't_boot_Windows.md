---
title: "GRUB won't boot Windows"
date: 2014-08-03
forum: Windows
---

### Post by Gabriel_Taets on 2014-08-03
Hi to all! I'm new here so I might have posted this thread on the wrong section. If so, pardon me.
Some time ago, I've installed Mint, with dual boot with Win8. So far, so good.
But GRUB kinda gets on my nerves because it is really ugly naturally.
So I decided to customize it a little bit and installed a theme (Grau GRUB Theme: [http://gnome-look.org/content/show.php/Grau+GRUB+Theme?content=158610](http://gnome-look.org/content/show.php/Grau+GRUB+Theme?content=158610)). It got A LOT better in terms of elegance. Until then, I've never had a problem with booting. But oddly, after installing the Theme (I've tried installing it through GRUB customizer and through the Terminal), it won't boot Win 8 anymore (but still boots Mint). If I disable the theme through GRUB Customizer, GRUB boots Win 8 normally. Really odd!
I wonder if anyone could give me some help. GRUB without any customizing is really ugly, and I'd rather not give up on this theme that made the booting screen a lot cooler, hehe.

When I boot Win 8, it gets stuck on the screen I've attached. Linux Mint goes through this screen for about 2s and boots.

Thanks to all!

---

### Post by oldfred on 2014-08-03
Moved to otherOS since Mint & Windows 8.

Not sure what version of grub Mint uses. 
And do not know why a theme would make any difference as the chain load should be the same either way.

But grub customizer does add its own scripts to make changes and perhaps some issue with version?

Are you booting in UEFI or BIOS mode.
Attach link to BootInfo report, but it may not show details of customization. 

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

