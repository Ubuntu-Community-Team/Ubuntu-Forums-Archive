---
title: "Is Vista VirtualBox Friendly?"
date: 2007-11-09
forum: Virtualisation
---

### Post by Zipster90 on 2007-11-09
I'm currently running XP on VirtualBox with no problems whatsoever, but I'm just wondering if Vista would work just as well.

I already have a Vista Home Premium disc that came with my Dell laptop, and I was just wondering if it works at all. If it does, how much RAM and video memory should I allot to it? Any other special settings Vista needs? Thanks in advance.

---

### Post by Ctrl+Alt+Del on 2007-11-15
It won't run well... I haven't tried it myself but afaik Virtual Box has no 3D Support, meaning you will have to disable Aero for decent performance. As to how much RAM: LOTS. I found Vista to be somewhat sluggish when running with 1GB RAM or less

---

### Post by Rhubarb on 2007-11-15
Vista (ultimate) runs fine in virtual box, if you read the fine print on your vista home premium you'll notice that you are not allowed to run any vista home based operating systems in a virtual machine, you can only legally run vista business and ultimate in a virtual machine.

And yeah, vista (in virtual box) does not have any 3D acceleration, so no fancy (well it's not really fancy compared to compiz fusion) aero gui will work.
Please note that some programs require a 3D acceleration in vista - like home DVD maker, windows media player.
Make sure you've got plenty of RAM to donate to Vista's VM too (I would recommend 1GB).

---

### Post by vidmantas on 2009-08-10
i experiencing problem with network. real os - vista home premium sp1, guest ubuntu 9,04

from ubuntu ping 10.0.2.2 (real os ip) 100% successful 
from ubuntu ping any real ip - packet loss ~95%

virtual box 3.0.2 and 3.0.4 tested

---

### Post by jocampo on 2009-08-10
> **vidmantas said:**
> i experiencing problem with network. real os - vista home premium sp1, guest ubuntu 9,04

from ubuntu ping 10.0.2.2 (real os ip) 100% successful 
from ubuntu ping any real ip - packet loss ~95%

virtual box 3.0.2 and 3.0.4 tested

when you say from Ubuntu, you mean .... from your Guest or from your Host? For labs and decent performance I usually recommend Bridged network (looks like you are using NAT) Bridged network will give the Guest a real private IP address (with NAT, not, you're sharing the host one) so you can communicate and exchange packets with your Host and future VMs. Sun says the performance is a bit better on Bridged network when compare with NAT.

---

### Post by Orfintain on 2010-09-21
I bought windows vista as a student when I was in college and now I'm trying to virtual it with Virtual Box OSE, on my Dell Inspirion  N series. I can't seam to get it to connect to the internet. I tried installing guest additions. Is it even possible to do this ? What version if windows would I have to buy/use to function well in a virtual environment?

---

### Post by manzdagratiano on 2010-09-26
You can try installing Vista on QEMU. I do not know how Vista would behave per se, but I currently have seven GNU/Linux virtual machines and none gave me any trouble with network - they see my wireless as an ethernet connection, and it works right out of the box. VIsta should see it as ethernet too.

---

