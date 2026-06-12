---
title: "Display Problems - Ubuntu Host w/ Win7 Guest Need Win to 3rd physical monitor"
date: 2016-09-28
forum: Virtualisation
---

### Post by win10-2-zorin11 on 2016-09-28
Hi All,

I'm a recent Win10 convert and so-far happy about it. Actually starting to like apt-get but not liking the USB or Display idiosyncrasies. 
Understand I just need more knowledge can you please spread some my way?

**Hardware**
AMD 8-core supports vx 
NVIDIA 740 supports two displays via DVI
GeForce Built in Graphics - supports HDMI/DVI/VGA
Memory 8 GB
Bios - Set so both video cards are active but disabled UMA
USB3 Support
jCreate USB to VGA
Tritton UV150 USB to VGA[B]

Host[/B]
Ubuntu 14 running [B]Virtual Box with vBox Extensions installed
[/B]Using two monitors connected via DVI to the NVIDIA 740

**Guest**
Win 7 Ultimate
2 GB reserved
2 CPU reserved @ 90%
USB 3 Set
Guest extensions installed

[B]Problem
[/B]I need three, or better yet four monitors- do not care about poor performance[B]

What I've Tried[/B]
I can get two displays to work from NVIDIA but can't detect anything on the second video card
I can get the one display to start loading Linux but it stops with errors when it figures out that the two DVI monitors are no longer the same and it won't go any further.
I can boot Linux off the other video card if I set that one to default but it won't start fully - it gets confused (won't start) because my monitor situation changed.
I tried using both of the USB to VGA devices in Linux  - no luck at all. 
[LIST]
[*]Tried debugging with dmesg
[*]Saw the j3Create USB to VGA's in dmesg
[*]Saw the Tritton USB to VGA in dmesg
[*]No displays would be detected however.
[/LIST]
But since I couldn't get more than two on Linux thought I'd get smart and use a guest Win7 to use the USB to VGA's but it won't work I enabled USB3 and make sure to check mark the device.
Tried increasing displays to 2 in vBox settings - just gave me a second virtual screen- that's no help.
I'll take 3 monitors ANY way I can get it with the hardware I've got - any suggestions- am I going about it wrong? I do use windows for my job so it would be helpful to have running all the time as virtual machine.
I'm so close to being able to blow away my dual boot Windoze machine -if I solve this it's gone.

Is it hopeless? Am I going to have to reinstall Linux using the first card as the primary one?

---

