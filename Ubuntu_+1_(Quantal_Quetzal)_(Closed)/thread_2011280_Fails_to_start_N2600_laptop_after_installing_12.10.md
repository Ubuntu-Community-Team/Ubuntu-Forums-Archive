---
title: "Fails to start N2600 laptop after installing 12.10"
date: 2012-06-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Jollibee on 2012-06-26
Downloaded the first version of the 12.10 via Bittorrent. Installed but fails to start or load.

Also, during installation, mostly only when I touch the touchpad does the progress bar advances.

But, I can still load Windows 7 Starter that I use to login to Ubuntu fora.

I got an uncommon hardware, I should say, because this one is not a popular brand of netbook. I got NEO, a Philippine-based laptop-assembling company. All of their laptops are sold in the Philippines. Well, the parts are made in Taiwan or perhaps from mainland china. So NEO merely assembles.

I think this issue has something to do with the motherboard?

Would you want the messages that 12.10 says when it fails to start?

Also, I'm not proficient in computing. So you may want to adjust that way you convey instructions.

Thanks for your time.

---

### Post by Mark Phelps on 2012-06-27
It's an ALPHA -- meaning it's not intended for general use.  Some features will be missing, others won't work, and crashes are quite likely.

If you want support for ALPHA versions, post you questions in the appropriate Development forum, not here.

---

### Post by Elfy on 2012-06-27
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by balloons on 2012-06-27
> **Jollibee said:**
> Downloaded the first version of the 12.10 via Bittorrent. Installed but fails to start or load.

Also, during installation, mostly only when I touch the touchpad does the progress bar advances.

But, I can still load Windows 7 Starter that I use to login to Ubuntu fora.

I got an uncommon hardware, I should say, because this one is not a popular brand of netbook. I got NEO, a Philippine-based laptop-assembling company. All of their laptops are sold in the Philippines. Well, the parts are made in Taiwan or perhaps from mainland china. So NEO merely assembles.

I think this issue has something to do with the motherboard?

Would you want the messages that 12.10 says when it fails to start?

Also, I'm not proficient in computing. So you may want to adjust that way you convey instructions.

Thanks for your time.

You are going to have to give us a little more info about what messages your seeing, and what you mean by fails to start. I've no doubt we can get you up and running on the bleeding edge. However, as mentioned development versions will break.

If you need something stable, please download and run 12.04.

---

### Post by Jollibee on 2012-06-28
> **Mark Phelps said:**
> It's an ALPHA -- meaning it's not intended for general use.  Some features will be missing, others won't work, and crashes are quite likely.

If you want support for ALPHA versions, post you questions in the appropriate Development forum, not here.

The thing is that even 12.04 fails.

---

### Post by Jollibee on 2012-06-28
> **guitara said:**
> You are going to have to give us a little more info about what messages your seeing, and what you mean by fails to start. I've no doubt we can get you up and running on the bleeding edge. However, as mentioned development versions will break.

If you need something stable, please download and run 12.04.

Right. I realized that the title is wrong. It should be *12.10 fails to load itself after installing onto N2600 laptop*.

Even 12.04 fails so I tried 12.10 for the newer kernel.

I'll tell about the messages shortly after.

---

### Post by Jollibee on 2012-07-01
So here are the messages that I read. When the optical mouse is connected, for a long wait, it is a black background with a white flashing cursor like an underscore. Then, followed by many messages about the USB optical mouse.

So I removed the mouse and restarted my pc. So, the outcome was a shorter wait for the black background with the following.

udevd [131]: timeout killing '/sbin/blkid -o udev -p /dev/sda6' [225]
udevd [125]: timeout killing '/sbin/blkid -o udev -p /dev/sda2' [223]
udevd [123]: timeout killing '/sbin/blkid -o udev -p /dev/sda1' [224]

udevd[12 ]: '/sbin/blkid -o udev -p /dev/sda2' [223] terminate by signal 9 (Killed)

... and several similar messages, blah blah blah.

 Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay = (did the system wait long enough?)
  - Check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/7c858db3-5675-4379-9967-1046c6f939b7 does not exist.
Dropping to shell!
BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash)

Enter 'help' for a list of built-in commands (initramfs)_


I got no telephone with camera so I wrote the messages instead.

Anyway, 12.10 Alpha 2 is ready. I'm currently getting it at 10 kB/s. Internet connection is slow here.

---

### Post by Jollibee on 2012-07-12
Any responses for this, people?

---

### Post by dino99 on 2012-07-12
you might need some additional boot option

google around "ubuntu boot option"

and first try booting by adding nomodeset or noacpi

---

### Post by Jollibee on 2012-07-12
> **dino99 said:**
> you might need some additional boot option

google around "ubuntu boot option"

and first try booting by adding nomodeset or noacpi

I will rather use Startpage or DuckDuckGo.

---

### Post by jerrylamos on 2012-07-13
When the grub boot menu appears, press "e" then at the end of the line starting with "linux" and add:
nomodeset
then do 
Ctrl-x

What's going on, is during boot Ubuntu is setting the screen from "text"
 to "graphics" then later on when 'X" graphics starts the modes may be incompatible.

This used to affect a lot of graphics cards.  During development it may show up.

Now if your configuration doesn't run 12.04 it is not likely to run 12.10 which is in development and can/does have some bugs and not likely to settle down until it is released to general distribution in October.

You can try 10.04 Long Term Support Lucid Lynx to see if you can run Ubuntu at all.  10.04 was supposed to be supported for 3 years may be up by now.  

Jerry

---

