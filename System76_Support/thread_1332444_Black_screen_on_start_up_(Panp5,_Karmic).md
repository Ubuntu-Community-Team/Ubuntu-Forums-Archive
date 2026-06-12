---
title: "Black screen on start up (Panp5, Karmic)"
date: 2009-11-20
forum: System76 Support
---

### Post by jtappin on 2009-11-20
I recently upgraded my PanP5 from Jaunty to Karmic the "old fashioned way" (i.e. edit /etc/apt/sources.list and then run apt-get from the console -- I've had too many upgrades in graphical mode kick X out from under themselves part way through). 

I have Kubuntu installed over the top of the original installation.

Now when I start the system up the normal Kubuntu splash screen shows, but when it tries to start X it frequently comes up with a completely black screen -- no cursor indicator of any kind. 
Typically if I hold down the off switch and then switch on again it works the second time.

From looking through the Xorg logs it appears that there are problems find the keyboard & mouse.

Does anybody have any ideas what's happening and how to solve it?

---

### Post by thomasaaron on 2009-11-20
> Typically if I hold down the off switch and then switch on again it works the second time.

Well, it's odd that it would *intermittently* have difficulty finding the keyboard or mouse. Failure to find a keyboard and mouse most likely would be a grub-related problem.

The fact that it sometimes finds the keyboard and mouse and boots leads me to believe that the system is having some difficulty finding some boot scripts. It's possible that something got muddled in the upgrade.

If I'm right, you could try running fsck from a live CD. If that doesn't work, you may need to just do a fresh install.

To run fsck, first boot from a live CD. Once you are booted, to to System > Administration > Partition Editor. This will show you your current partiton layout and the designations of your partition. For example, your partitions may be /dev/sda1, /dev/sda5, and /dev/sda7. Whatever the designations, make note of them. 

Then open a terminal (Applications > Accessories > Terminal) and run fsck as follows (only use your own partition designations)...

sudo fsck /dev/sda1
sudo fsck /dev/sda5
sudo fsck /dev/sda7

fsck will examine your filesystems and try to repair any damage. Occasionally, filesystems get too broken for fsck to fix them. In this is the case, it may be necessary to put a fresh image on your machine.

It could also mean that you have a faulty hard drive. However, this is pretty rare, and it is better to try re-imaging the machine first.

---

### Post by jtappin on 2009-12-07
From what I can tell the problem only seems to happen if I have the Logitec NanoReceiver for the external mouse plugged in on boot up. This also sometime leads to X starting in safe mode with an error about an axis initialization problem.

I suspect therefore that the problem is that somewhere X or the kernel is not waiting long enough for the receiver to respond.

---

