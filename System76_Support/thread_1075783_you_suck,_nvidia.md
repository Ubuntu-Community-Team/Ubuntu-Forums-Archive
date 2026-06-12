---
title: "you suck, nvidia"
date: 2009-02-20
forum: System76 Support
---

### Post by MorphWVUtuba on 2009-02-20
Anybody else in here have trouble with borked virtual terminals?  Has ANYONE had any luck AT ALL fixing it?

This problem is absurd, especially to have gone on so long across multiple Linux distros.  I think I even saw it pop up on a Google search from a BSD forum.  worst part is nvidia seems to just ignore it.:evil:

So, barring a miraculous fix from nvidia (not holding breath) is it possible to remove the nvidia card from the gazp5 & install an ATI card?

---

### Post by thomasaaron on 2009-02-20
```
is it possible to remove the nvidia card from the gazp5 & install an ATI card?
```

No, it's integrated.

Not that this is even close to a nice workaround, but if you use nv as the driver, can you see a virtual terminal?

---

### Post by gpstar on 2009-02-20
....

---

### Post by MorphWVUtuba on 2009-02-21
> **thomasaaron said:**
> No, it's integrated.

Not that this is even close to a nice workaround, but if you use nv as the driver, can you see a virtual terminal?

I don't even consider it even close to worth trying.  Without 3D, who cares if it works?

Probably the last nvidia card my money buys.[-(

---

### Post by soleblaze on 2009-02-23
From what I remember, in the restricted driver setup, you have the option to use driver 177 or 173 (or 163 or something like that).  The 177 driver is the one with the funky terminal problems.  Downgrading to the other driver fixes this.  (Also upgrading to the 180 beta driver seems to fix this)

---

### Post by MorphWVUtuba on 2009-02-23
> **soleblaze said:**
> From what I remember, in the restricted driver setup, you have the option to use driver 177 or 173 (or 163 or something like that).  The 177 driver is the one with the funky terminal problems.  Downgrading to the other driver fixes this.  (Also upgrading to the 180 beta driver seems to fix this)

Unfortunately, not for me.  I have the very latest 180.29 driver direct from nvidia's website.  I haven't tried the older drivers though.  It's a very recent card, 9800M GTS, so that's why I haven't done so but I may yet.

---

### Post by WatchingThePain on 2009-02-23
Hehe You think nvidia suck, wait till you try ati!.

---

### Post by 73ckn797 on 2009-02-23
**A**in't
**T**otally
**I**ntegrated into a working set-up.

That has been my ATI experience. Nvidia works for me.

---

### Post by WatchingThePain on 2009-02-23
Seriously man.. my other pc has an nvidia and I have never had problems with it like I have had with this ati card. Admittedly the price difference is large since the nvidia was like £300 and the ati cost £20. But still that shouldn't be the issue cos you'd expect to get a reasonable gui experience.
When Jimi Hendrix wrote 'are you experienced' he had no idea it would apply to ati graphics cards.

---

### Post by MorphWVUtuba on 2009-02-24
Yeah, nvidia is great, if you don't have problems.

They won't release the code, nor fix their bugs.  Google "nvidia no virtual terminals" and you'll get my point.

Don't get me wrong, it performs well as a GPU.  And if it works well for you, I'm honestly glad that you're not having trouble with either the terminals or the [faulty cards]("http://www.google.com/search?hl=en&q=nvidia+faulty+chips&btnG=Google+Search&aq=1&oq=nvidia+faul") they rushed out the door.

But from my perspective, this is bull***t.  Fix your crap or else open the code so someone else can.

Hence the title I gave this thread.

---

### Post by finite9 on 2009-02-26
doesn't it depend on which driver you use?

nVidia is crap because they only provide their own driver and if it has issues then that's tough... they may fix it in the future.

ATI is good because you can now use the free driver unless you have R700 or later, and everything works: suspend, 3d everything.  no serious bugs.

The nVidia free driver is crap.  nv is not enough good enough for 2d as far as im concerned.

If you use the ATI proprietary driver then it has issues, so like I said: it all depends on which driver you use as to how you experience that manufacturers product quality and support.

Me, I tend to go with Intel wherever possible, and then ATI as they have the best free driver support.

---

### Post by MorphWVUtuba on 2009-03-22
*BUMP*

I wish I could sticky this because it still pisses me off.  I want it to have as much mindshare as possible to build pressure on nvidia to change their aggravating ways.

...OR, get people to stop putting nvidia cards in the computers they sell and move to ATI. ;)

---

### Post by gpstar on 2009-05-21
thought i'd bump this up to see if any new progress, been annoying not having any of the virtual tty's working.

as posted in this thread

[http://ubuntuforums.org/showthread.php?t=1070706](http://ubuntuforums.org/showthread.php?t=1070706)

The bug is still present in Jaunty. Only happens when using nvidia drivers higher than the 96.43.11 version.

i've tried the "options nvidia NVreg_UseVBios=0" workaround in /etc/modprobe.d/options that some people reported success with, but it doesn't work on laptops it seems. (though the options file is gone in jaunty, but can create your own .conf file in there and it'll do the same thing).

I also notice this gets written in my Xorg.0.log file everytime I try to switch to another tty.

```
(WW) NVIDIA(0): ACPI: Error: Unable to find the DOS (Enable/Disable output
(WW) NVIDIA(0):     switching) file path under /proc/acpi/video. The NVIDIA X
(WW) NVIDIA(0):     driver will not be able to respond to ACPI display change
(WW) NVIDIA(0):     hotkey events.
```

also attached is my Xorg.0.log file.

specs
bonobo with nvidia 9800m gt
nvidia driver version 180.51

---

### Post by gpstar on 2009-05-21
ok finally solved this blank tty problem.

beta driver version: 185.18.10 solves the problem, all the virtual tty's now work.

can grab the beta driver from here

[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/)

or can install it from here and stay up to date when new versions come out.

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by betrunkenaffe on 2009-05-22
fyi, to anyone looking at trying it, it does have issues, I've experienced graphical degradation and macro blocking with it from time to time.

---

### Post by retrovertigo on 2009-05-27
I just installed the 185 driver, and suddenly lost the ability to left-click by tapping the touchpad on my laptop.  Anyone else experiencing this?  It's weird, I can still scroll with the touchpad, and right and left-click using the buttons below the touchpad... I just can't left-click by tapping.

---

### Post by thomasaaron on 2009-05-28
If you install the previous version, do you get the left clicking back? Did you make any changes to your xorg.conf?

---

### Post by retrovertigo on 2009-05-28
No, I did not get the left click back.  I didn't make any changes to my xorg.conf either.  In fact, when I reinstalled the 180 driver, I couldn't start X and had to use low graphics mode.  And the left-click still didn't work.  Being that I still don't know much about X after 10 years of using Linux (no fault but my own), I ended up having to reinstall Jaunty to fix the problem.  I'm sure there was a better way to revert, but I didn't know it.

I guess I have to deal without ttys until nVidia gets their crap together and puts out a proper driver.

---

### Post by MorphWVUtuba on 2009-07-13
I'm bumping this from my Android Dev Phone because I no longer have functional X.  I'll probably have to reinstall.

This is way beyond unacceptably aggravating.

Tom, have you guys switched to ATI yet?  How are the latest Intel cards?  Any gameable ones?

---

### Post by PatrickVogeli on 2009-07-13
nah, just forget about ati. Their newer card don't have any working 3d drivers and I believe that the closed source one don't work too well neither.. Yeah, you won't have blank terminals but you'll have other much worse problems.

Google a bit and you'll see how ati cards have been / are a trouble.

---

### Post by retrovertigo on 2009-07-13
Yeah, ATI is horrible. Their proprietary driver doesn't work for pre-2.6.28 kernels, and the open-source driver does absolutely zero acceleration on 2.6.28+ kernels either. I had to compile a 2.6.27 kernel on my Fedora box to get acceptable video performance.

---

### Post by MorphWVUtuba on 2009-07-13
Ubuntu community FTMFW

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

