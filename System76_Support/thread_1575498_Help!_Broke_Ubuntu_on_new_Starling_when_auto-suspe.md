---
title: "Help! Broke Ubuntu on new Starling when auto-suspended during Upgrade Manager run"
date: 2010-09-15
forum: System76 Support
---

### Post by Ms.N on 2010-09-15
Hello,

I'm brand-new to these forums because I'm brand-new as a customer of system76.

I have a Starling; it just arrived yesterday, and today I brought it to a coffee shop with me to do the setup.

Initial setup went fine, OS desktop looked lovely. I have some basic familiarity with Ubuntu, so I started Upgrade Manager and played with some other settings too, specifically the ones for power management (in hindsight, ugh)! Set it to suspend after 30 minutes, I believe.

It did suspend in the middle of upgrading, and when I brought it out of suspend it let me log back in normally and then showed me a frozen screen. No mouse or keyboard response, and it was in the middle of installing something to do with Flash. I waited 10 minutes and then shut the machine off after it didn't appear to make further progress (the details dialogue was showing on that install, so I could tell).

On reboot, it never got to the OS. Instead, I got this series of messages:[INDENT]*udevadm trigger is not permitted while udev is unconfigured.*
*udevadm settle is not permitted while udev is unconfigured.*
*udevadm settle is not permitted while udev is unconfigured.*
*udevadm settle is not permitted while udev is unconfigured.*
*ALERT! /dev/disk/by-uuid/[long character string; happy to type this if important] does not exist. Dropping to a shell!*

*Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell  (ash)*
*Enter 'help' for a list of built-in commands.*

*(initramfs)*
[/INDENT]And that's it, folks. No more Ubuntu access. Apparently it wasn't okay to suspend in the middle of what it was doing? 

Ran recovery mode by accessing GRUB during boot. Completed normally, then back to the same messages as above.

That's the extent of what I know to try. Looking forward to guidance!

Thanks very much,

Ms. N

---

### Post by wilee-nilee on 2010-09-15
Go to recovery again go to the last line, it is a terminal that will if, the Ethernet is plugged in will access the web, and run these two commands, you have to be hooked up to the web if the download was still happening.

```
sudo dpkg --configure -a
```
then
```
sudo apt-get install -f 
``` 

Hopefully this will clear up what is needed to finish the update/upgrade.

---

### Post by Ms.N on 2010-09-15
Thank you very much for the quick response!

Unfortunately, I don't see a terminal prompt anywhere after running recovery. Also, I have no Ethernet access available to me---I have a MyFi 2200 and can access it as WiFi, can use public WiFi, or can use the MyFi as a USB modem. I think all of those options require me to be past this problem to connect? So I don't seem to have a way to boot up with an Internet connection in place.

Tried typing in your first sudo command at *(initramfs)*, but got this:[I]

/bin/sh: sudo: not found
[/I]
Any other suggestions? Also, generally, must one turn off the suspend function whenever running Upgrade Manager?

---

### Post by wilee-nilee on 2010-09-15
> **Ms.N said:**
> Thank you very much for the quick response!

Unfortunately, I don't see a terminal prompt anywhere after running recovery. Also, I have no Ethernet access available to me---I have a MyFi 2200 and can access it as WiFi, can use public WiFi, or can use the MyFi as a USB modem. I think all of those options require me to be past this problem to connect? So I don't seem to have a way to boot up with an Internet connection in place.

Tried typing in your first sudo command at *(initramfs)*, but got this:[I]

/bin/sh: sudo: not found
[/I]
Any other suggestions? Also, generally, must one turn off the suspend function whenever running Upgrade Manager?

I'm on my way to a overnight stay at a sleep clinic so the only thing I can do now is say, never let the computer shutdown during any update or upgrade it just creates a lock. Hopefully a system76 person or others will chime in. I will be back on line in a couple of hours.

---

### Post by Ms.N on 2010-09-15
Yes, somehow I thought the update would create enough activity that it wouldn't suspend. Now I know better, and thanks. Good luck on your sleep study!

*crosses fingers, hopes for additional help*

---

### Post by isantop on 2010-09-16
When you boot into recovery mode, do you get a prompt asking what you want to do? If so, you should look for an option labeled "Netroot" or similar. Select that, and you should get to a command line resembling:
```
root@system76-laptop:~#
```
At this prompt, try running this:
```
dpkg --configure -a
```
That should at least allow you to boot into your desktop and re-run the update.

Interrupting updates are going to be hit and miss all the time. It will depend on what gets installed/configured before the interruption. If you interrupt after a vital system component is installed but before it gets configured, it won't work, and subsequent boots will fail.

In the future, if this happens by accident, the best thing to do is to immediately (without shutting down) press Ctrl+Alt+F1 to get to console, then login and run:
```
sudo dpkg --configure -a
``` That should configure any installed updates. Then, try:
```
sudo apt-get install -f -y
``` to make sure all of your dependencies are satisfied, then:
```
sudo apt-get update -y && sudo apt-get upgrade -y
``` which will attempt to re-update any remaining packages. Finally:
```
sudo reboot
``` to restart  safely.

---

### Post by Ms.N on 2010-09-16
Hello,

Thank you so much for your reply! I also very much appreciate you letting me know how to handle this kind of situation if it happens again in the future. That's comforting in the long run.

Meanwhile I'd love to do what you suggest and could, if only I could get a prompt. But I actually get nothing before the Busybox prompt *(initramfs) *pops up. That's the first time it gives me a chance to type anything after selecting recovery mode. So, things appear to be badly off enough that I can't get a regular prompt in the first place---or perhaps I'm not talking about the "recovery mode" that you mean?

I'm getting to GRUB by holding down Shift during boot, right after the System76 screen disappears.

There are two recovery options in GRUB that I can see. The first is with Linux 2.6.32-24-generic, and the second is with Linux 2.6.32-21-generic.

The first one is the only one that actually ends up at Busybox. The second one appears to hang. 

A. When I choose the first one, text scrolls by, stopping with this as the last:

[I]Begin: Mounting root file system...
Begin: [/I][something][I] /scripts/local-top...
Done.
[/I]
The cursor then flashes underneath but doesn't accept any input. About a minute or so after that, the system goes right to the Busybox prompt, via the process I mentioned in my first post and still never asking me what I want to do before *(initramfs) *comes up. Typing "netroot" at the Busybox prompt gets me */bin/sh: netroot: not found*

B. When I try the second recovery option, I get the following:
[many strings of apparently informative text, ending with...]
*Big FIFO is enabled. *

The cursor flashes underneath that last without actually showing me a prompt at all. Just now, I let this go for 5 minutes, by the clock, and when nothing else happened and the drive wasn't spinning, I shut the Starling down again.

So, can you help me get to a prompt?

Thanks again.

---

### Post by isantop on 2010-09-16
If you have access to a liveCD or liveUSB, you can boot to it, and do it from there.

From the Live Desktop, go to Applications > Accessories > Terminal. First, run the following commands:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo cp /mnt/etc/resolv.conf /etc/resolv.conf
sudo chroot /mnt

```
This will give you that root prompt I mentioned. Then, try running those commands again.

---

### Post by Ms.N on 2010-09-16
Thanks. Okay, worked through some snafus downloading to create a Live USB**, **but once that was done the rest of your instructions worked well, and I appear to be set.

May I ask what that sequence did that I was typing into the Live terminal to get to root? I'd just like to understand what was needed!

---

### Post by isantop on 2010-09-17
No problem.

The heart of this sequence is the chroot command. That bassically allows you to login to a computer with / somewhere other that the actual /. In this case, the original / was the root of the Live Disk, so running thing there would apply to the disk. We wanted your hard disk, so we mounted it with "sudo mount /dev/sda1 /mnt" then used chroot to make that the root of our filesystem.

Everything else was prepping for that. The second two mounts take important files for the system and make them available to the chroot environment. The cp command took a network configuration file and compied it to the chroot, so that the apt-get commands would work.

Sorry if this is a technical explanation. It's a very technical process. If you have any questions, feel free to ask.

---

### Post by Ms.N on 2010-09-17
Thanks!

I did want the somewhat technical response---I'm realizing that if I'm going to use a Linux netbook, I need to be able to handle that. :)

Your help has been greatly appreciated. All seems fine now, and I am pleased.

Ms. N):P

---

### Post by isantop on 2010-09-17
You shouldn't need to be technical with it. That's the real beauty of Ubuntu; you can have a technical system if you want one, but you don't have to have one if you don't want to.

---

