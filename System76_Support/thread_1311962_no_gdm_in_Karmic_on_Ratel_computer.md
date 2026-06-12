---
title: "no gdm in Karmic on Ratel computer"
date: 2009-11-02
forum: System76 Support
---

### Post by seedsgrow on 2009-11-02
I recently upgraded the Jaunty system on my Ratel value desktop computer to Karmic and cannot get the desktop manager to load. Booting proceeds normally up to that point, but all I get of the Gnome desktop is a one-pixel wide stripe along the left edge of the monitor. I downloaded a copy to see about doing a fresh install, but the live system does the same thing. The graphics processor is Intel X3100, the cpu is a Pentium Dual Core E6300. The Karmic live system works fine on my laptop. Any thoughts on what the problem is and how I can fix it?

---

### Post by thomasaaron on 2009-11-03
Hmmm... 

The Karmic live CD you tested with... how old is it? If it's not the newest iteration, you should download and burn a fresh image.

We're not seeing this problem on the X3100, so it's probably something on your system.

If you press the Esc key when you see the grub countdown, it will show you what kernels are available. Which one are you booting into (it will be the first one in the list).

---

### Post by HotShotDJ on 2009-11-03
> **thomasaaron said:**
> If you press the Esc key when you see the grub countdown, it will show you what kernels are available.Not in Karmic it won't.  To get to the grub menu, you must press and hold down the "Shift" key as soon as the word "Grub" appears in the upper left side of the screen, and keep holding it down until the Grub menu appears.

... unless, of course, the Karmic install left the legacy version of Grub intact on the mbr... in which case, the Esc key might still work.

---

### Post by ctsdownloads on 2009-11-03
> **HotShotDJ said:**
> Not in Karmic it won't.  To get to the grub menu, you must press and hold down the "Shift" key as soon as the word "Grub" appears in the upper left side of the screen, and keep holding it down until the Grub menu appears.

... unless, of course, the Karmic install left the legacy version of Grub intact on the mbr... in which case, the Esc key might still work.

I can confirm the lack of Esc doing squat with 9.10 during the boot - had me going nuts! :lolflag:

I have the same PC, but with ATI graphics. So I cannot duplicate for ya. Sorry...

---

### Post by seedsgrow on 2009-11-03
I brought up the Grub menu on the upgraded system, which I did by pressing Esc, as I was trying to get it working Sunday, November 1. I had two kernels available then, 2.6.28 and 2.6.31. I could get gdm to load in the earlier kernel, but there was no audio, and Firefox was too sluggish to use. I didn't really want to explore what all the problems with that kernel were anyway, since one reason I upgraded is to have a newer kernel. Besides, when I ran the system in recovery mode, I lost access to 2.6.28, probably when the obsolete files were deleted, so all that I have left to work with on the upgraded system is kernel 2.6.31.

I downloaded Karmic yesterday, November 2 and used it to make a live USB stick. Only kernel 2.6.31 is available on it as well.

Thanks for your efforts.

Tom

---

### Post by seedsgrow on 2009-11-03
I brought up the Grub menu on the upgraded system, which I did by pressing Esc, as I was trying to get it working Sunday, November 1. I had two kernels available then, 2.6.28 and 2.6.31. I could get gdm to load in the earlier kernel, but there was no audio, and Firefox was too sluggish to use. I didn't really want to explore what all the problems with that kernel were anyway, since one reason I upgraded is to have a newer kernel. Besides, when I ran the system in recovery mode, I lost access to 2.6.28, probably when the obsolete files were deleted, so all that I have left to work with on the upgraded system is kernel 2.6.31.

I downloaded Karmic yesterday, November 2 and used it to make a live USB stick. Only kernel 2.6.31 is available on it as well.

Thanks for your efforts.

Tom

---

### Post by thomasaaron on 2009-11-04
If you boot from the karmic usb stick, does gdm start?

If so, you might want to just do a fresh install of karmic. I'm seeing a lot of corrupted upgrades right now. And whenever I get one issue fixed, there are seven more right behind it.

---

### Post by seedsgrow on 2009-11-04
Sorry, I thought I had made it clear when I said in my original post that the live system behaves the same way as the updated system that gdm does not load when I boot into it, either. The notion that I could do a fresh install is what led me to download and try to boot into the live system.

---

### Post by thomasaaron on 2009-11-04
Sorry. Indeed you did. It gets hard to track these issues when there are so many of them, and the threads start getting long.

Try booting into recovery mode and running...

apt-get --reinstall install xserver-xorg-video-intel
reboot -h now

Did that fix it?

If not, boot back into recovery mode again and run this command...

dpkg-reconfigure xserver-xorg

In the resulting configuration utility, choose *all* default options.

When it is finished...

reboot -h now

---

### Post by seedsgrow on 2009-11-05
Thanks for the suggestion; however, it did not work.

I did get a Sabayon 5.0 KDE version live USB to load its desktop environment. I'll either install a KDE distro or try another 2.6.31-based Gnome distro. If I do try another new Gnome distro, are you interested in hearing whether it loads gdm? I'll e-mail you results if you are. Otherwise, I just say thanks for your efforts and leave it at that. I'm going to give up on Ubuntu 9.10 for now. Maybe by the time Mint 8 is released they will have made a change that allows the system to work on my computer.

---

