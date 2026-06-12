---
title: "Headless Ubuntu Server?"
date: 2010-08-13
forum: Server Platforms
---

### Post by Ldoogy on 2010-08-13
I have a working Ubuntu 10.4 server setup, that is functioning as a file server. I am trying to use it in a completely headless setup (managed using SSH), but it just isn't working out. 

Every once in a while, it won't boot due to some on-screen bootup question or another. One time it's the boot loader asking me if I want a safe boot because the system wasn't shutdown properly, another time it's some RAID device (not the boot drive) thats offline. This is very annoying because it forces me to hook up a screen and keyboard, which is hugely inconvenient,

My question is: Isnt there a single configuration setting that makes the system more headless friendly?

Any advice would be greatly appreciated.

Thanks!
Ldoogy.

---

### Post by arrrghhh on 2010-08-13
Unfortunately if you have errors on boot, you're going to have to resolve them.

I just keep my server up all the time... But I've only had one or two times where I've had an issue from reboot.

Solve those problems, and you'll be good.

---

### Post by cj.surrusco on 2010-08-13
The only real way to avoid those problems is to keep it running all the time. There really isn't any way to monitor it during boot except maybe getting a monitor switch.

---

### Post by arrrghhh on 2010-08-13
Or some sort of a remote access controller like Dell has....

---

### Post by CharlesA on 2010-08-13
> **arrrghhh said:**
> Or some sort of a remote access controller like Dell has....
That might work too, but I don't know how practical it is.

I have a dual-input monitor hooked up to my server, but the machine machine that uses it is another desktop.

That way if I have problems, I just need to hook up a keyboard (gogo usb) and switch the input to the server and I can see what's going on.

---

### Post by arrrghhh on 2010-08-13
Agreed, not very practical.  Just *something* to solve his keyboard+monitor issue.  Assuming the server is in the same building, hooking something up shouldn't be a big deal - and shouldn't need to be done that frequently...

---

### Post by cj.surrusco on 2010-08-13
They even have switches that have a USB input now for keyboards. If the server is in close proximity to a desktop, that may be the most practical solution.

---

### Post by koenn on 2010-08-13
> **arrrghhh said:**
> Or some sort of a remote access controller like Dell has....

Lights Out Management  : [http://en.wikipedia.org/wiki/Lights_out_management](http://en.wikipedia.org/wiki/Lights_out_management)
most server hardware has it (iLO by HP is well known)
it's designed for this sort of thing, but if it's not already built-in ...

I agree with previous posters : just leave the server turned on,

---

### Post by Ldoogy on 2010-08-13
Thanks everyone. I guess maybe to try and slightly emphasize my question: Isn't it possible to tell the boot sequence to ignore all but the most critical errors in this case, so I can connect to my system and then deal with them via SSH?

It often stops due to non critical issues, just waiting for me to tap a key on the keyboard. Why?

Thanks again!

---

### Post by koenn on 2010-08-13
> **Ldoogy said:**
> Thanks everyone. I guess maybe to try and slightly emphasize my question: Isn't it possible to tell the boot sequence to ignore all but the most critical errors in this case, so I can connect to my system and then deal with them via SSH?

It often stops due to non critical issues, just waiting for me to tap a key on the keyboard. Why?

Thanks again!


what kind of errors ? 
The only errors I've seen during boot *are* critical - mostly damage to the filesystem and consequently an unreliable system and risk of data loss.
All others end up as warnings in the syslog, and don't stop you from logging on.

---

### Post by arrrghhh on 2010-08-13
> **koenn said:**
> what kind of errors ? 
The only errors I've seen during boot *are* critical - mostly damage to the filesystem and consequently an unreliable system and risk of data loss.
All others end up as warnings in the syslog, and don't stop you from logging on.

+1.  If something stops the boot process, it's usually pretty critical (in my personal experience).

---

### Post by cj.surrusco on 2010-08-13
I agree with the previous post. Any non-critical errors (such as 'keyboard not deteced') can be disabled from the bios. If the error messages can't be disabled from the bios, they are probably critical.

---

### Post by CharlesA on 2010-08-14
Agreed with the previous 3 posters.

The only "show stopping error" I've run into was after I updated to a new kernel and forgot to comment out a line in fstab before rebooting.

Having a system just sit there without displaying an error message is very very frustrating (got the problem fixed, but the lack of error message is lame)

The problem was that the device I was mounting needed to have the drivers built and added to the kernel, which needed a reboot (since I don't know how to add them on the fly to the kernel)

---

