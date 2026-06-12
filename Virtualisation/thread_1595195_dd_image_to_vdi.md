---
title: "dd image to vdi"
date: 2010-10-13
forum: Virtualisation
---

### Post by r+9 on 2010-10-13
I understand this process is quite simple, so I'm stumped on how I'm stumped.

1. dd if=/dev/<hd_on_laptop> of=laptop.img

2. VBoxManage convertdd  laptop.img laptop.vdi

3. use virtualbox to load the image.

At step 3 I get a "deadbox" just a blank screen, I've been scouring google and just about every combination of search criteria that would uncover a step I'm missing, so I am turning to the community for help.

thanks.

---

### Post by r+9 on 2010-10-13
Apparently not a popular topic!

I was all excited to "save" my old computers in little virtual boxes, but I guess it's only me.

Nevertheless I'll post any advances/success I find

---

### Post by JKyleOKC on 2010-10-14
There's a six-year-old thread in the vbox forums that may (or may not) help you wend your way through this problem: [http://www.virtualbox.org/ticket/943](http://www.virtualbox.org/ticket/943) is the address. If your image failed to get the entire disk, that might explain why step 3 fails...

---

### Post by r+9 on 2010-10-31
Thanks, that helped me get smart on virtualbox commands.

It turns out if you dd a partition it's not really bootable if your MBR is some other place.

I made a dd of the entire disk, grub booted and I could load Ubuntu but the the windows part would hang on some file called mup.sys

googling the mup.sys this seems to be a common problem.

I've managed to talk the wife into getting a netbook, which will inevitably come with that "other OS" so I can keep that around for when I am forced to use that "other OS"

---

