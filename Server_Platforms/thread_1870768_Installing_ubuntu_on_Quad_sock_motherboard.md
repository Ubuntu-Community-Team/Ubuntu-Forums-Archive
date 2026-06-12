---
title: "Installing ubuntu on Quad sock motherboard"
date: 2011-10-27
forum: Server Platforms
---

### Post by ebiru on 2011-10-27
Hello, I am trying to install Ubuntu(or anything really) on a TYAN S8812WGM3NR MEB Server Motherboard Quad Socket G34 AMD SR5690 DDR3 1333 but every time I install from an usb, it either black screens or freezes at gs_change+0x13. I have tried Ubuntu, sever, fedora.

---

### Post by ebiru on 2011-10-28
Update!!
Ok, I was able to get it to boot using the long term support 10.04 ver! The problem now is that it will not go past step 3 of 7.

---

### Post by ebiru on 2011-10-30
Update: Was able to install via cd. 

ps
I am surprise no one can help in this...

---

### Post by headvampyre@hotmail.co.uk on 2011-10-31
Does Ubuntu support the chipset being used?
Looking at this:

[https://lkml.org/lkml/2011/4/14/707](https://lkml.org/lkml/2011/4/14/707)

It could possibly be the disks you are using. You should check for backplane support (If you have one).

---

### Post by Zeon100 on 2011-12-30
I had the same problem with A supermicro quad socket opteron g34 server. I've been trying to install server11.10 AMD64 all night. After getting past the blank screen by disabling frame buffers (change vga=711 in the advanced boot options line).

However I just got stuck at gs_change too. I did manage to install the alternate installer 10.04 i386 alternate and use do-release-upgrade to upgrade to the new version.

Maybe the chipset isn't supported?

---

### Post by Vegan on 2011-12-30
check with linux.org and see if the chipset is supported

---

### Post by TwiceOver on 2011-12-30
I've never had good luck with the USB install method.  Always use the CD.

---

### Post by Zeon100 on 2012-01-01
OK I've spent ALL day again on this and finally have found a way to get what I want. It starts with installing the 10.04 LTS AMD64 ISO which installed great. I then upgraded to 10.10 which also wnet painlessly.

Then from 10.10 I upgraded to 11.04. This is where the troubles begin. After upgrading I got a black screen on boot (after GRUB) and when trying to use recovery mode it froze after "loading ramdisk". But the good news was it had the kernels there still from 10.04/10.10 so I could choose those and it worked great. Upgraded from 11.04 to 11.10 hoping the new kernel would work but same problem.

Now I'm just using the old 10.10 kernel but with 11.10 and it works fine. I think there must be something wrong with the kernels from 11.04 onwards that causes issues with this chipset?

It seems that it can't load the initial boot initrd of the newer kernels?

---

### Post by -alias- on 2012-02-26
> **ebiru said:**
> Hello, I am trying to install Ubuntu(or anything really) on a TYAN S8812WGM3NR MEB Server Motherboard Quad Socket G34 AMD SR5690 DDR3 1333 but every time I install from an usb, it either black screens or freezes at gs_change+0x13. I have tried Ubuntu, sever, fedora.

Hey, it's been a while since you asked, but I have the same quad socket motherboard from Tyan,  S8812 and I have installed Ubuntu 11.10 64bit from a USB stick with no problems. If the answer is still relevant and you want the solution you give me just an answer on this?

---

