---
title: "What's the minimum server installation?"
date: 2010-08-23
forum: Server Platforms
---

### Post by ichi2 on 2010-08-23
I'd like to create the smallest-possible installation of Ubuntu 10.04 Server x64 as a VirtualBox OSE VM.  I want to run just one service -- a Bitcoin client.  

The standard installation is about 800 MB.  By whatever approach, what's the smallest possible installation?

I find various procedures for removing unnecessary packages.  However, I suspect that there's a simpler approach that I'm missing.  By simpler, BTW, I don't mean compiling it myself.  That's far above my current comfort level.

Thank you.

---

### Post by arrrghhh on 2010-08-23
There's the net installer, but honestly you may want to go with Debian... IMHO it's much easier to start with a clean install and go bare-bones with that over Ubuntu Server...

---

### Post by Bachstelze on 2010-08-23
debootstrap with --variant=minbase

---

### Post by Vegan on 2010-08-23
Depending on what components are needed. Ubuntu can make do with 128 MB of memory but more is preferred.

Disk cost is higher as updates need a lot of space to install etc. So a 8 GB disk is about as small as you want to go.

---

### Post by Bachstelze on 2010-08-23
> **Vegan said:**
> Depending on what components are needed. Ubuntu can make do with 128 MB of memory but more is preferred.

Disk cost is higher as updates need a lot of space to install etc. So a 8 GB disk is about as small as you want to go.

I have Ubuntu running happily on 64 MB of RAM and a 2 GB CF card.  A debootstrap minbase install of Lucid amd64 will take exactly 152 MB.  Add 20-some for a kernel and GRUB, and you have a lot of available space on a 2 GB card.

---

### Post by Vegan on 2010-08-23
I installed Ubuntu on a USB stick and it fits 2 GB but I suggest more as applications need some space.

---

### Post by Bachstelze on 2010-08-23
> **Vegan said:**
> I installed Ubuntu on a USB stick and it fits 2 GB but I suggest more as applications need some space.

If you had read this thread, you would know that the OP only needs it to run one service.  I think with a 152 MB base system, any service would fit on 2 GB.

---

### Post by ichi2 on 2010-08-23
Thank you, all.

Memory isn't the critical issue, because I can tweak that in VirtualBox after installation.

It's disk size that's my concern, because I want to distribute these VMs as preloaded Bitcoin "debit cards".

I'm already using a 1 GB virtual disk.  The documentation says 400 MB, but I couldn't complete the installation with that.  I was hoping for more like 200 MB ;)

@ Bachstelze

I will explore what "debootstrap with --variant=minbase" means.

@arrrghhh

Yes, perhaps Debian.  I've tried ttylinux, and it's missing a package that's not available for it, and the idea of creating packages is totally intimidating at this point.

---

### Post by Bachstelze on 2010-08-23
> **ichi2 said:**
> 
@ Bachstelze

I will explore what "debootstrap with --variant=minbase" means.


Basically, mount your to-be root partition somewhere (since you're running that on VirtualBox, just boot a Live CD and mount the partition), and do

```
sudo debootstrap --variant=minbase lucid /mnt/root http://archive.ubuntu.com/ubuntu
```

Be warned, though, you'll have a bit of manual configuration to do (basically, everything the installer normally does for you, you will have to do it manually).  And you will also need to install a kernel and boot loader.

---

### Post by ichi2 on 2010-08-23
Thank you, Bachstelze.

My current attempt has 50 MB boot, 20 MB swap and 930 MB root.  What could I cut root to with "minbase"?

---

### Post by Bachstelze on 2010-08-24
> **ichi2 said:**
> Thank you, Bachstelze.

My current attempt has 50 MB boot, 20 MB swap and 930 MB root.  What could I cut root to with "minbase"?

As I said above, the base installation for Lucid 64 bit takes 152 MB.  I don't know about Bitcoin, though, so I can't tell you really how much additional space that would take.

---

