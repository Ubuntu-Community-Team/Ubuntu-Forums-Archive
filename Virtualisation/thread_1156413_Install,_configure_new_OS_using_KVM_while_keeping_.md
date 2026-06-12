---
title: "Install, configure new OS using KVM while keeping current OS running."
date: 2009-05-11
forum: Virtualisation
---

### Post by 123Mike on 2009-05-11
My harddrive has a bunch of partitions, and have a free 15GB partition.

I'd like to install Jaunty on it, but I'd like to install in the background, and I want to slowly over a few days, configure things, install things, prep it, before I make it my prime time OS. In mean time, I want to keep working my current OS (8.04).

The idea is to install inside the VM, on an actual harddrive partition, with the intention of running it raw, directly, later, once I'm happy with it.

So, did this:
$> sudo kvm -boot d -cdrom /download/xubuntu-9.04-desktop-i386.iso /dev/sda

In the partition manager I can do manual partitioning, and put '/' on that 15GB partition. Nothing else is accessing that partition.

Now, question: Is this safe? Will this work? How many problems will I see once I make the switch from Virtual to Physical?

---

### Post by 123Mike on 2009-05-11
I went as far as getting to the partition manager, and picking that partition to become '/'. But then I got scared and bailed.

Then, while doing other stuff, I was seeing that my current '/' partition (I'm *sure* it was a different partition than I was playing with in kvm) become write protected. Some data corruption I guess.
I rebooted and I had to manually run fsck. All kinds of orphaned nodes, directory structure problems, and whatnots.
I just went 'y' to all the checks, rebooted, and I'm back.
I don't know how much damage has been done.

Needless to say, I'm a little nervous now, using KVM fiddling with /dev/sda.

I'm impatiently waiting for some feedback on this issue.

---

### Post by veloce on 2009-05-11
I'm assuming that you are using partition manager from a cd or usb drive when you are changing the "/" partition. (and that you change the existing "/" drive to a new name).

Other than your corruption issue (you are doubly sure that you weren't pointing at the wrong partition?) The main issue is that it's like taking your hard drive and sticking it in a different box. All the hardware is different.  All the current drivers are redundant and all the needed ones haven't been installed.  This takes away the major benefit of "testing" Jaunty - the biggest issues are often with drivers and hardware.

---

### Post by 123Mike on 2009-05-11
> **veloce said:**
> I'm assuming that you are using partition manager from a cd or usb drive when you are changing the "/" partition. (and that you change the existing "/" drive to a new name).

I start kvm like this:
$> sudo kvm -boot d -cdrom /download/xubuntu-9.04-desktop-i386.iso /dev/sda

Then in the partition manager that's part of the installer, I choose manual settings to leave the partitions intact, and to choose /dev/sda2 for my '/' partition, which I select to be formatted with ext3 as well.

> The main issue is that it's like taking your hard drive and sticking it in a different box. All the hardware is different.  All the current drivers are redundant and all the needed ones haven't been installed.  This takes away the major benefit of "testing" Jaunty - the biggest issues are often with drivers and hardware.

On Ubuntu, and many other Linux distros, all drivers for all hardware it knows about get installed. Often, moving a harddrive over mostly works, except for the video. Sometimes there are references to a specific network driver, but not always (dynamically detects at runtime I guess). The video can be set to vesa after which I can use the built in NVidia installer.
I don't see the kind of hardware issues as you are suggesting.
Perhaps you have a bad taste in the mouth knowing how Windows can't be moved very well. But on Linux things move pretty well. I'm also not moving to a different cpu, so the risks are pretty minimal I think.

The key mission here, is that it would be so nice to be able to install the next version of Ubuntu on a partition, in the background, and then configure it, taking a few days going through apt-get after apt-get. Once I get it right, I can turn it into my host, non vm.
In the meantime, I have my old host to work on.

---

