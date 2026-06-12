---
title: "Nvidia-xconfig update booting to blank screen new install 20.04"
date: 2021-01-24
forum: Ubuntu/Debian BASED
---

### Post by webheadjunky2 on 2021-01-24
Hi

Returned to Ubuntu after a number of years and installed the Deepin 20.04 LTS flavour yesterday

Loved it but only issue was not being able to get linked monitor working

Previously had Mint Mate 18.04 where it worked

I have an HP Omen gaming laptop with dual intel and nvidia drivers

It is connected to a Dell monitor via an HDMI connection to a Toshiba Dynandock 3.0 docking Station

I tried to do the recommended thing by trying existing forum solution first and followed steps like installing 
latest nVidia drivers (I think it was 460)

Nothing worked

The last post I read was to run: "sudo nvidia-xconfig" whixh I did. I noticed a response around creating a new /etc/xconf file or something similar

However, reboot now fails to load properly and freezes at a black screen with a login prompt

Hope this is something you can help me with and grateful for your advice 

Thanks in advance

R

---

### Post by simon-webb on 2021-01-24
Hi. If you created any custom configurations under /etc/X11 just shift them back out of there (move them to your home folder or wherever) and things should work again. One of the reasons Xorg configures hardware automatically these days is that getting the manual configuration right can be quite fiddly (in the sense that small mistakes can stop the hardware from working)...but fortunately, just getting rid of the manual configuration files should get it auto-detecting stuff again.

[Edit]: That should get you back to a working display, but not necessarily the two that you want. I wonder...do you know for sure that you were using the NVIDIA drivers on Mint MATE? If you have both Intel and NVIDIA cards, you actually have about five (!) possible setups, namely (1) you run everything off the low-power Intel chipset, (2) you run everything of the faster but more power-hungry NVIDIA chipset, or (3) you set things up so you can alternate between them, running the Intel by default but engaging the NVIDIA when you need it. I say five rather than three possibilities because an added complication is that you have a choice of two very different drivers for the NVIDIA display...the free in-kernel nouveau driver and the official proprietary closed-source NVIDIA driver (so each of the options that use the NVIDIA hardware can actually do it in two different ways). All of this means that there are lots of possibilities for what you were seeing on Mint MATE: for example, it might have been the Intel hardware driving both displays, with no involvement from the NVIDIA card at all.

As far as I know it should be possible to get the two displays working properly on any of the options for how you want to use your hardware...so it might be best to decide that first and then research the way to achieve the dual displays with that particular setup. On the other hand if you don't really care about the graphics hardware, maybe forget about NVIDIA and just use the Intel driver, because that will give you longer battery life and might just work "out of the box" for dual displays (i.e. the GUI display configuration tools should work without any additional fiddling). On the other hand if you're wanting to use your gaming laptop for gaming on Linux, the proprietary Linux driver is probably the way to go: the in-kernel nouveau and Intel drivers are safer but nowhere near as fast.

---

### Post by webheadjunky2 on 2021-01-25
Many thanks Simon for quick response

To be honest. I don't know what setup I had in Mint - it just recognised both displays and I 
was happy with that

Here I could see the default was intel and my second display was blank so something not right

Do I boot to command prompt

Grateful if you could advise re command /filepath please

Regards 
R

---

### Post by CelticWarrior on 2021-01-25
How did you install the NVIDIA drivers? In any current release it can be done automatically just by enabling the "install third-party drivers, codecs, etc." option during the Ubuntu installation.
Please also post your NVIDIA card model.
Note: The latest driver version may not be the recommended one.

---

### Post by webheadjunky2 on 2021-01-25
Hi I went into an nvidia settings tool and selected the recommended driver
from there 

From windows device manager I have:
Intel HD Graphics 630 and Nvidia GeForce GTX 1050 Ti

Cheers 
R


1

---

### Post by CelticWarrior on 2021-01-25
I'm not familiar with the "nvidia settings tool", maybe a feature of your distro?
Anyway, the driver version is correct for a GTX 1010ti

---

### Post by webheadjunky2 on 2021-01-25
If it helps to resolve, whilst I can no longer boot into 5.4.0.64, I can boot into 5.4.0.42

Cheers
R

---

### Post by webheadjunky2 on 2021-01-26
Ok I purged the newer kernel so I can boot into older kernel without selecting advanced options

I thought I might then reinstate the newer kernel via a "dist-upgrade" but that did nothing

Have I therefore done a bad thing and compromised my system? 

Also, shall I continue this thread re inactive monitor or post a new one?

Grateful if you could let me know

When I run the "nvidia-settings" command, a little pop-up advises I am in Nvidia performance mode

Typing this on phone so will post screen shot seperatelu

Cheers 

R

---

### Post by webheadjunky2 on 2021-01-26
screen dump attached

---

### Post by CelticWarrior on 2021-01-26
Have you disabled Secure Boot in UEFI settings? You should otherwise unsigned drivers like the Nvidia ones won't load. Unsure why it worked with Mint before but worth to check anyway.

---

### Post by webheadjunky2 on 2021-01-27
Thanks for this
Secure boot was already disabled 
Cheers 
R

---

### Post by webheadjunky2 on 2021-01-27
Perhaps I coukd try nouveau driver?

---

### Post by webheadjunky2 on 2021-01-27
Sorry back to square one
Noveau did not work so returned to nvida
Then tried the suggested fix on this page:
[https://forums.developer.nvidia.com/t/ubuntu-18-04-3-blank-screen-at-startup-with-430-drivers-and-gtx-960/107501/2](https://forums.developer.nvidia.com/t/ubuntu-18-04-3-blank-screen-at-startup-with-430-drivers-and-gtx-960/107501/2)

I changed the nomodeset from 1 to 0 and now booting to cursor again

Is there a way I can boot to root and edit that file

Apologies - love this desktop and want to make it my main OS but unless I can get that second monitor working again, will have to stick to windows

---

### Post by simon-webb on 2021-01-27
If it doesn't eventually launch your desktop, and you can't get far enough through the boot process to shift to another  tty (e.g. hold down CTRL-ALT-F3 to shift to tty3) and login as root  from there, you can temporarily edit a line in your GRUB menu by  pressing e...so you could just change that modeset option back, continue the boot, and then make the permanent change. If the worst comes to the worst and you don't have a backup "safe boot" line in your GRUB menu (always handy to have...leave something in there that you know will boot!), you'll just have to access the drive from another system (e.g. a rescue or install USB).

Intel's still the driver most likely to work "out of  the box", simply because it's the most commonly used driver (out of your  three options there). It tends to be gaming laptops/desktops or  high-end systems that spend the additional money on NVIDIA hardware  because they aren't happy with the (perfectly good for normal desktop  use) graphics hardware built into Intel CPUs. All of them should work  though (I've had lots of NVIDIA desktops and don't recall any problems  with multi-monitor setups either on the nouveau or NVIDIA drivers); I'm  just saying it's likely to involve the least fiddling to get it to work  with your Intel chipset.

The modesetting is in some respects a different issue from your  multi-monitor woes. Kernel modesetting is what enables your graphics  hardware to use high-resolution graphics modes straight away, while your  system's booting (without resorting to complicated framebuffer setups):  with KMS and properly configured software you can have, for example, a  nice high resolution console and/or a nice high resolution splash screen  while you're booting, and then go smoothly from that to your X  login...on some systems so smoothly that there's no discernible change  or flicker (i.e. potentially the image you're viewing while the system  boots remains on screen as the background image while you're prompted  for a login, and then can even remain in place as your desktop  background...the whole thing can feel very "seamless" with KMS). That's  all very nice but it has little to do with multi-monitor desktops in X:  you can have KMS or no KMS and X will still use whatever drivers you've  told it to use.

I've got an NVIDIA card in this desktop so will grab another monitor and  see how it works with the nouveau driver I'm using. I can probably try  the other two options as well (I don't have an either-or setup like  yours, but can simply plug the monitor directly into the motherboard to  use the Intel driver) so will have a play and report back.

---

### Post by simon-webb on 2021-01-27
OK, I wasn't able to test the Intel dual-display setup as my motherboard's only display output (apart from the standard VGA) is Displayport and I don't have a Displayport cable or Displayport-to-HDMI adapter handy. However, I did test both the NVIDIA drivers that Ubuntu 20.04 uses by default (if you install the non-free stuff), and the nouveau drivers (it takes a little bit of fiddling to enable those, because it's no longer enough these days just to echo "blacklist nvidia" >> /etc/modprobe.d/blacklist.conf, as the initrd will load before this and you'll be stuck with nvidia regardless...so you have to rebuild the initrd with update-initramfs -u -k `uname -r` as well). Anyway, first the bad news:

Everything works with no requirement for tweaking Xorg configs or anything like that. It "just works", out of the box, with both the NVIDIA and the nouveau drivers. So, I don't have anything to offer in the way of a setting change that might fix things for you.

On the other hand, some possible good news:

For a while I thought I'd hit the problem you're having: I could see the second monitor as "connected" via xrandr and the GUI tools (gnome-control-center and nvidia-settings); however, nothing would make that thing switch on. The software claimed it was working...but it just wasn't. Since you'd been having similar problems, I initally tried a few driver/settings changes to fix it...and it wasn't until nothing worked that I thought to check the hardware connection itself. HDMI cables are notoriously good at slipping out, and that's exactly what mine had done, just a tiny distance...it wasn't quite seated firmly all the way in. Pushing it firmly in solved the problem. I think the odds of your being so fortunate as to have us both encounter the same issue with the cables are extremely low...but still, it's worth checking just in case: with your docking station it sounds like you might have quite a few points of connection for HDMI cables, so make sure all of them are firmly plugged in.

Assuming that's not the issue, all I can say is that it doesn't matter on my setup whether I select the NVIDIA or nouveau drivers: both work (I didn't need nvidia-settings at all as the NVIDIA driver also worked perfectly with GNOME's built-in display settings tool...i.e. the one that you select from the little cog settings menu at the top right of the default Ubuntu 20.04 desktop...or via gnome-control-center from a terminal). If all else fails, maybe go back to Mint? Mint 20.1 is using the Ubuntu 20.04 base anyway, so it's essentially the same OS (third party Ubuntu 20.04 packages should work without problems) and is supported until 2025. Of course there's no guarantee that (current versions of) Mint will be any better, as its having shifted from the 18.04 to the 20.04 base could mean that it's introduced whatever issue you're experiencing...but I'd certainly give Mint 20.1 a try before downgrading to the old 18.04 setup that definitely works for you.

You really need advice from someone else with a similar hardware setup (one of those dual Intel/NVIDIA laptops and a docking station): I can't replicate your setup so can't really narrow things down any more. All I can say is that there doesn't seem to be any difference between the nouveau and NVIDIA drivers in this (dual display) respect: they both work out-of-the-box for me.

---

### Post by webheadjunky2 on 2021-01-28
Many thanks for those comprehensive replies. I can rule out hardware as I am presently dual booting into Windows and everything works as it should


I attach a sceeen dump from my grub file for info

Thanks again

R

---

