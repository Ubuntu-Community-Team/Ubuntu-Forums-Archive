---
title: "Ubuntu Server - Scrambled Letters on cmdline"
date: 2012-02-11
forum: Server Platforms
---

### Post by zachnap on 2012-02-11
I just installed Ubuntu Server 11.10 32-bit on a PIII with integrated graphics. Everything installed but I did not setup a network yet. When I boot-up the GRUB screen is readable but when I select ubuntu server the screen becomes scrambled. The letters are there but they are reversed and doubled-over so it just looks like a mess. Is this a problem with my graphics driver or something else? I've read some threads that seemed similar to this problem discussing the frame buffers but not sure if this was actually the same problem. What can I do to attempt to remedy this? Thanks

---

### Post by zachnap on 2012-02-11
more info:

when i started the install i got a message: "undefined video mode: 314"

also,

it works fine in rescue mode.

edit:

i reinstalled and am getting a white and black-striped screen and then it hangs.

i rebooted and got a normal start-up screen but a hanging orange cursor in the upper left corner.

---

### Post by cabaro on 2012-02-13
This link might help
[https://wiki.edubuntu.org/FrameBuffer](https://wiki.edubuntu.org/FrameBuffer)

---

### Post by cabaro on 2012-02-13
Or try different videomodes 
[http://pierre.baudu.in/other/grub.vga.modes.html](http://pierre.baudu.in/other/grub.vga.modes.html)

Actually i think this might help.
When in grub menu, click e to edit and use a videomode from link above and click b to boot.

---

