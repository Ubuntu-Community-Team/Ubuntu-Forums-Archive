---
title: "ATI Catalyst 9.11 Released"
date: 2009-11-18
forum: The Cafe
---

### Post by Pasdar on 2009-11-18
Download it, try it and let us know if its any better, lol:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Excedio on 2009-11-18
> **Pasdar said:**
> Download it, try it and let us know if its any better, lol:
 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
 
I would, but I'm afraid to be the guinea pig for this. Anyone want to give it a shot so that I have a green light? :-D

---

### Post by Nerd King on 2009-11-18
Recent releases have been excellent and I see no reason for that to change. I'll probably test it out tomorrow.

---

### Post by Zoot7 on 2009-11-18
I'll give it a whirl in XP over the weekend, but I think I'll pass in Ubuntu.
I've Catalyst 9.10 up and running in both Karmic and openSUSE 11.2, so I don't really see any reason to upgrade. :)

---

### Post by Pasdar on 2009-11-18
**New Features**
[LIST]
[*]Support for New Linux Operating Systems
[LIST]
[*]RHEL 5.4 support
[*]openSUSE 11.2 early look support
[/LIST]
[/LIST]

**Resolved Issues**
[LIST]
[*][Ubuntu 9.04] Animated busy mouse cursor no longer disappears or flickers in Clone mode
[*]Corruption no longer occurs after hot plugging a display and doing a Virtual Terminal switch
[*]With CrossFire enabled, system no longer becomes unresponsive when switching to DC (battery) mode with full-screen applications running
[*][SUSE 11.1] Unplugging the secondary display and terminating the X server (Ctrl + Alt + Backspace) does not cause the primary display to become blank and display corruption
[*]Playing full screen Flash video on a secondary display no longer causes screen corruption
[*]Screen corruption no longer occurs when Open GL screen saver is enabled with Desktop effects
[/LIST]

**Known Issues**
[LIST]
[*]Segmentation fault may occur or system may display error during boot up if X is stopped in Dual-Head mode
[*]System may become unresponsive after executing specific combinations of Xrandr reflections and rotations
[*]X server may fail to start GUI Desktop Manager after enabling secondary adapter using Catalyst Control Center
[*]Desktop resolution changes through Catalyst Control Center might not be applied after restarting X
[*][Ubuntu 9.04] Some video cards may stop video output signal when monitor has been powered off
[/LIST]

---

### Post by Excedio on 2009-11-18
Honestly, it doesn't look like anything that I need. 9.10 is running nicely and these Bug Fixes are not related to me. I guess i'll be sticking with 9.10. :-)

---

### Post by handy on 2009-11-19
As previously posted elsewhere, it doesn't solve the xserver 1.7 incompatibility. :(

---

### Post by lethalfang on 2009-11-19
I'll bet my life it still takes 2 seconds to maximize a window. [-X

---

### Post by Pasdar on 2009-11-19
> **lethalfang said:**
> I'll bet my life it still takes 2 seconds to maximize a window. [-X
I read somewhere (i think on phoronix) that you can solve that by doing something.... but really thats the only issue ati drivers have. Last version i tested was 9.4 or something, it took 2 secs to raise window, but if you ran a heavy game it just ran it without issue and full res and settings... very weird... i heard they blame it on linux or something and say its not a bug in their drivers...

---

### Post by TheWhiteDemon on 2009-11-19
I just installed it; X started up fine which is good. Seems to work fine, plays video. Haven't done any real in-depth testing yet but so far so good.

---

### Post by Pasdar on 2009-11-20
> **TheWhiteDemon said:**
> I just installed it; X started up fine which is good. Seems to work fine, plays video. Haven't done any real in-depth testing yet but so far so good.

Did they solve the delay in minimize/maximize windows and such?

---

### Post by forrestcupp on 2009-11-20
> **Pasdar said:**
> i heard they blame it on linux or something and say its not a bug in their drivers...

That's their response to everything that is a problem.  It's funny how nvidia and other chipsets seem to work these problems out with their drivers.

---

### Post by TheWhiteDemon on 2009-11-20
> **Pasdar said:**
> Did they solve the delay in minimize/maximize windows and such?

Doesn't seem to be a problem, resizing and Min/Maxing is very responsive and quick.  I'm running an HD3650 by the way.

---

### Post by Excedio on 2009-11-20
> **TheWhiteDemon said:**
> Doesn't seem to be a problem, resizing and Min/Maxing is very responsive and quick. I'm running an HD3650 by the way.
 
That's good to hear. I run HD 3200.

---

### Post by Pasdar on 2009-11-20
> **Excedio said:**
> That's good to hear. I run HD 3200.
HD 3200 is now considered legacy isn't it?

---

### Post by Excedio on 2009-11-20
> **Pasdar said:**
> HD 3200 is now considered legacy isn't it?
 
Beats me. How can I check?

---

### Post by Pasdar on 2009-11-20
> **Excedio said:**
> Beats me. How can I check?

EDIT: your videocard seems to be unsupported by latest drivers, so it means its old i guess.

I dont see it in the list: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_911_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_911_linux.pdf)

---

### Post by markbuntu on 2009-11-20
The HD3200 is an IGP and is part of the 3xxx series and so it fully supported.

I never had any delay in maximizing/minimizing windows.

---

### Post by handy on 2009-11-20
For those interested in the maximise fix (I don't need it) you should be able to track it down with the info' on this page:

[http://aur.archlinux.org/packages.php?ID=26687](http://aur.archlinux.org/packages.php?ID=26687)

---

### Post by doorknob60 on 2009-11-21
No worse that 9.10. Unfortuanetly, no Xorg 1.7 yet though...that's what all us Arch users have been waiting for. Oh well, it's still a pretty good driver, although KDE has started acting funny around it with desktop effects on (used to be fine, started a week or two ago).

---

### Post by kpholmes on 2009-11-21
the 9.10 driver works fire with my 4890, but i have a second one that i was to run crossfire with but x always brakes. anyone know if this is fixed? last time i tried to figure out what was going on it was some compatibility error between the new ati driver and x.

i might test it out but its to much work for me to just get disappointed with my purchase again

---

### Post by Pitboss on 2009-11-23
> **lethalfang said:**
> I'll bet my life it still takes 2 seconds to maximize a window. [-X

hahahah that's a safe bet man ;)

---

### Post by willmac38 on 2009-11-27
> **Pasdar said:**
> Download it, try it and let us know if its any better, lol:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
I just downloaded the lastest drivers but how do I install them? When I click on the download I get this error message
"Could not open the file /...aller-9-11-x86.x86_64.run using the Unicode (UTF-8) character coding"
Can someone tell me how to install 3rd party drivers that you download not using the software center? plz help

---

### Post by semitone36 on 2009-11-27
Followed the wiki but just got a black screen after install. Im sure there is a work around but i didnt feel like messing with it.  

Radeon HD 4870

---

### Post by PariahVayne on 2009-11-27
> **semitone36 said:**
> Followed the wiki but just got a black screen after install. Im sure there is a work around but i didnt feel like messing with it.  

Radeon HD 4870

AGP or PCI-e?

---

### Post by Nerd King on 2009-11-27
> **willmac38 said:**
> I just downloaded the lastest drivers but how do I install them? When I click on the download I get this error message
"Could not open the file /...aller-9-11-x86.x86_64.run using the Unicode (UTF-8) character coding"
Can someone tell me how to install 3rd party drivers that you download not using the software center? plz help
I reckon you've probably not made it executable (linux doesn't automatically make it executable, for obvious security reasons). If you're in the terminal doing this...
chmod +x installer-9-11-x86.x86_64.run or whatever the filename is
If you're in GUI, right-click the file, properties -> Permissions -> Execute (tick).
Done.

---

### Post by sepimour on 2009-11-30
For those who are complaining about the minimize/maximize issue here is the fix for Ubuntu 9.10:

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

Just posting as it took me forever to find this when I went from 8.10 -> 9.04 and everyone else at work with an ATI card had this issue and was unaware of the fix.

Now let's hope the 9.12 driver fixes this ;)

---

### Post by lethalfang on 2009-11-30
> **sepimour said:**
> For those who are complaining about the minimize/maximize issue here is the fix for Ubuntu 9.10:

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

Just posting as it took me forever to find this when I went from 8.10 -> 9.04 and everyone else at work with an ATI card had this issue and was unaware of the fix.

Now let's hope the 9.12 driver fixes this ;)

Yes, this fix does work.
But something this simple shouldn't need a fix! ATI should've taken care of it in their driver.

---

### Post by handy on 2009-11-30
I've not had the need for the maximise fix with the HD2600pro GPU.

I'm still using the catalyst 9.10, & won't bother to upgrade catalyst until they have made it compatible with xorg-server 1.7.

Currently I have about 5 packages blocked from upgrading on Arch, to keep xorg-server 1.6 for the benefit catalyst 9.10.

Hopefully 9.12 gets the xorg-server compatibility thing sorted out?

---

### Post by galaver on 2009-12-14
Radeon *ATI*  HD 3470 **... **just installed 9.11 (haha what a version).. Yes I do not have problems to min/max windows... when I run basic settings... but that's why I bought (or at least I thought) an ATI and not an intel... The problem occurs in extra settings.. The delay is small but it quickly becomes annoying...  Its an embarrassment for ATI.. I have an NVIDIA much older laptop and its twice faster! I tried the fix  and indeed it fixes the problem...but I do not recommend it  unless you are prepared to suffer a huge loss in quality... Furthermore when I tried to remove I run into all kinds of troubles (the machine wouldn't boot)

Ok seriously guys I take it back... I thought I could do without the patch but its virtually imposible if you want to have some decent desktop effects, however you have to take care if you want to uninstal it and see if a new driver is working

---

