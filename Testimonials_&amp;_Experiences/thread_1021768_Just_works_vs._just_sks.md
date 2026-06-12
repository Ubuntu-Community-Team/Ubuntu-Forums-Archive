---
title: "Just works vs. just s**ks"
date: 2008-12-25
forum: Testimonials &amp; Experiences
---

### Post by uljanow on 2008-12-25
hi
I was running Ubuntu Intrepid for over a month now. I was quite happy with it until I needed to compile a custom kernel due to a 4 GB RAM upgrade.

I tried using the debian way (make-kpkg) but since I use fglrx which comes with dkms there is no easy fix. First, you need to deal with this [bug]("https://bugs.launchpad.net/ubuntu/+bug/292606"). After installing linux-image* and linux-headers* of the custom kernel I ended up with the error message describing that dkms isn't satisfied with the kernel headers (missing Makefile_32.cpu). Trying to remove fglrx* and using the packages from the ati installer doesn't work either because the ubuntu packages have an epoch ("2:.*").


Unless you don't touch your system, you're fine...:(

---

### Post by hardyn on 2008-12-25
does 64bit not enable above 4gb by default?

---

### Post by uljanow on 2008-12-25
Yes. But I was using 32 bit Ubuntu. There's also a server kernel which has PAE enabled but that's not an option on a desktop machine because it has other disadvantages.

---

### Post by solwic on 2008-12-26
> **uljanow said:**
> 
Unless you don't touch your system, you're fine...:(

Much as I love Ubuntu (it's the only OS on my system, and will continue to be so), I have to say +1.  I've struggled with OpenOffice3 and Kubuntu too many times, and this lesson becomes painfully clear:  if you leave Ubuntu alone, it's good.

Change something - anything - and you run the risk of borking your system.  :(

Ah well, the price of freedom.  :P

---

### Post by 3rdalbum on 2008-12-26
PAE sounds like a good idea, but it never works properly on any operating system, partly because there's less that's compatible with 32-bit PAE than with 64-bit. Just install a 64-bit operating system if you've got a 64-bit processor. If your processor is 32-bit, then just "suffer" with a "measly" 3.3GiB of RAM and bear in mind that the computer I'm currently typing this on has less than 1/6th that amount.

---

### Post by wolfen69 on 2008-12-26
just out of curiosity, what are you doing that requires 4gb of ram? i remember having 12 apps working at the same time and only using 800-900mb. if 32bit ubuntu sees "only" 3gb, will it affect you?

why not just use the stock configuration? why make things harder for yourself?

---

### Post by kerry_s on 2008-12-26
i thought all modern kernels support up to 4gigs, so only if you have more than 4 gigs should you need to use a bigmem kernel.

have you tried telling the kernel "mem=4096" on the boot line?
how much ram is it showing with the "free" command?

---

### Post by cb951303 on 2008-12-26
with 32bit OS you are supposed to have 3.3GiG ram max. Sure there are workarounds like PAE or memory remapping (BIOS feature) but in short, if you want to use your 4GiG+ ram you should use 64bit OS.

---

### Post by dmizer on 2008-12-26
> **uljanow said:**
> Unless you don't touch your system, you're fine...:(
Do you think it's fair to put an OS independent architectural limitation in the same league as a usability issue?

I understand that it sucks to have to go through that much effort; on the other hand, is it even possible at all to utilize 4gig of ram in 32bit Windows?

---

### Post by uljanow on 2008-12-26
It looks like I have to use 64 bit Ubuntu (although using PAE is still reasonable). I guess there is no such thing as a perfect Distro...Maybe I'll give CentOS/RHEL 5.3 a shot when it's released.

---

### Post by 3rdalbum on 2008-12-27
> **uljanow said:**
> It looks like I have to use 64 bit Ubuntu (although using PAE is still reasonable). I guess there is no such thing as a perfect Distro...Maybe I'll give CentOS/RHEL 5.3 a shot when it's released.

Why are you opposed to running 64-bit Ubuntu? I'm using it right now - it's virtually identical in operation and configuration to 32-bit Ubuntu. Being opposed to 64-bit Ubuntu is like saying "I'm happy with Windows XP Home; I don't want to switch to XP Professional because I don't want to learn a new operating system".

PAE is a dead-end, and it will not work unless your drivers support PAE. Of course, all open-source Linux kernel drivers support 64-bit, but I'd bet my lunch money that not all of them support PAE.

---

### Post by uljanow on 2008-12-27
IMHO x86 is the best supported and tested architecture. But I haven't run into problems yet. Especially setting up flashplayer is easy thanks to the [64 bit version]("http://labs.adobe.com/downloads/flashplayer10.html").

---

### Post by dmizer on 2008-12-28
> **uljanow said:**
> IMHO x86 is the best supported and tested architecture. But I haven't run into problems yet. Especially setting up flashplayer is easy thanks to the [64 bit version]("http://labs.adobe.com/downloads/flashplayer10.html").

While that may be true, you're asking a 32 bit OS to go beyond it's physical limitations. This is an architectural problem, not an OS problem. 32 bit Windows also cannot fully utilize 4 gig of RAM.

---

