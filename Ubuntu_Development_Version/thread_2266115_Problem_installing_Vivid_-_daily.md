---
title: "Problem installing Vivid - daily"
date: 2015-02-19
forum: Ubuntu Development Version
---

### Post by fantab on 2015-02-19
Dowloaded 15.04 on 19th Feb. 
The installation gets stuck at Installation Type dialog. Specifically, ubiquity won't setup the '/' partition, it just hangs forever.
I have checked my HDD and partitions and they are all good.

I tried booting the .iso, at first, from HDD, then I also tried it from the USB, but no avail.

Has anyone else encountered this issue? Is there a known bug (I didn't find one)?

Regards...

---

### Post by VinDSL on 2015-02-19
Xubuntu, by any chance?

---

### Post by fantab on 2015-02-20
No, not Xubuntu. I have ubuntu, as prefixed.

---

### Post by ventrical on 2015-02-20
Graphics adapter type?

---

### Post by Elfy on 2015-02-20
> **VinDSL said:**
> Xubuntu, by any chance?

I've seen this in Xubuntu, Ubuntu and Kubuntu

---

### Post by ventrical on 2015-02-20
The [ubuntu] unity7 daily has the same superbug as described here [http://ubuntuforums.org/showthread.php?t=2265727](http://ubuntuforums.org/showthread.php?t=2265727)

I upgraded the daily-live, then hard installed alongside. When I chose to *restart* after the live session was finished it knocked out the desktop and my whole KVM array. (Iv'e tested the array with other installs and apparently no hardware problems. (This on nVidia graphics)

 The error I get is something about:

```


[178.911544] nouveau E[     DRM] GPU - lockup - switching to software fbcon


```

```


[xorg - failed to idle channel]


```

on nVidia G71GL [Quadro FX 3500]



Regards..

---

### Post by grahammechanical on 2015-02-20
I have had to switch to Nvidia drivers on vivid because of that nouveau GPU lockup problem. I get it when I am using Libreoffice Writer and I try to select for copying and pasting several lines of text. I do not get it with Nvidia drivers.

GPU lock up completely freezes the UI. I also get something similar when I use the workspace switcher icon to reveal the four workspaces and then I try to drag an application from one workspace to another.

Regards.

---

### Post by ventrical on 2015-02-20
> **grahammechanical said:**
> I have had to switch to Nvidia drivers on vivid because of that nouveau GPU lockup problem. I get it when I am using Libreoffice Writer and I try to select for copying and pasting several lines of text. I do not get it with Nvidia drivers.

GPU lock up completely freezes the UI. I also get something similar when I use the workspace switcher icon to reveal the four workspaces and then I try to drag an application from one workspace to another.

Regards.

Yes .. workspace switcher locked up here in live session....edit... ok .. workspace switcher working now.

edit:

Here is apport generated bug report. ( I didn't touch it) Looks like half of the part of the bigger problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1424058](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1424058)

What do you make of it?

 Regards..

edit:

Bug confirmed.

---

### Post by fantab on 2015-02-20
> **ventrical said:**
> Graphics adapter type?

Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

> **Elfy said:**
> I've seen this in Xubuntu, Ubuntu and Kubuntu

In my case Live Ubuntu works flawlessly (or performs as expected), the problem is when I try to install. 
The installer won't setup the '/' partition, it hangs at this exact step every time. I've tried it several times.

Is it the same issue that I face when trying to install Ubuntu? I am not so sure if the problem could be graphics related..

Regards...

---

### Post by Elfy on 2015-02-21
> **fantab said:**
> Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)



In my case Live Ubuntu works flawlessly (or performs as expected), the problem is when I try to install. 
The installer won't setup the '/' partition, it hangs at this exact step every time. I've tried it several times.

Is it the same issue that I face when trying to install Ubuntu? I am not so sure if the problem could be graphics related..

Regards...

Have you tried using gparted to do the partition work prior to starting the installer - so you can then Something Else and the partition just needs mounting at / ?

---

### Post by fantab on 2015-02-21
> ... - so you can then Something Else and the partition just  needs mounting at / ?

That is what I have done.
My partition is already setup (I had Bodhi Linux on it and I did format it with gparted), I am using 'Something Else' option to set the mountpoint, which is not happening.
I'll give it another try tomorrow with the latest build...

---

### Post by jerrylamos on 2015-02-21
> **fantab said:**
> That is what I have done.
My partition is already setup (I had Bodhi Linux on it and I did format it with gparted), I am using 'Something Else' option to set the mountpoint, which is not happening.
I'll give it another try tomorrow with the latest build...

Set up several partitions ahead of time with gparted, usually about 10G each.

Install with Somethin Else, choose a partition, set to Ext4, format, / 
I had done formats with gparted but ubuntu ubiquity likes to do a format again.

I typically test with a USB hard drive - the internal hard drive is Win7 - so I set the boot drive to /dev/sdb

---

### Post by fantab on 2015-02-22
I have tried the latest build every which way, still no show.
The installer won't let me set the '/' mountpoint... it hangs for ever.
I guess I'll wait for the beta1.

I was wondering if it was possible to install Ubuntu from CLI using Live media... is it?

---

### Post by Elfy on 2015-02-22
> **fantab said:**
> I have tried the latest build every which way, still no show.
The installer won't let me set the '/' mountpoint... it hangs for ever.
I guess I'll wait for the beta1.

I was wondering if it was possible to install Ubuntu from CLI using Live media... is it?

There won't be an Ubuntu Beta 1.

They no longer do that.

Not sure what to suggest tbh.

---

### Post by jerrylamos on 2015-02-22
> **fantab said:**
> I have tried the latest build every which way, still no show.
The installer won't let me set the '/' mountpoint... it hangs for ever.
I guess I'll wait for the beta1.

I was wondering if it was possible to install Ubuntu from CLI using Live media... is it?
Not sure what you mean.  
I download and update the .iso's with zsync.
Then I have an entry
sudo gedit /etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "vivid64 15.04" {
set isofile="/vivid-desktop-amd64.iso"
loopback loop (hd0,06)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
save
sudo update-grub
reboot
select the vivid entry

In development testing we do lots of updates & installs.
Ubuntu ubiquity install is complex (!) frequently full of bugs for us to find.  My opinion it would take a whole pile of cli to do what ubiquity does.

---

### Post by fantab on 2015-02-23
> **Elfy said:**
> There won't be an Ubuntu Beta 1.

They no longer do that.

Not sure what to suggest tbh.

Thanks for the info... I didn't know that.
I'll give another try after a week or so then... 

@jerrylamos: 
My problem is that I am not able to set the '/' mountpoint from the 'Installation Type' dialog during Installation. Even formatting does not work from the installer.
Ubuntu media boots fine and it works as expected.... no issues there.

---

### Post by sudodus on 2015-02-23
> **fantab said:**
> I have tried the latest build every which way, still no show.
The installer won't let me set the '/' mountpoint... it hangs for ever.
I guess I'll wait for the beta1.

I was wondering if it was possible to install Ubuntu from CLI using Live media... is it?

If you need not install in UEFI mode, you can try from the Ubuntu ***mini.iso*** - either use the menu option or install a minimal system (ticking no option) and after reboot into the minimal installed system you install the relevant meta-package, for example

```
sudo apt-get install xubuntu-desktop
```

and reboot again.

Does it work for you to set the '/' mountpoint in the mini.iso? It worked the last time I used it, but maybe that was a different version or daily build. You can find the mini.isos via ***post #3*** in the following link.

                          [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by fantab on 2015-02-24
Got it. I finally installed 15.04,  :guitar:

I am still not sure what the problem was with setting the '/' mountpoint, but looking at the parted log suggested that parted was stuck in some sort of a loop. (I regret not saving the log).
Using gparted live I deleted the partition where I was trying to install 15.04 and left myself with 'unallocated space'.
Booted live Vivid, and from the installer used 'something else', chose to create a new partition with all the needed settings and Viola!

@sudodus: Thanks for the input. I have problem with my ISP which only allows me to login from a browser and this is an issue when using mini.iso.
I have the same issue when installing Archlinux but Arch suppors install from 'existing linux' so I use Ubuntu to chroot and install Arch.
Using wifi resolves this. However as of now I don't have access to a wifi.

Regards...

---

### Post by craig10x on 2015-02-25
Off topic, but i was just curious...has 15.04 switched to the 3.19 kernel yet? (read a few weeks ago it was coming soon) i know it has been running with the 3.18

---

### Post by Elfy on 2015-02-25
> **craig10x said:**
> Off topic, but i was just curious...has 15.04 switched to the 3.19 kernel yet? (read a few weeks ago it was coming soon) i know it has been running with the 3.18

No it hasn't - there is still a .18 in proposed they wanted to drop in yesterday. Right in the middle of flavour beta 1's - I ignored the question and it went away :)

So I'd be expecting that one pretty soon.

Also - every week without fail there is a kernel meeting in #ubuntu-meeting 1700UTC on Tuesdays.

All those logs are at irclogs.ubuntu.com/ so you could check that out yourself.

Finally - they keep this up together [https://wiki.ubuntu.com/KernelTeam/Meeting#Minutes](https://wiki.ubuntu.com/KernelTeam/Meeting#Minutes)

Hope that helps.

---

### Post by craig10x on 2015-02-25
Thanks for the update, Elfy :)
I'll want to try a live session of 15.04 after 3.19 arrives in it...

---

### Post by Elfy on 2015-02-27
> **craig10x said:**
> Thanks for the update, Elfy :)
I'll want to try a live session of 15.04 after 3.19 arrives in it...

should be soonish - 3.19 is sitting in -proposed atm

---

