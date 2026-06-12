---
title: "flickering"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by matt_symes on 2012-03-24
If this is a duplicate of another thread; apologies. I had a quick scan but could not see any.

Is anybody else having crazy flicking with the panel and the launcher after the last round of updates ? The terminal is also flickering.

Using the radeon driver

```
matthew@matthew-Aspire-7540:~$ lsmod | grep rad
radeon                804304  3 
ttm                    76949  1 radeon
drm_kms_helper         42489  1 radeon
drm                   241834  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ modinfo radeon | grep -i ^ver
vermagic:       3.2.0-15-generic SMP mod_unload modversions 
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ lspci | grep -i vga
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
matthew@matthew-Aspire-7540:~$
```

```
matthew@matthew-Aspire-7540:~$ uname -r
3.2.0-15-generic
matthew@matthew-Aspire-7540:~$ 
```

I'm seeing this on both 3.2.0-15 and -20 which i installed yesterday.

From dmesg

```
matthew@matthew-Aspire-7540:~$ dmesg | grep radeon
[    1.578203] [drm] radeon defaulting to kernel modesetting.
[    1.578206] [drm] radeon kernel modesetting enabled.
[    1.579903] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.579911] radeon 0000:01:05.0: setting latency timer to 64
[    1.580367] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
[    1.580370] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    1.580890] [drm] radeon: 256M of VRAM memory ready
[    1.580892] [drm] radeon: 512M of GTT memory ready.
[    1.580933] [drm] radeon: irq initialized.
[    1.683766] radeon 0000:01:05.0: WB enabled
[    1.716187] [drm] radeon: ib pool ready.
[    1.716759] [drm] radeon: power management initialized
[    2.745560] fbcon: radeondrmfb (fb0) is primary device
[    2.745655] fb0: radeondrmfb frame buffer device
[    2.745664] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   49.923330] radeon 0000:01:05.0: texture bo too small (1600 900 26 0 -> 5785600 have 5763072)
[   49.923336] radeon 0000:01:05.0: alignments 1600 64 8 256
[   49.923338] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
matthew@matthew-Aspire-7540:~$
```

---

### Post by bluebyt on 2012-03-24
Same problem here with intel vga board.


bluebyt@SalonUbuntu:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

---

### Post by badhorse on 2012-03-24
Same problem here. Intel card:

miguel@Ogre:~$  lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

---

### Post by xerosis on 2012-03-24
Not just you: [https://bugs.launchpad.net/unity/+bug/963093](https://bugs.launchpad.net/unity/+bug/963093)

---

### Post by matt_symes on 2012-03-24
It happened sometime in-between these reboots.

```
reboot   system boot  3.2.0-15-generic Sat Mar 24 10:26 - 11:42  (01:16)    
reboot   system boot  3.2.0-20-generic Sat Mar 24 10:22 - 10:25  (00:03)    
reboot   system boot  3.2.0-15-generic Mon Mar 19 18:13 - 10:20 (4+16:07)
```

I'm going to check what was installed.

EDIT: @xerosis. Thanks for that link. I'll check it out. 

EDIT2: That looks like it. Added myself as an "affects me". It's critical so there should be a quick fix.

EDIT3: Just seen the screen cast. That's exactly what i am seeing.

---

### Post by narkosen on 2012-03-24
Same problem also.  Using ATI graphics card and radeon driver.
Tried ATI proprietary driver from additional drivers to see if that fixed things and that failed to display Unity panels etc, just the desktop image.  Shutdown was also borked.
Logging on with Unity 2D worked, so uninstalled the proprietary driver and retried Unity desktop.
It now works perfectly apart from the fact that I can no longer adjust the panel width - the option to do so has disappeared from System settings -> Appearence -> Look (normally at the bottom) !!
So for now the workaround maybe to drop into Unity 2D, logout and then back to Unity?

---

### Post by djbenny on 2012-03-24
also getting this after a reboot this morning.

---

### Post by matt_symes on 2012-03-24
unity --reset kind of fixed it for me. I have lost animation on the launcher though.

EDIT:

Animations all fixed. Added the keyboard shortcuts again. 

The only thing i have lost is the icons were highlighted when the mouse pointer was over them.

It's a setting i cannot find. Anybody know how to enable it again ?

---

### Post by cryptotheslow on 2012-03-24
Same here, had mad flickering and strange display quirks if there was a window open behind dash, fixed with unity --reset but the launcher icon "glow" no longer happens.

---

### Post by matt_symes on 2012-03-24
> **cryptotheslow said:**
> Same here, had mad flickering and strange display quirks if there was a window open behind dash, fixed with unity --reset but the launcher icon "glow" no longer happens.

Yes. That's exactly what i'm now (not) seeing. No launcher glow.

---

### Post by cryptotheslow on 2012-03-24
Can't find anything in gconf that would seem to relate glowing (or otherwise) icons except perhaps:
/apps/compiz-1/plugins/unityshell/screen0/options/backlight_mode

*Change how the icons are backlit (0 = Backlight Always On, 1 = Backlight Toggles, 2 = Backlight Always Off, 3 = Edge Illumination Toggles, 4 = Backlight and Edge Illumination)*

.... but I've no idea if that refers to launcher or something else entirely. Doesn't seem to make any difference what it is set to :confused:

---

### Post by mmasroorali on 2012-03-24
Same here with Dell 17" CRT monitor.

After the last (upgrade and) reboot, the upper part of screen has gone crazy. 

Does not happen in login interface, all hell breaks loose after I login.

```
unity --reset
```
as suggested here, [https://bugs.launchpad.net/unity/+bug/963093](https://bugs.launchpad.net/unity/+bug/963093) did not solve the problem for me. I lost everything except the desktop background.

---

### Post by VinDSL on 2012-03-24
LoL!  I had crazy flickering in the panel last week (nVidia).

The latest upgrades took care of it!  :)

Guess they're still trying to dial things in...

---

### Post by Baldrick_NZ on 2012-03-25
> **cryptotheslow said:**
> Can't find anything in gconf that would seem to relate glowing (or otherwise) icons except perhaps:
/apps/compiz-1/plugins/unityshell/screen0/options/backlight_mode

*Change how the icons are backlit (0 = Backlight Always On, 1 = Backlight Toggles, 2 = Backlight Always Off, 3 = Edge Illumination Toggles, 4 = Backlight and Edge Illumination)*

.... but I've no idea if that refers to launcher or something else entirely. Doesn't seem to make any difference what it is set to :confused:

Download Ubuntu-tweak (you'll need to get it from the website, no currently in repos?), launch, and go to 'tweaks' and click on 'Unity Settings'. You'll find a setting there, under launcher called 'Icon backlight'. Choose 'Backlight Always On'.

Close out of app. should have fixed your prob.

---

### Post by matt_symes on 2012-03-25
Hi

> **Baldrick_NZ said:**
> Download Ubuntu-tweak (you'll need to get it from the website, no currently in repos?), launch, and go to 'tweaks' and click on 'Unity Settings'. You'll find a setting there, under launcher called 'Icon backlight'. Choose 'Backlight Always On'.

Close out of app. should have fixed your prob.

That setting is also available from ccsm in the Unity plugin. No joy No glow when mouse over the launcher icons although backlight does work :O(

Kind regards

---

### Post by fhyusran on 2012-03-26
It's been happening to my Lenovo ThingPad Edge and my local brand desktop since Saturday.  Both with Intel (Core i3 and Duo).  So I stopped updating the Precise Pangoline in other units.

Any help? #-o

---

### Post by mmasroorali on 2012-03-26
> **fhyusran said:**
> It's been happening to my Lenovo ThingPad Edge and my local brand desktop since Saturday.  Both with Intel (Core i3 and Duo).  So I stopped updating the Precise Pangoline in other units.

Any help? #-o

Do not stop updating. The only way it will stop is by updating. All others have failed for me.

My office machine is affected as well.

---

### Post by clifford junior on 2012-03-26
this worked for me

```
unity --reset
```

---

### Post by mmasroorali on 2012-03-26
> **clifford junior said:**
> this worked for me

```
unity --reset
```

For me it did not. Everything went away except the screen background. 

I had to log in to terminal (Ctrl F1) and reboot my machine.

---

### Post by clifford junior on 2012-03-26
well i dunno if it makes a difference because when i was having the flickering problems i eventually couldnt even get into ubuntu or 2d, so i ran that command from within gnome and it took me to ubuntu and fixed the problem simultaneously.

maybe try and run it in gnome

---

