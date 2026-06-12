---
title: "Help Want to Dual Boot my Windows 8 tablet PC with a linux distribution"
date: 2015-03-30
forum: Ubuntu, Linux and OS Chat
---

### Post by josh122 on 2015-03-30
Hello Guyz 
I would like to dual boot my tablet PC which has Windows 8.1 with ubuntu or CentOS.
Heres my tablet Specs: [http://imgur.com/TCichOG](http://imgur.com/TCichOG)
Please do tell me if i can dual boot Windows 8 and Linux with this specs
if yes how do I do it and which linux distribution will also support touch in my tablet pc
Warm Regards,
Josh

---

### Post by Bucky Ball on 2015-03-30
With 1Gb of RAM and that dinky processor, Ubuntu won't be very satisfactory (if you can get it to run, that is). Try Lubuntu or perhaps Xubuntu. They are lighter and, particularly with Lubuntu, you have more chance of a successful install.

As for how you would install, please post a new thread in a support area of the forums regarding that (***Installation & Upgrades***) as this area is not for support requests.

Good luck. ;)

---

### Post by grahammechanical on 2015-03-30
That machine has 32 bit Windows on a 64 bit CPU and that could mean trouble if the UEFI code is also 32 bit wide. Ubuntu uses EFI code that is 64 bit wide.

> 
[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"). This is a problem if 32-bit EFI is the only way your computer can boot, e.g. if you have a modern Intel Atom based laptop. In this case, you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It seems that you will need to compile 32 bit EFI  code yourself.

[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555)

Many of the comments in that bug report are by people who think that fixing must surely be easy. Read what on prominent RedHat engineer said about it.

[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

Regards.[/FONT]
[/LIST]

---

