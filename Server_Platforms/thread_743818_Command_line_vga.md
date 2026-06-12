---
title: "Command line vga"
date: 2008-04-03
forum: Server Platforms
---

### Post by pokerface on 2008-04-03
I did some searching on Google and on linux related forums but I was not able to find an answer. I have a Ubuntu-Server 7.10 running as a web, samba, files, video server. This server has its own monitor and keyboard attached. The problem lies with the vga settings. I try to set it to a higher resolution but it keeps failing. Just turns blank. I have an ati video card on it and i though maybe its the drivers. So my question is how do i install the ati drivers for my card?

I have installed ati and nvidia drivers before but the difference here is i dont have X installed nor do i want to install it. is  there some CLi version of this driver or something? 

Thanks in advance.. your help is appreciated.

ps... I know this question is very 'n00b'

---

### Post by netlogic on 2008-04-03
i am not very clear about your question. i am going to assume you want 1024x800 resolution on your console.

you want to append this statement in your kernel line in your grub.
```
vga=791
```

---

### Post by pokerface on 2008-04-03
thanks netlogic.
see thats the problem. i did it and my monitor just went blank and wouldn't respond. the only way to access it was with ssh. 
Now i dont know if my monitor just cant support that resolution but thats highly doubtful because its capable of 1600x1200. Could their be another factor playing a role here?

---

### Post by koenn on 2008-04-03
a normal console is not defined by a resolytion in pixels, but by colums and rows of characters, usually 80x25, sometimes 80x >25 (with smaller fonts).

You can do a graphical display without X by using the framebuffer.
[http://tldp.org/HOWTO/Framebuffer-HOWTO.html](http://tldp.org/HOWTO/Framebuffer-HOWTO.html)

Then there's also this:
[http://tldp.org/HOWTO/Framebuffer-HOWTO.html](http://tldp.org/HOWTO/Framebuffer-HOWTO.html)

and the quick/dirty trial/error approach : add vga=ask
to your boot line in hrub menu : you'll be prompted for a choice of vga options, so you can try and see which ones work.

---

