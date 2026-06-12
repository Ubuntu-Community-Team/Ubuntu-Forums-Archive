---
title: "USB flash instal"
date: 2007-04-04
forum: The Cafe
---

### Post by naknak987 on 2007-04-04
I want to get ubuntu on my computer to dual boot with winxp, but I dont have a working cd drive or floppy drive. I do however have a 1gig flashdrive and my bios does support booting from a usb flash. but I'm having trouble getting ubuntu to boot from the flash, it trys to boot, but it wont. Or is there a way to install ubuntu from windows xp to another hard drive? I don't care if its from a usb flash drive or from windows as long as it dual boots and installs on a hard drive. 

BTY I'm new. never used ubuntu before, and decided to give it a try. Also, I have messed with linux before, but not much.

---

### Post by naknak987 on 2007-04-05
*bump*

---

### Post by insane_alien on 2007-04-05
have you tried extracting the .iso to the USB drive. it MIGHT work. infact, i'll go try it.

okay, it didn't work.

---

### Post by naknak987 on 2007-04-05
Yes, I did. and that did not work for me, I will however try it again. just to see.

---

### Post by naknak987 on 2007-04-05
Well, I tried that again, and I got it to boot but it won't install ubuntu on my hard drive. It gave me some kind of disk access error.

---

### Post by Dual Cortex on 2007-04-05
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
Good luck

---

### Post by naknak987 on 2007-04-05
That wont work, I only have windows installed, and I need to boot the live cd from a flash drive to install on a hard drive.  Thanks any way.

---

### Post by Dual Cortex on 2007-04-05
Do you have any other flash drives?

---

### Post by naknak987 on 2007-04-05
waiting...

---

### Post by Dual Cortex on 2007-04-05
Do you have any other flash drives?
You might try installing DSL
[http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/](http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/)
Then
[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)
hehe

now, REALLY, good luck.

---

### Post by naknak987 on 2007-04-05
I have one other one, but its not at my house at the moment. Its 1 gig also and I'm getting it back later tonight.

---

### Post by Dual Cortex on 2007-04-05
> **Dual Cortex said:**
> Do you have any other flash drives?
You might try installing DSL
[http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/](http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl/)
Then
[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)
hehe

now, REALLY, good luck.

Just posting that again in case you didn't notice.
...*I shouldn't keep editing my posts*

---

### Post by naknak987 on 2007-04-05
I will try that. thanks

---

### Post by naknak987 on 2007-04-05
When I click on makeboot.exe it tells me...  

to run this application, you first must install one of the following versions of the .net framework:
v2.0.50727
contact your application publisher for instructions about obtaining the appropiate version of the .net framework.

I don't know what that means


Edit: never mind. I found what i need

---

### Post by naknak987 on 2007-04-05
Ok, I got DSL working, but I have two problems with it.
#1. It does not recognizes either of my network cards. (I have two of different  make and model.)
#2. How do I use it to install ubuntu on my hard drive.

---

### Post by Dual Cortex on 2007-04-05
> **naknak987 said:**
> Ok, I got DSL working, but I have two problems with it.
#1. It does not recognizes either of my network cards. (I have two of different  make and model.)
Doesn't really matter for installation.... just copy down/print the instructions or something.

#2. How do I use it to install ubuntu on my hard drive.[/QUOTE]
:| That's what the 2nd link was for.
Good luck.
[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

### Post by naknak987 on 2007-04-05
thanks

---

### Post by naknak987 on 2007-04-05
Man, I just cant get this to work. Is there a easer way to install with out having to use a cd? Maybe it would help if I knew half of what it was talking about.
RRRRRRRRRRRR......  I'm about to rip out my hair. :(  Please help.

---

### Post by andb on 2007-04-06
While I prefer Ubuntu, I've installed debian on a few machines when booting from a cd wasnt possible. 

I found this site about booting from a usb key: [http://d-i.pascal.at/](http://d-i.pascal.at/) Worst think about this way is that you need access to a linux box to set it up :( Maybe you know someone with linux or can you find someone near you by using the cafe section who can help? 

A small note, I saw a howto on Damn small linux on how to install it from windows on a usb key, there may be some overlap that you could use. DSL is really good and easy to put on a usb key.

Ive done the 3 floppy disk boot, wihch then pulls everything over the net.

Sorry I cant give you a clear answer how to do this, but hopefully these comments will point you in the right direction...

---

### Post by Dual Cortex on 2007-04-06
That's what I told him to do. Install DSL on a flash drive to install Ubuntu on a flash drive. A rather insteresting project.

> **naknak987 said:**
> Man, I just cant get this to work. Is there a easer way to install with out having to use a cd? Maybe it would help if I knew half of what it was talking about.
RRRRRRRRRRRR......  I'm about to rip out my hair. :(  Please help.

What don't you understand?


**EDIT**: Just went over the instructions. At the end you need to install syslinux and mtools... don't know of any packages of them compatible with DSL. You might try installling PCLinuxOS instead ([http://www.pendrivelinux.com/2006/09/19/all-in-one-usb-pclinuxos-minimezip/](http://www.pendrivelinux.com/2006/09/19/all-in-one-usb-pclinuxos-minimezip/)) since those seem to be available for it.

---

### Post by naknak987 on 2007-04-07
Um. One problem, I can't download anything to DSL because it wont let me connect to the net.
And I want to install ubuntu on my hard drive, not my flash drive, but I cant use a cd to do it, seeing as how I have one at the moment, so I want to install ubuntu on my hard drive from flash. I would try a net boot but I started reading how and got lost...  LOL. thanks for trying to help tho.

---

