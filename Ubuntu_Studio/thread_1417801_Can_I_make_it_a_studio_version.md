---
title: "Can I make it a studio version?"
date: 2010-02-27
forum: Ubuntu Studio
---

### Post by pc999 on 2010-02-27
Hi,

I want to put UNR on my netbook, because it is quite light and fast, pretty and can run must things.

But I had hard time getting things like Muse, Ardour and Rosegarden, in parte due to jack and realtime Kernel (?).

Things is I heard it is possible to make a normal version of Ubuntu in a ubuntu studio like, ie that there is a easy way to do that ( i am stiil quite new to linux).

Is it really possible? It is possible in UNR?

WILL I STILL NEED TO CONFIGURE THE OS? to get those apps to run well?

HOW DO I DO IT?

Thanks.

---

### Post by miegiel on 2010-02-27
> **pc999 said:**
> Hi,

I want to put UNR on my netbook, because it is quite light and fast, pretty and can run must things.

But I had hard time getting things like Muse, Ardour and Rosegarden, in parte due to jack and realtime Kernel (?).

Things is I heard it is possible to make a normal version of Ubuntu in a ubuntu studio like, ie that there is a easy way to do that ( i am stiil quite new to linux).

Is it really possible? It is possible in UNR?

WILL I STILL NEED TO CONFIGURE THE OS? to get those apps to run well?

HOW DO I DO IT?

Thanks.

I suggest you make a dual boot with 4 partitions (UNR, studio, swap and home). I suspect ubuntu studio won't be very battery-life friendly and possibly more sluggish compared to UNR.

You can make the partitions during installation, but I recommend making them in advance. You can do this with gparted from the live-CD (boot the installation CD and choose "Try ubuntu without installing", gparted is in the menus somewhere). When you install UNR or studio and get to the partitioning section of the installation, choose the "manual" option. You won't need to redo the partitions, but you do need to set which partitions you want to use and what you want to use them for (set a root, swap and home partition and leave 1 free for the root of other UNR/studio installation). You can use the same home and swap partitions for both installations.

Finally regarding the partition sizes; 10GB should be enough for UNR and studio (each) but you can make them a bit larger if you have plenty disk space (mine are 20GB but I'm making them smaller next time), make the swap partition at least as large as your memory and use what you have left for you home partition.

---

### Post by pc999 on 2010-02-28
That seems a bit hard but I will give a look.

Does the studio version will it make much more sluggish and eta much more battery? I guess I will soon discover.

Thanks.

---

### Post by miegiel on 2010-02-28
> **pc999 said:**
> Does the studio version will it make much more sluggish and eta much more battery?

To be fair that's an assumption on my part. Ubuntu studio is made with real-time performance in mind and UNR is cutout for netbooks, so both are made for very different uses. In theory real-time performance and battery economy bite each other. How hard they bite each other I don't know, but I'd be surprised if it doesn't make a difference at all.

It's not really hard once you know how to do it, and the benefits can be great. For example you can make you hard disk spin down asap in UNR for "on the road" use (saves energy and protects the disk against bumps), but there is no doubt that the disk spinning down will be really annoying while using your laptop as a studio. And there's the advantage of having a 2nd ubuntu ready to boot when you (or something else) breaks your ubuntu.

Having a separate home partition is also an advantage when you need to reinstall ubuntu or want to try a different linux flavor. All you need to do while (re)installing is tell the "partitioner" what partition to use for home (and of course _not_ format it) and all the stuff you had in your home directory will still be there. Even your settings (like your desktop customization) will be preserved.

Anyway, that's what I'll be setting up once lucid is released. For now I'll be dual-booting xubuntu kamic and xubuntu lucid alpha (alpha's do break from time to time ;)).

---

### Post by snowpine on 2010-02-28
You can install the real time kernel in your existing UNR install:

```
sudo apt-get install linux-rt
```

You can switch between kernels from the GRUB menu, so you could use the RT kernel for audio production and the "regular" kernel for general use.

The other Ubuntu Studio applications are easy to install, too. One way to do it is open the Synaptic Package Manager and search for "ubuntustudio." 

Of course, there is nothing stopping you from simply installing Ubuntu Studio on your netbook in the first place, if that's what you want. If the Netbook Remix runs okay on your hardware, then Ubuntu Studio should work too.

---

### Post by hrst on 2010-03-14
I'd like to install the studio packages on my live usb ubuntu. But apt-get doesn't find the packages. (Not even linux-rt). What's wrong?

---

### Post by snowpine on 2010-03-14
> **hrst said:**
> I'd like to install the studio packages on my live usb ubuntu. But apt-get doesn't find the packages. (Not even linux-rt). What's wrong?

Did you do

```
sudo apt-get update
```

first?

You should be able to install the applications, but I don't think you can install linux-rt in "live" mode, as switching kernels requires a reboot. :)

---

### Post by hrst on 2010-03-14
Ok, the problem was I didn't activate the universe repository.
But now when I try to install the studio packages ubuntu says I'm out of disk space, even though my 8gb live stick isn't full.

---

### Post by snowpine on 2010-03-14
> **hrst said:**
> Ok, the problem was I didn't activate the universe repository.
But now when I try to install the studio packages ubuntu says I'm out of disk space, even though my 8gb live stick isn't full.

Install Ubuntu. :) If you are running in "Live" mode, your "disk" is your RAM, and you'll lose your changes when you power down.

---

### Post by hrst on 2010-03-14
I tried to use the persistence mode [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) because I want some kind of usb system to replace my puredyne stick. I didn't think it's that hard to install ubuntu studio on a stick. Looks like I'm stuck with puredyne.

---

### Post by snowpine on 2010-03-14
I have no experience with this "persistence" option, sorry I can't be of further assistance. :(

---

### Post by mdrake36 on 2010-04-26
I have been trying to do this exact stuff. All DIY How to articles are awesome but they really get you working on Command line stuff. 
I had the problem of insterting the RT Kernel from scratch. 
So I read this thread.
Of course the Host system I am trying to create this Remix from is not RT.
So I download the RT Kernel .TAR 
This was a bit over my head as far as compiling correctly. I am very Novice and impatient.
But reading this thread I came up with this Idea.
1. Run "Sudo apt-get install linux-rt"
2. reboot with the new Kernel
3.Then follow the Customize Live CD instructions and I should be able to copy the initrd.lz and vmlinuz for the RT version, right in?

P.S. I was having trouble getting my custom console commands to find any Casper intrid.lz  or vmlinuz even non-RT. I will keep trying though.
So right now I would love to just be able to insert any Kernel in my live remix let alone a RT

---

