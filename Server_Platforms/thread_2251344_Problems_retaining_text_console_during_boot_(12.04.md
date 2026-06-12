---
title: "Problems retaining text console during boot (12.04.5)"
date: 2014-11-03
forum: Server Platforms
---

### Post by Jonathan L on 2014-11-03
Hi All

As part of some standardisation I"m doing, I'm trying to get Ubuntu Server 12.04.5 LTS to boot and stay in pure text mode, without the framebuffer and soft fonts.

I've achieved the GRUB menu in pure text 80x25 in what I would call 'BIOS font', but as the kernel boots, it changes the font without changing the screen contents

/etc/default/grub
GRUB_TERMINAL=console
GRUB_GFXPAYLOAD_LINUX=keep

Most documents I've seen say you need kernel parameters nomodeset but it appears to have no effect.  I have tried many experiments and every GRUB_TERMINAL=text, nofb and vga=magic I've ever seen, in /etc/default/grub (yes, remembering update-grub) and grub boot lines, without luck.

First image is Grub in 'proper text' mode, followed by the early part of the boot in proper text, followed by what it changes to.  It's the last step I'm trying to change.  (Just to clarify, the second one is a fraction of a second later than the first.  The photos were actually taken on separate boots.)

[ATTACH=CONFIG]257725[/ATTACH][ATTACH=CONFIG]257726[/ATTACH]

Anybody got a method to make this happen?

My thanks for any help or suggestions.

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2014-11-05
Posting my solution in case it helps anyone else.

It turns out that the system *is* in pure text mode; what's happening is the font file /etc/console-setup/Uni2-Fixed16.psf is being loaded by setupcons.  This is a 512-glyph font with Unicode encoding, representing Latin, Cyrillic, line-drawing and other characters, and is used to configure the VGA character generators.

If you delete/rename/configure out this file, the 'font change/dimming' effect doesn't happen, but there will be some impairment in the display of non-ASCII characters, depending on locales.   I'm guessing you'll have a different font installed depending on the answers to the locale questions during installation -- my systems are in en_GB.UTF-8.

Documentation on the font and what's going on is in /usr/share/doc/console-setup/README*; good description of the VGA's two 256-character set generators and consequences in Wikipedia [http://en.wikipedia.org/wiki/VGA-compatible_text_mode](http://en.wikipedia.org/wiki/VGA-compatible_text_mode) and [http://www.osdever.net/FreeVGA/vga/vgatext.htm](http://www.osdever.net/FreeVGA/vga/vgatext.htm)

Hope it's useful to someone.

Jonathan.

---

