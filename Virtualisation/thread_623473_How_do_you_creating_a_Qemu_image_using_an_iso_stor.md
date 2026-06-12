---
title: "How do you creating a Qemu image using an iso stored on the hard-drive?"
date: 2007-11-25
forum: Virtualisation
---

### Post by AndyCooll on 2007-11-25
The title really says it all.

May be I'm missing something obvious, but I ask because even though I can get a new Qemu image to boot up from the iso (e.g. an Ubuntu iso), when I get as far as detecting the hardware it then tells me that it can't find the CD-drive and won't let me go any further.

:cool:

---

### Post by AndyCooll on 2007-11-29
Has no-one ever created a Qemu image from an iso on their hard-drive??

:confused:

---

### Post by ruibernardo on 2007-11-29
Hi AndyCooll,

is this happening with all your isos? Ubuntu, windows, etc, with Gutsy host and the qemu package from the repositories? If it is check this: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368)

---

### Post by bodhi.zazen on 2007-11-29
What command are you using to start qemu ?

---

### Post by aysiu on 2007-11-29
Maybe I don't know enough about Qemu, but I've always found it a bit limiting. You might have more luck with VirtualBox.

That said, whenever I've used Qemu in the past, I haven't created an image... I've just used the .iso itself. For example, if it's on your desktop: ```
cd ~/Desktop
qemu -cdrom ubuntu-7.10-desktop-i386.iso
```

---

### Post by AndyCooll on 2007-11-30
Thanks for the replies guys. I'm at work at the moment, but I'll get back to you with a fuller reply later.

:cool:

---

### Post by AndyCooll on 2007-12-10
My apologies for not replying. In the end I got side-tracked, so haven't had a chance to revisit this.
 
epimeteo: I think it was just the Ubuntu iso's I was having problems with. I'll have a look at that bug report.

bodhi.zazen: I was creating an image and then attempting to install Ubuntu using the following commands:
```
qemu-img create -f qcow ubuntu.img 5G

qemu -localtime -cdrom /dev/cdrom -m 512 -boot d ubuntu.img
```
I also tried creating an image using Qemulator.

aysiu: Yeah, I have used VirtualBox and quite liked it. However at the time, I was looking for a fully open-source virtualisation app and the VirtualBox deb I'd downloaded from the website wasn't. Of course I hadn't realised that the repos now contain VirtualBox OSE!

Anyway, when I have the time maybe I'll come back to this ...now it's the challenge that keeps me interested!

:cool:

---

