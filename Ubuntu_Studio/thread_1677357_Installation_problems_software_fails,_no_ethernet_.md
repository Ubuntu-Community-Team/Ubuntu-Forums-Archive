---
title: "Installation problems: software fails, no ethernet detected"
date: 2011-01-28
forum: Ubuntu Studio
---

### Post by everluck on 2011-01-28
I'm trying to install Ubuntu Studio 10.10 right now. I've used Ubuntu in the past, but this is my first time trying to install it on this system.

The first installation problem occurs during the network detection segment of installation. I am getting an error message that reads "no ethernet card detected." My motherboard is an Asus P6T Deluxe v2. Googling this issue, I found that the driver needed for this board is called "sky2." But even manually loading that driver (whether or not an ethernet cable is connected), yields no positive results. I also have a PCI-E wireless card installed (and the activity light is blinking even during installation), but again it is not being detected. I'm pretty sure it's a Linux-supported card (D-Link DWA-552). I've found people claim to have it working in Linux, anyway. But it isn't being detected by my installation, and since my hardwired connection is likewise undetected, I'm stuck without the ability to configure my network.

The next problem is installing software. It just fails sporadically sometime through the installation. I'm not sure why this is happening... is Ubuntu trying to download software packets, but unable to because there isn't a live connection?

Right now I'm trying to install again. Stick at "installing the base system." 83%. Preparing linux-image-2.6.35-22-generic. The system's just hanging here. Been stuck for about ten minutes. Not sure what's going on.

I've installed Linux quite a few times in the past. Puppy Linux, Ubuntu, Debian, Linux Mint, even Ubuntu Studio -- but all on different machines. Is there something that's simply incompatible with my current hardware? These are my specs:

Asus P6T Deluxe v2
Intel i7 920
ATI 5870

I already have Windows 7 and Mac OS X fully installed and working fine. Wanted to have a Linux installation alongside :(

---

### Post by gordintoronto on 2011-01-28
Have you tried regular Ubuntu 10.10? Anything you want that is in Studio, you can install using Synaptic Package Manager.

---

### Post by everluck on 2011-01-28
I tried Linux Mint in place of Ubuntu Studio. Same problem my first two attempts. I tried a third time (third time's the charm?) and it seemed to magically work. I haven't changed anything, so I'm not sure what the problem was.

But *now* Linux Mint will crash near the end of the installation process and tell me: GLib-WARNING 454: getpwuid_r(): failed due to unknown user id

It froze twice on me. I just stuck the disc back in there to see what happens. It picks up during the installation at the place it left off as soon as the disc is loaded, so maybe it'll work if I keep doing this...

Not sure if it matters, but I'm using EasyBCD to dual boot Windows and OS X.

It looks like maybe the Mint installation finished after I booted from disc a few more times? But now I can't get the OS to boot up properly. I don't know if it's EasyBCD or if it's a fault in the installation. Just to check -- Linux Mint 10 uses GRUB2, correct?

When trying to launch from GRUB I get a "find --set-root --ignore-floppies \grub\grub.conf" error, when trying to launch GRUB2 I get the option to enter commands, but whenever I type "boot," I'm told "kernel must first be initialized" or something to that effect. This is all through EasyBCD (which really isn't turning out to be as easy as the name suggests).

Eh, I figure it's just that Mint isn't installed correctly. Not sure what's causing the installation instability. Ah, well... I'll figure it out eventually I suppose.

Got Mint installed. Must have been my optical drive causing the problems. Worked properly after a few tries. Now to figure out how to get OS X up and running through GRUB -- it's bringing me to a text-based screen now and not getting anywhere on boot.

Sometimes it'd be nice if things just worked :lol:

---

### Post by gordintoronto on 2011-01-28
Did you check the disc?

Mint 10 uses Grub2, I am almost certain.

Is the optical drive glitch-free for other uses such as playing a CD or watching a DVD?

---

