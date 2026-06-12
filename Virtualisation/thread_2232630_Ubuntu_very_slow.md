---
title: "Ubuntu very slow"
date: 2014-07-03
forum: Virtualisation
---

### Post by RaoulJWZ on 2014-07-03
Hello everyone,
I've installed ubuntu on virtualbox on my windows 7.
I only have a big problem: It runs so very slow.
I gave Ubuntu the recommended amount of ram, so everything should work fine i think.
Is there anyway to fix this?
BTW i have to run it from the cd, because it can't detect my windows and if i want to install it, it wil erase everything i have on my pc it says.
So i don't know if that could cause the slowness, if so: How can i fix the system error?
Thanks

---

### Post by slickymaster on 2014-07-03
Moved to the **Virtualisation** sub-forum.

What sort of resources have you given to your VM:

[LIST]
[*]How many 'Processors' have you allocated?
[*]How much RAM have you allocated to the VM?
[*]How much video memory?
[/LIST]

Take a read at this guide to speed up Virtual Machines: [http://www.howtogeek.com/124796/the-...tual-machines/](http://www.howtogeek.com/124796/the-...tual-machines/)

---

### Post by kc1di on 2014-07-03
if your running it from CD it's going to be slow as it has to uncompressed the files on the fly.
you should be able to install it in your Virtual machine without affecting any windows host programs. 

but if you want to install it to the Hard Drive you need to be careful about how you install.  The disk partitioning page is the important step.
There is a choice on that page that should offer to install ubuntu along side Windows and it will shrink the windows space and make room for ubuntu for you.
**As Always though back up any important files first.  Mistakes do happen!**

here is a [page about dual booting ]("https://help.ubuntu.com/community/WindowsDualBoot")that may be of help.
Other than that install it to VirtualBox it will be a bit slower than an H.D. Install but will be much faster than running for the live DVD.

---

### Post by 3rdalbum on 2014-07-03
Ubuntu requires 3D acceleration. If you don't have 3D acceleration (for instance, inside a virtual machine) it uses the CPU to render the desktop. This is quite a bit slower than using your GPU.

Virtualbox comes with a "Guest Additions" package that enables some level of graphics acceleration in Linux guest OSes, you should consider installing that. You may get a bit of a speedup.

---

### Post by TheFu on 2014-07-03
Old/slow CPUs cannot be fixed. What is yours?
After that, follow these instructions on settings - it isn't just RAM: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

You don't need to run from a CD. That will be terribly slow. Re-read my other posts to you in the other thread and create a vHDD for the VM to install Ubuntu into. 

BTW - this virtualization stuff takes time to get used to. It is hard to think "virtual machine" until you get used to it. It will NOT wipe your windows install.

---

