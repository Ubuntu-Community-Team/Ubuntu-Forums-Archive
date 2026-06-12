---
title: "New Kernel 3.8.0-19 just arrived."
date: 2013-04-19
forum: Ubuntu Development Version
---

### Post by philinux on 2013-04-19
All good after restart. No issues at all.

BFB icon is now shown clockwise as per [http://www.omgubuntu.co.uk/2013/04/clockwise-ubuntu-logo-button?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/04/clockwise-ubuntu-logo-button?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Although software updater is still anti-clock.

---

### Post by Frogs Hair on 2013-04-19
No problems since the Nvidia 3.10 driver and the -17 header . As for the bfb icon I probably wouldn't  have noticed unless pointed out.  ;)

---

### Post by Elfy on 2013-04-19
> **Frogs Hair said:**
> ... As for the bfb icon I probably wouldn't  have noticed unless pointed out.  ;)

Who would.

At least now we know it only takes one e-mail to Mark to get pointless things changed ;)

---

### Post by sgage on 2013-04-19
-19 broke my sound. Running 3.9 rc7 now with no problems.

---

### Post by Elfy on 2013-04-19
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1170697](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1170697)

---

### Post by sgage on 2013-04-19
Thanks, I added a "me too" to the bug report.

---

### Post by grahammechanical on 2013-04-19
> [COLOR=#000000]BFB icon is now shown clockwise[/COLOR]

Yes, but is the Milky Way galaxy spinning clockwise or anti-clockwise?

---

### Post by WorLord on 2013-04-19
Still busted with nVidia drivers here.  3.9 rc7 works.  -17 works.  It's the HDMI audio module -- a fix has actually been committed but didn't make it in.

---

### Post by monkeybrain2012 on 2013-04-19
> **philinux said:**
> All good after restart. No issues at all.

BFB icon is now shown clockwise as per [http://www.omgubuntu.co.uk/2013/04/clockwise-ubuntu-logo-button?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/04/clockwise-ubuntu-logo-button?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Although software updater is still anti-clock.

I don't know, In mathematics and physics positive is counter-clockwise, the right hand coordinate system is such that if look at the x-y plane from the positive z-axis, the roration that brings the  x-axis  to the y-axis is counter-clockwise, same as the right hand rule for vector product  . Whoever posted that tripe about swirling clockwise is culturally more appropriate was not a scientist. :)

Edited: Just noticed  Worlord's avatar above, it also rotates counter-clockwise if you look down from the North Pole. :))

---

### Post by mcellius on 2013-04-19
> **monkeybrain2012 said:**
> Just noticed  Worlord's avatar above, it also rotates counter-clockwise if you look down from the North Pole. :))

Maybe that's actually the South Pole!  Well, unless you use the, um, circular reasoning that the North Pole is the one that when viewed from, um, above, shows the rotation as counter-clockwise.

Of course, Worlord's avatar is like the Earth, which perhaps in a culturally-insensitive way rotates counter-clockwise.  Hey, if it's good enough for the Earth, it should be good enough for Ubuntu!

---

### Post by philinux on 2013-04-19
This.[ATTACH=CONFIG]241542[/ATTACH]

---

### Post by PJs Ronin on 2013-04-19
> **philinux said:**
> ... BFB icon is now shown clockwise''' 

Coriolis, and those of us in the southern hemisphere, are severely peeved.

---

### Post by mcellius on 2013-04-19
> ...and those of us in the southern hemisphere, are severely peeved.

Quite right.  On the other hand, you can still view it as turning counter-clockwise, but now instead of something like a swirling storm, you can view it as a rotary saw blade.

---

### Post by stinkeye on 2013-04-19
> **philinux said:**
> This.[ATTACH=CONFIG]241542[/ATTACH]
...but which way is mini wheee spinning.... is he evil or good ???

---

### Post by ELD on 2013-04-20
The new kernel is not bootable for me, -18 works fine though.

Here's my output when I try to boot -19:
Link as it's a big file taken on my phone [http://img521.imageshack.us/img521/7569/20130420131229.jpg](http://img521.imageshack.us/img521/7569/20130420131229.jpg)

---

### Post by victor9098 on 2013-04-20
Ditto with the non bootable on -19 when combined with Nvidia. Things running fine with the default Xorg drivers. That said, a successful shutdown or restart is still once in a blue moon, system tends to hang or freeze. Hard shutdown leads to Grub launching on the next launch... basically all the same bugs as the last 2 or 3 kernel updates. Have tried two fresh installs, but its when I grab the latest kernel in the updates everything goes to pot. I think the Beta I install from has the -11 kernel, but works just fine.

---

### Post by pqwoerituytrueiwoq on 2013-04-20
> **ELD said:**
> The new kernel is not bootable for me, -18 works fine though.

Here's my output when I try to boot -19:
Link as it's a big file taken on my phone [http://img521.imageshack.us/img521/7569/20130420131229.jpg](http://img521.imageshack.us/img521/7569/20130420131229.jpg)
for a phone that is a good camera
try running dpkg-reconfigure on your -19 kernel and your nvidia driver
i think i notice my system not booting from time to time with the 18 driver (nvidia gpu)
sometimes it boots and others it fails, i know it was find before the -17 kernel

---

### Post by cariboo on 2013-04-20
I had a kernel panic when trying to install -19 on my atom powered netbook. What I did was start in recovery mode, then choose:

```
dpkg
```

from the menu, after a notification that the packages couldn't be verified because of no network connectivity, the system went on to install all the updates, including the kernel. The only thing I had to do after the process finished, was install the proprietary wireless driver, and I was good to go.

---

### Post by ELD on 2013-04-21
> **pqwoerituytrueiwoq said:**
> for a phone that is a good camera
try running dpkg-reconfigure on your -19 kernel and your nvidia driver
i think i notice my system not booting from time to time with the 18 driver (nvidia gpu)
sometimes it boots and others it fails, i know it was find before the -17 kernel

I can't even boot into recovered mode on the -19 kernel though :(

---

### Post by pqwoerituytrueiwoq on 2013-04-21
then try reinstalling the kernel via synaptic

---

### Post by roly33 on 2013-04-22
> **sgage said:**
> -19 broke my sound. Running 3.9 rc7 now with no problems.

Just a quick querie where did you get 3.9 rc7 from PPA etc?

Roland

---

### Post by matt_symes on 2013-04-22
Roland

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by roly33 on 2013-04-22
> **matt_symes said:**
> Roland

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Thank's.  Can the url be added to the software Sauces list?

Roland

---

### Post by pqwoerituytrueiwoq on 2013-04-22
> **roly33 said:**
> Thank's.  Can the url be added to the software Sauces list?

Roland
just use this scripts to keep you up to date with kernels
[http://ubuntuforums.org/showthread.php?t=2137026](http://ubuntuforums.org/showthread.php?t=2137026)
it checks for update at login, if you run your box 24/7 i suggest using a cron job
by default it ignore release candidates, you can take the "-no-rc" option off under startup applications

---

### Post by ELD on 2013-04-23
I have tried re-installing the -19 kernel, it now gets to just before the login screen and freezes, very annoying as -18 still boots like a champ!

---

### Post by pqwoerituytrueiwoq on 2013-04-23
> **ELD said:**
> I have tried re-installing the -19 kernel, it now gets to just before the login screen and freezes, very annoying as -18 still boots like a champ!mine seems to do that at random, though it is over due for a clean install, not going to bother as it is a testing install and raring will be going live on that system in a day or 2, waiting on -20 to come out, if it does not come out soon i could just use the mainline kernel
if 3.9 final comes out 1st i will use that

---

