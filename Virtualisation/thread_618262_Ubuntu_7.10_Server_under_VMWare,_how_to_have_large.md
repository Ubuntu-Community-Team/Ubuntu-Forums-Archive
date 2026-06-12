---
title: "Ubuntu 7.10 Server under VMWare, how to have larger but 80x25 terminal?"
date: 2007-11-20
forum: Virtualisation
---

### Post by Merry Prankster on 2007-11-20
Hi!

I have Ubuntu 7.10 running VMWare, in which I have Ubuntu 7.10 Server edition running in a virtual machine. Everything works ok. However, I'm having trouble understanding how to change terminal "resolution". Please note, no X-windows here!

I'm currently stuck with 80x25. If I enable vga=ask in GRUB, I get to select from couple of really bad choices :D i.e. 80x50 is the "best" I get. I'd really like to have wide terminal, more than 25 rows would be fine, too. And with 'vga=ask', font will change depending on selection - I'd rather just have VMWare window resize depending on terminal configuration, i.e. grow/shrink the resolution used, not fonts.

I don't know if my question even makes sense but..in a setup mentioned above, how do I enable for instance 132 columns by 25 rows "terminal"? I guess this needs some framebuffer trickery, but I'm totally lost where to start looking :/ 

Any help/pointers appreciated!

---

### Post by jfsylvain on 2007-11-21
```
vga=0x303          (for 800 x 600)
vga=0x305          (for 1024 x 768)
vga=0x307          (for 1280 x 1024)
```

see: [_Kernel Framebuffer Doc_]("http://www.mjmwired.net/kernel/Documentation/fb/vesafb.txt")

---

### Post by Merry Prankster on 2007-11-22
Hi,

and thanks for trying. I forgot to mention I have tried this (and some other values, too, to see if color depth makes a difference). However, it seems  that screen resolution _is_ changed as VMWare window resizes depending on the value but otherwise I just get black screen, i.e. no text at all. So in practice this doesn't work for me :/

As everything I get is just black screen, I don't even know if this could be actual solution - does this change column/row properties of the terminal (I assume that it doesn't)?

---

### Post by jfsylvain on 2007-11-22
Columns and rows change, font stays constant:

[INDENT]0x301 = 80 columns x 30 lines
0x303 = 100 columns x 37 lines
0x305 = 128 columns x 48 lines[/INDENT]

I went back and checked my vms.  The vga parameter works with dapper and feisty virtual machines.  If I try to set vga on gutsy, the window changes to the right size, but stays black.

---

### Post by scorp123 on 2007-11-22
> **jfsylvain said:**
> Columns and rows change, font stays constant:

[INDENT]0x301 = 80 columns x 30 lines
0x303 = 100 columns x 37 lines
0x305 = 128 columns x 48 lines[/INDENT]

I went back and checked my vms.  The vga parameter works with dapper and feisty virtual machines.  If I try to set vga on gutsy, the window changes to the right size, but stays black. Framebuffers are disabled per default in "Gutsy". So "out of the box" you can't have higher text resolutions than the 1970-ish 80x25.

You can re-enable it ... See my other posting here:
[http://ubuntuforums.org/showpost.php?p=3784922&postcount=2](http://ubuntuforums.org/showpost.php?p=3784922&postcount=2)

---

### Post by Merry Prankster on 2007-11-23
> **scorp123 said:**
> Framebuffers are disabled per default in "Gutsy". So "out of the box" you can't have higher text resolutions than the 1970-ish 80x25.

You can re-enable it ... See my other posting here:
[http://ubuntuforums.org/showpost.php?p=3784922&postcount=2](http://ubuntuforums.org/showpost.php?p=3784922&postcount=2)

Ok, this is most likely cause then :) I followed the instructions as per first link found in your posting. Second one didn't seem to apply to me as I don't have /etc/usplash.conf (and I'm not really looking for splash screen here :D). I still get just black screen (although window does resize according to vga-parameter).

---

### Post by jfsylvain on 2007-11-23
> **Merry Prankster said:**
> Ok, this is most likely cause then :) I followed the instructions as per first link found in your posting. Second one didn't seem to apply to me as I don't have /etc/usplash.conf (and I'm not really looking for splash screen here :D). I still get just black screen (although window does resize according to vga-parameter).

Try running 'sudo update-initramfs -u' *after* modifying the blacklist file (that was the only way I could get it to work).

---

### Post by Merry Prankster on 2007-11-26
> **jfsylvain said:**
> Try running 'sudo update-initramfs -u' *after* modifying the blacklist file (that was the only way I could get it to work).

Great tip - that did it! Thank you very, very much =D>

---

