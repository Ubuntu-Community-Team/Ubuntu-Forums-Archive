---
title: "App-indicator gone wild!"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-03-13
Since yesterday's updates, I find that the items that the panel displays (user name, date/time, network status, menu for shutdown/restart etc) are there when I login but disappear after about 30 seconds. No indication from the GUI that anything has crashed, but when I have a look at syslog I see the following series of messages. This problem wasn't happening previously:
```
Mar 14 06:26:59 1204Test goa[2145]: goa-daemon version 3.3.0 starting [main.c:112, main()]
Mar 14 06:27:10 1204Test kernel: [   83.706919] unity-panel-ser[2056]: segfault at 20 ip 00007ff74d368b92 sp 00007fff2e0e5ae8 error 4 in libglib-2.0.so.0.3120.0[7ff74d2ee000+f2000]
Mar 14 06:27:12 1204Test kernel: [   85.483180] unity-panel-ser[2292]: segfault at 20 ip 00007f0ed4a56b92 sp 00007fff27a5b4a8 error 4 in libglib-2.0.so.0.3120.0[7f0ed49dc000+f2000]
Mar 14 06:27:12 1204Test kernel: [   85.697265] unity-panel-ser[2302]: segfault at 20 ip 00007f0ce8059b92 sp 00007fff9a919018 error 4 in libglib-2.0.so.0.3120.0[7f0ce7fdf000+f2000]
Mar 14 06:27:12 1204Test kernel: [   85.933398] unity-panel-ser[2312]: segfault at 20 ip 00007f485be51b92 sp 00007fff9b852908 error 4 in libglib-2.0.so.0.3120.0[7f485bdd7000+f2000]
Mar 14 06:27:13 1204Test kernel: [   86.161999] unity-panel-ser[2364]: segfault at 20 ip 00007f726da42b92 sp 00007ffff6526338 error 4 in libglib-2.0.so.0.3120.0[7f726d9c8000+f2000]
Mar 14 06:27:13 1204Test kernel: [   86.378641] unity-panel-ser[2374]: segfault at 20 ip 00007f8db2990b92 sp 00007fff20d5d1b8 error 4 in libglib-2.0.so.0.3120.0[7f8db2916000+f2000]
Mar 14 06:27:13 1204Test kernel: [   86.589984] unity-panel-ser[2384]: segfault at 20 ip 00007fde658e7b92 sp 00007fff5c33e708 error 4 in libglib-2.0.so.0.3120.0[7fde6586d000+f2000]
Mar 14 06:27:13 1204Test kernel: [   86.802832] unity-panel-ser[2394]: segfault at 20 ip 00007f82a99cdb92 sp 00007fffa6548a88 error 4 in libglib-2.0.so.0.3120.0[7f82a9953000+f2000]
Mar 14 06:27:13 1204Test kernel: [   87.028535] unity-panel-ser[2405]: segfault at 20 ip 00007fa01c101b92 sp 00007fff3556f728 error 4 in libglib-2.0.so.0.3120.0[7fa01c087000+f2000]
Mar 14 06:27:14 1204Test kernel: [   87.251477] unity-panel-ser[2457]: segfault at 20 ip 00007f291b9c5b92 sp 00007fffeefd7018 error 4 in libglib-2.0.so.0.3120.0[7f291b94b000+f2000]
Mar 14 06:27:17 1204Test kernel: [   90.595404] show_signal_msg: 15 callbacks suppressed
Mar 14 06:27:17 1204Test kernel: [   90.595407] unity-panel-ser[2753]: segfault at 20 ip 00007fd7f8b51b92 sp 00007fff4af10f38 error 4 in libglib-2.0.so.0.3120.0[7fd7f8ad7000+f2000]
Mar 14 06:27:17 1204Test kernel: [   90.813546] unity-panel-ser[2763]: segfault at 20 ip 00007ffe86649b92 sp 00007fffc9ab5a48 error 4 in libglib-2.0.so.0.3120.0[7ffe865cf000+f2000]
Mar 14 06:27:17 1204Test kernel: [   91.016338] unity-panel-ser[2773]: segfault at 20 ip 00007f3f07b50b92 sp 00007fffdb98aac8 error 4 in libglib-2.0.so.0.3120.0[7f3f07ad6000+f2000]
Mar 14 06:27:18 1204Test kernel: [   91.216910] unity-panel-ser[2784]: segfault at 20 ip 00007fc4fd7beb92 sp 00007fff486749b8 error 4 in libglib-2.0.so.0.3120.0[7fc4fd744000+f2000]
Mar 14 06:27:18 1204Test kernel: [   91.422393] unity-panel-ser[2794]: segfault at 20 ip 00007f8a51121b92 sp 00007fff0307ac58 error 4 in libglib-2.0.so.0.3120.0[7f8a510a7000+f2000]
Mar 14 06:27:18 1204Test kernel: [   91.632677] unity-panel-ser[2846]: segfault at 20 ip 00007f875214eb92 sp 00007fff714515d8 error 4 in libglib-2.0.so.0.3120.0[7f87520d4000+f2000]
Mar 14 06:27:18 1204Test kernel: [   91.829938] unity-panel-ser[2856]: segfault at 20 ip 00007f6f82825b92 sp 00007ffff491ab98 error 4 in libglib-2.0.so.0.3120.0[7f6f827ab000+f2000]
Mar 14 06:27:18 1204Test kernel: [   92.022894] unity-panel-ser[2867]: segfault at 20 ip 00007fae5a942b92 sp 00007ffff825bc38 error 4 in libglib-2.0.so.0.3120.0[7fae5a8c8000+f2000]
Mar 14 06:27:19 1204Test kernel: [   92.219962] unity-panel-ser[2877]: segfault at 20 ip 00007f3429e1fb92 sp 00007fff0f75aa28 error 4 in libglib-2.0.so.0.3120.0[7f3429da5000+f2000]
Mar 14 06:27:19 1204Test kernel: [   92.421391] unity-panel-ser[2888]: segfault at 20 ip 00007fc88abc8b92 sp 00007fff45b51238 error 4 in libglib-2.0.so.0.3120.0[7fc88ab4e000+f2000]
Mar 14 06:27:22 1204Test kernel: [   95.909318] show_signal_msg: 16 callbacks suppressed
Mar 14 06:27:22 1204Test kernel: [   95.909325] unity-panel-ser[3192]: segfault at 20 ip 00007f4699ed3b92 sp 00007fff21edb6e8 error 4 in libglib-2.0.so.0.3120.0[7f4699e59000+f2000]
Mar 14 06:27:23 1204Test kernel: [   96.156043] unity-panel-ser[3203]: segfault at 20 ip 00007ff584247b92 sp 00007fff872d4378 error 4 in libglib-2.0.so.0.3120.0[7ff5841cd000+f2000]
Mar 14 06:27:23 1204Test kernel: [   96.413728] unity-panel-ser[3254]: segfault at 20 ip 00007f52b4f89b92 sp 00007fffc24ecbe8 error 4 in libglib-2.0.so.0.3120.0[7f52b4f0f000+f2000]
Mar 14 06:27:23 1204Test kernel: [   96.668628] unity-panel-ser[3264]: segfault at 20 ip 00007f89fa6bbb92 sp 00007fff08fda4f8 error 4 in libglib-2.0.so.0.3120.0[7f89fa641000+f2000]
Mar 14 06:27:23 1204Test kernel: [   96.920771] unity-panel-ser[3275]: segfault at 20 ip 00007fb2e0e29b92 sp 00007fffa0c30038 error 4 in libglib-2.0.so.0.3120.0[7fb2e0daf000+f2000]
Mar 14 06:27:24 1204Test kernel: [   97.168214] unity-panel-ser[3286]: segfault at 20 ip 00007fccd9879b92 sp 00007fff98864708 error 4 in libglib-2.0.so.0.3120.0[7fccd97ff000+f2000]
Mar 14 06:27:24 1204Test kernel: [   97.428588] unity-panel-ser[3296]: segfault at 20 ip 00007fde72bbab92 sp 00007fff28f39c28 error 4 in libglib-2.0.so.0.3120.0[7fde72b40000+f2000]
Mar 14 06:27:24 1204Test kernel: [   97.672213] unity-panel-ser[3350]: segfault at 20 ip 00007fddc9b68b92 sp 00007fff104e5158 error 4 in libglib-2.0.so.0.3120.0[7fddc9aee000+f2000]
Mar 14 06:27:24 1204Test kernel: [   97.916022] unity-panel-ser[3360]: segfault at 20 ip 00007f1aa5e0db92 sp 00007fff552a8aa8 error 4 in libglib-2.0.so.0.3120.0[7f1aa5d93000+f2000]
Mar 14 06:27:25 1204Test kernel: [   98.176268] unity-panel-ser[3370]: segfault at 20 ip 00007fa9ec0a5b92 sp 00007fffa0899f98 error 4 in libglib-2.0.so.0.3120.0[7fa9ec02b000+f2000]
Mar 14 06:27:28 1204Test kernel: [  101.219076] show_signal_msg: 11 callbacks suppressed
Mar 14 06:27:28 1204Test kernel: [  101.219081] unity-panel-ser[3583]: segfault at 20 ip 00007f7607f7db92 sp 00007fff76ff9068 error 4 in libglib-2.0.so.0.3120.0[7f7607f03000+f2000]
Mar 14 06:27:28 1204Test kernel: [  101.478248] unity-panel-ser[3628]: segfault at 20 ip 00007fd9f7161b92 sp 00007fff42950538 error 4 in libglib-2.0.so.0.3120.0[7fd9f70e7000+f2000]
Mar 14 06:27:28 1204Test kernel: [  101.731854] unity-panel-ser[3639]: segfault at 20 ip 00007ff4a47dcb92 sp 00007fffd0166cb8 error 4 in libglib-2.0.so.0.3120.0[7ff4a4762000+f2000]
Mar 14 06:27:28 1204Test kernel: [  101.985858] unity-panel-ser[3650]: segfault at 20 ip 00007f2b45885b92 sp 00007fffed27a5a8 error 4 in libglib-2.0.so.0.3120.0[7f2b4580b000+f2000]
Mar 14 06:27:29 1204Test kernel: [  102.240502] unity-panel-ser[3661]: segfault at 20 ip 00007fea50d0bb92 sp 00007fff9af6b248 error 4 in libglib-2.0.so.0.3120.0[7fea50c91000+f2000]
Mar 14 06:27:29 1204Test kernel: [  102.496074] unity-panel-ser[3677]: segfault at 20 ip 00007f651d450b92 sp 00007fffe5bcd5b8 error 4 in libglib-2.0.so.0.3120.0[7f651d3d6000+f2000]
Mar 14 06:27:29 1204Test kernel: [  102.750412] unity-panel-ser[3723]: segfault at 20 ip 00007faeedc07b92 sp 00007fff4b87b548 error 4 in libglib-2.0.so.0.3120.0[7faeedb8d000+f2000]
Mar 14 06:27:29 1204Test kernel: [  102.991682] unity-panel-ser[3734]: segfault at 20 ip 00007fa4016fab92 sp 00007fffbc13dd78 error 4 in libglib-2.0.so.0.3120.0[7fa401680000+f2000]
Mar 14 06:27:30 1204Test kernel: [  103.242540] unity-panel-ser[3744]: segfault at 20 ip 00007fdb3a253b92 sp 00007fffe8ed1108 error 4 in libglib-2.0.so.0.3120.0[7fdb3a1d9000+f2000]
Mar 14 06:27:30 1204Test kernel: [  103.504617] unity-panel-ser[3755]: segfault at 20 ip 00007f29b848cb92 sp 00007fffb61571c8 error 4 in libglib-2.0.so.0.3120.0[7f29b8412000+f2000]

```

---

### Post by Nick Payne on 2012-03-13
Well after logging off and on a few times, and watching the panel to see when it blanks out, the problem happens at the exact moment that the window for the first application that I start appears. doesn't matter what application that happens to be - Libreoffice, Terminal, Chrome, Nautilus, etc - they all cause it. It Just seems to be the appearance of an app window that triggers the problem.

---

### Post by miguelpires on 2012-03-13
Same problem happen to me. Anyone have made a bug?!

---

### Post by Bowmore on 2012-03-13
It's a global menu issue.

A temporary solution is to remove indicator-appmenu.

The current (new) version of indicator-appmenu 0.3.92-0ubuntu2 that fixed some crashes however doesn't seem to solve this issue that in may case only show up on a 64-bits machine.

---

### Post by Nick Payne on 2012-03-14
> **Bowmore said:**
> It's a global menu issue.

A temporary solution is to remove indicator-appmenu.

The current (new) version of indicator-appmenu 0.3.92-0ubuntu2 that fixed some crashes however doesn't seem to solve this issue that in may case only show up on a 64-bits machine.

It's not that it doesn't fix the issue, it's that it's introduced the issue, which wasn't there before.

---

### Post by Bowmore on 2012-03-14
I'm well aware of that but we're still in development ;)

The issue seems to be a unity panel graphic rework done as it doesn't only affect the indicator-appmenu segfaulting but also some indicators like 
- system load indicator
- weather indicator applet
not to show up correctly.

But still it only seems to be a 64-bit issue here.

---

### Post by mc4man on 2012-03-14
@Nick Payne
have you disabled global menus? (specifically thru that unsettings app

If so then unity-panel-service will segfault as soon as you open an app like nautilus, ect.

Edit: Also happens if you remove the appmenu* packages without removing indicator-appmenu.

---

### Post by VinDSL on 2012-03-14
<< THREADS COMBINED >>

Just did an upgrade, via Synaptic.

Before I applied the upgrades, I read the changes - Unity was in there, as well as app-indicator, and 117 others.

After a restart, the app-indicators (in the panel) blink, flash, appear and reappear in sequence (like a movie marque) then, finally, disappear.

In order to restart, I have to Alt-Ctrl-F1, then Alt-Ctrl-Delete.

Anybody else experiencing this?!?!?!?

---

### Post by ventrical on 2012-03-14
Nothing on this box:

ventrical@Precise-on-600MHzCeleron-with-parts-from-the-recycle-bin:~$ 


but I'll try a bigger machine with Unity 3D.

---

### Post by mc4man on 2012-03-14
All seems well here - you haven't happened to use the Unsettings app to disable global menus?

---

### Post by ventrical on 2012-03-14
I get the unity update but not the app-indicator update.

---

### Post by ventrical on 2012-03-14
Nothing here on the P4 either.

---

### Post by VinDSL on 2012-03-14
> **mc4man said:**
> All seems well here - you haven't happened to use the Unsettings app to disable global menus?
No, they're enabled.  I actually like the global menus.  Heh!  :)

> **ventrical said:**
> Nothing here on the P4 either.

Maybe it was a fluke.

On the last restart it did the same thing, but...

I was going to quickly muck around in cli, before app-indicator crashed, but as soon as I opened a terminal, the craziness went away... almost as if opening the terminal made it stop.

Weird!

Anyway, thanks guys.  I'll see what happens on the next restart...  ;)

---

### Post by screaminj3sus on 2012-03-14
I just installed those updates and am not experiencing that issue.

---

### Post by sammiev on 2012-03-14
All seems fine here on the updates. No problems to report so far.

---

### Post by VinDSL on 2012-03-14
Interesting!

Okay.  Well...

Just happened again, to me.

It must be something specific to my install.

Gonna go a-hunting...  :D

---

### Post by ventrical on 2012-03-14
> **VinDSL said:**
> Interesting!

Okay.  Well...

Just happened again, to me.

It must be something specific to my install.

Gonna go a-hunting...  :D

Gee .. you get all the fun stuff !

:)

---

### Post by VinDSL on 2012-03-14
> **ventrical said:**
> Gee .. you get all the fun stuff !

:)
Heh!  :D

Just checked Synaptic and I see a whole slew of new app-indicator upgrades are waiting (again).

Odd!  Second time in one day.

I'll upgrade to those, and see what happens.  Can't be any worse...  :D

**Edit**

By the numbers...

```
<snip>

Unpacking replacement indicator-appmenu ...
Preparing to replace indicator-application 0.4.92-0ubuntu1 (using .../indicator-application_0.4.93-0ubuntu1_i386.deb) ...
Unpacking replacement indicator-application ...
Preparing to replace indicator-power 1.91-0ubuntu1 (using .../indicator-power_1.92-0ubuntu1_i386.deb) ...
Unpacking replacement indicator-power ...
Preparing to replace indicator-session 0.3.93-0ubuntu1 (using .../indicator-session_0.3.94-0ubuntu1_i386.deb) ...

<snip>

Setting up indicator-appmenu (0.3.94-0ubuntu1) ...
Setting up indicator-application (0.4.93-0ubuntu1) ...
Setting up indicator-power (1.92-0ubuntu1) ...
Setting up indicator-session (0.3.94-0ubuntu1) ...

<snip>
```

---

### Post by VinDSL on 2012-03-14
WooHoo!  I can see it's gonna be one of *those* days~

I did the update, and I was met with a black screen on restart.

Then, after a couple of tries Plymouth came up in VGA mode, along with no networking.

After diddling around in recovery mode for awhile, I got this machine to boot, but XORG was MIA.

At that point, my monitor went blank.  I gave my video card a feel, and it actually blistered my finger... it was so hot.  Heat sink fan wasn't turning.

So, I took my PC out to the garage and blew everything out with compressed air.  GPU fan requires a kickstart now (won't start turning on its own) so it's got one foot in the grave.  Oh, joy!

Anyway, Plymouth is janky now.  No networking, until I get to the desktop.  XORG is back, but app-indicators is still doing its thing.

This time, I watched carefully, and there is a little icon popping in n' out, with a skeleton key on it.  Need to figure out what that (ahem) indicates.  

For some reason, opening up a terminal window makes it go away, and the app-indicators return to normal.

If I let it go, e.g. don't open a terminal window, then the skeleton key icon pops in n' out for a while, and then... all the app-indicators disappear.

Continuing...

---

### Post by VinDSL on 2012-03-15
Traced the app-indicator problem down to the indicator-appmenu upgrade(s).

This did nothing:
```
dpkg: warning: downgrading indicator-appmenu from 0.3.94-0ubuntu1 to 0.3.92-0ubuntu2.
```

This solved the problem(s):
```
dpkg: warning: downgrading indicator-appmenu from 0.3.92-0ubuntu2 to 0.3.1-0ubuntu2.
```

Appears to be a regression.

Network problem (connection timeout) at boot is a separate issue with the most recent network-mangler upgrade.

---

### Post by Nick Payne on 2012-03-15
> **mc4man said:**
> @Nick Payne
have you disabled global menus? (specifically thru that unsettings app

If so then unity-panel-service will segfault as soon as you open an app like nautilus, ect.

Yes, I did disable global menus. With a 30" monitor they're a total pain in the ****. Can't remember how I disabled them, though.

---

### Post by mc4man on 2012-03-15
> **Nick Payne said:**
> Yes, I did disable global menus. With a 30" monitor they're a total pain in the ****. Can't remember how I disabled them, though.

Try opening synaptic, search appmenu
You may have just removed the 1st 3  packages.  appmenu* & the firefox, thunderbird extensions

If so then scroll down a bit & remove 
indicator-appmenu

If you hadn't removed those mentioned packages then just go ahead & remove them all, then log out/in

*all the green marked in screen

---

### Post by screaminj3sus on 2012-03-15
> **VinDSL said:**
> Traced the app-indicator problem down to the indicator-appmenu upgrade(s).

This did nothing:
```
dpkg: warning: downgrading indicator-appmenu from 0.3.94-0ubuntu1 to 0.3.92-0ubuntu2.
```

This solved the problem(s):
```
dpkg: warning: downgrading indicator-appmenu from 0.3.92-0ubuntu2 to 0.3.1-0ubuntu2.
```

Appears to be a regression.

Network problem (connection timeout) at boot is a separate issue with the most recent network-mangler upgrade.
I've somehow never had a single issue with networkmanager, even during alpha/beta testing :)

---

### Post by Jay Car on 2012-03-15
> **VinDSL said:**
> Just did an upgrade, via Synaptic.

Before I applied the upgrades, I read the changes - Unity was in there, as well as app-indicator, and 117 others.

After a restart, the app-indicators (in the panel) blink, flash, appear and reappear in sequence (like a movie marque) then, finally, disappear.

In order to restart, I have to Alt-Ctrl-F1, then Alt-Ctrl-Delete.

Anybody else experiencing this?!?!?!?

Yes, this has been happening to me since updates applied last night - and continue to happen after doing two sets of updates this morning. I've rebooted several times and tried different desktops at login. The problem still happens in Unity 3D, Unity 2D and Gnome Classic. 

The upper right indicators disappear shortly after login, no matter what task I do, then periodically blink on and off, very fast. Then a crash report comes up.  

Also, the strangely scrambled, patchwork screen right after login seems especially bad now.  Until this morning it's only been small patchwork areas that disappeared very fast when the desktop loads. Today that patchwork covers the entire screen and stays several seconds.

Yay!  I have a bug!  How fun! 

I have a doctor's appointment in an hour...I'd rather stay here with the bug...

AMD Phenom(tm) II X6 1090T Processor
16GiB RAM
Gigabyte GA-970A-UD3 Motherboard
EVGA GeForce GT 520 
1024MB DDR3

---

### Post by chenxiaolong on 2012-03-15
A bug report has just been opened on this issue: [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/956061](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/956061) I suggest that anyone who experiences the problem go press the "This bug affects me" button :)

---

### Post by VinDSL on 2012-03-15
> **Jay Car said:**
> Yes, this has been happening to me since updates applied last night [...]

The upper right indicators disappear shortly after login, no matter what task I do, then periodically blink on and off, very fast. Then a crash report comes up.

Yay!  I have a bug!  How fun!
LoL!  It's a very exclusive club, we're in... judging by the posts!  :D

Regarding the crash report, the reason I believe it's a regression is...

When I tried to send in the crash report, it said that it's already been submitted.

I went to launchpad, and there were 8 "me too's" in there, but it was from 2011 and *supposedly* corrected with the release of version *so-and-so* of indicator-appmenu.

Thus, I just kept downgrading indicator-appmenu until it went away.  ;)

---

### Post by cariboo on 2012-03-15
Merged two threads on the same subject.

---

### Post by VinDSL on 2012-03-15
> **chenxiaolong said:**
> A bug report has just been opened on this issue: [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/956061](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/956061)
Thanks!  ;)

Added a "me too" with comment:

> Appears to be a regression. 

When trying to submit a bug report, Apport says it's already been reported (Mar-2011, upon checking launchpad):

[https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/741488](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/741488)

Downgrading to "indicator-appmenu 0.3.1-0ubuntu2" makes the bug go away in Ubu 12.04 Precise 32-bit.

---

### Post by Jay Car on 2012-03-15
> **VinDSL said:**
> LoL!  It's a very exclusive club, we're in... judging by the posts!  :D

Regarding the crash report, the reason I believe it's a regression is...

When I tried to send in the crash report, it said that it's already been submitted.

I went to launchpad, and there were 8 "me too's" in there, but it was from 2011 and *supposedly* corrected with the release of version *so-and-so* of indicator-appmenu.

Thus, I just kept downgrading indicator-appmenu until it went away.  ;)

My crash report also said it had already been submitted. I just now did a "Me Too" on the bug.  I'm doing an update now, hoping that might fix things.  If not, I'll try the downgrading of indicator appmenu. 

[Later] The updates did not help. In fact, after rebooting, The indicators were still blinking and the crash report came up again. Also, the fans on my computer were screaming, sounded like lawn mowers in high grass. My computer always runs very quietly, so this was a little unnerving. Interestingly, the patchwork crazy quilt stuff didn't happen on the reboot. 

One step forward, two steps back.

Just booted into Natty for now, will wait a bit and see what the next updates bring.

---

### Post by repawn on 2012-03-16
Thought I would chime in - this bug affects me as well - add myself to the bug report. Should mention I am running a 32-bit version of Ubuntu and just made the upgrade to 12.04 today. Immediately after logging in the screens is a garbled mess - that goes away and everything looks normal until I click on or run anything - then the panel goes away. I will wait to see what solutions are offered in the next week or so.

---

### Post by snkiz on 2012-03-16
I me 2'd the bug and filed another so my apport logs would get uploaded. I didn't see another way. My indicators disappear right after login on unity and 2D. They don't even show up in gnome classic. wingpanel still works and so does awn. (but that one is gtk2)

I used menuproxy in xsession.d to disable the gobalmenus. idk if thats the cause.

I love how whenever your not using stock Ubuntu settings the bugs get marked "low" priority do they not expect anyone to change their settings?

---

### Post by Jay Car on 2012-03-16
> **snkiz said:**
> I me 2'd the bug and filed another so my apport logs would get uploaded. I didn't see another way. My indicators disappear right after login on unity and 2D. They don't even show up in gnome classic. wingpanel still works and so does awn. (but that one is gtk2)

I used menuproxy in xsession.d to disable the gobalmenus. idk if thats the cause.

I love how whenever your not using stock Ubuntu settings the bugs get marked "low" priority do they not expect anyone to change their settings?

snkiz, I'll agree it was a frustrating thing to happen, but if you do what mc4man suggested in post #22 the problem gets fixed, at least it fixed it for me.

---

### Post by snkiz on 2012-03-16
Meh I use awn and 2d shell so I'm good but I'd imagine that isn't most peoples setup. just trying to help confirm, lend a hand where I can. I know others I've installed for would be affected.

---

### Post by VinDSL on 2012-03-16
I installed/pinned indicator-appmenu 0.3.1-0ubuntu2... working fine.

In the meantime, I'm locked down until someone says the coast is clear.

I noticed there is an app-indicator--all (or whatever) upgrade available today.

Heh!  Personally, I'm not upgrading jack.

Wake me up, when this problem goes away.  :D

---

### Post by VinDSL on 2012-03-22
**_UPDATE_**

Did an *indicator-appmenu* upgrade today, and the problem has not reappeared.

I had a *feeling* that something changed, recently.

My global menus disappeared (using the downgraded indicator-appmenu) a couple of days ago.

Anyway, app-indicators are working without issue & global menus are restored...  ;)

---

