---
title: "Anyone still have  graphical issues with the current live image?"
date: 2012-08-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-08-29
Particularly with nvidia display adapters

At least here the current images (last 10 tens or so), will boot up to either a mosaiac or black & white art deco type screen. Occasionally have gotten the live session but flashing on all windows, ect.

Edit: Am referring to booting to a live session or the installer, usb or dvd, not a current 12.10 once installed

Latest 08/29 is in screen
Only asking because it was requested of me to justify saying many users are having issues with the current images in this regard - if it's just me then no big deal..

bug if affected with graphical corruption
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

---

### Post by fjgaude on 2012-08-29
Unity seems to be working fine. It crashes here and there but the GUI is fine, no artifacts, HD3000 Intel.

By Beta1 it should be solid.

---

### Post by mc4man on 2012-08-29
> **fjgaude said:**
> Unity seems to be working fine. It crashes here and there but the GUI is fine, no artifacts, HD3000 Intel.

By Beta1 it should be solid.

Though probably not as obvious as should be I was only referring to booting to a live using the current image & whether others were getting a corrupted screen that would prevent or impede installing...

---

### Post by fjgaude on 2012-08-29
> **mc4man said:**
> Though probably not as obvious as should be I was only referring to booting to a live using the current image & whether others were getting a corrupted screen that would prevent or impede installing...

I have no issues with present installing; a clean 'try now' and no artifacts with today's daily. A normal looking desktop GUI. I installed 12.10 a few days ago without issues onto an SSD; updated, rebooted several times without issue.

Intel graphics seems to be what makes it all so easy.

---

### Post by ventrical on 2012-08-30
> **mc4man said:**
> Particularly with nvidia display adapters

At least here the current images (last 10 tens or so), will boot up to either a mosaiac or black & white art deco type screen. Occasionally have gotten the live session but flashing on all windows, ect.

Edit: Am referring to booting to a live session or the installer, usb or dvd, not a current 12.10 once installed

Latest 08/29 is in screen
Only asking because it was requested of me to justify saying many users are having issues with the current images in this regard - if it's just me then no big deal..

bug if affected with graphical corruption
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

```

downloading from http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.iso:
#################### 100.0% 259.5 kBps DONE      

verifying download...checksum matches OK
used 200814592 local, fetched 583068674
dale@dale:~/Desktop$ 

``` I just zsynced quantal-desktop-i386.iso and I keep getting when booting into a live session with my nVidia setup (GeForce218):

###:### [drm] nouveau: idle channel #

and then it goes to a buggy screen as you described and keeps looping back , trying different buggy screens.
:)

```

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

---

### Post by ventrical on 2012-08-30
> **fjgaude said:**
> I have no issues with present installing; a clean 'try now' and no artifacts with today's daily. A normal looking desktop GUI. I installed 12.10 a few days ago without issues onto an SSD; updated, rebooted several times without issue.

Intel graphics seems to be what makes it all so easy.


mac4man mentioned "particularily with nvidia adapters"

---

### Post by ventrical on 2012-08-30
> **mc4man said:**
> Though probably not as obvious as should be I was only referring to booting to a live using the current image & whether others were getting a corrupted screen that would prevent or impede installing...

At this point it is totally useless. Can't even get terminal. The only thing it can do is shut-down with crtl+alt+del.

*note* On nvidia display adapter.

---

### Post by ventrical on 2012-08-30
> **mc4man said:**
> Particularly with nvidia display adapters

At least here the current images (last 10 tens or so), will boot up to either a mosaiac or black & white art deco type screen. Occasionally have gotten the live session but flashing on all windows, ect.

Edit: Am referring to booting to a live session or the installer, usb or dvd, not a current 12.10 once installed

Latest 08/29 is in screen
Only asking because it was requested of me to justify saying many users are having issues with the current images in this regard - if it's just me then no big deal..

bug if affected with graphical corruption
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

+1 clicky bug!

---

### Post by mc4man on 2012-08-30
> ###:### [drm] nouveau: idle channel #

i did manage to gp to tty3, load X, then load unity. Altough that produced a somewhat 'useable' live session the installer was non-operable.

Looking thru the logs noticed syslog was over 71MB with about 500,000 lines similar to this
> Aug 29 21:03:24 ubuntu kernel: [   31.576278] [drm] nouveau 0000:01:00.0: PFIFO_CACHE_ERROR - Ch 2/2 Mthd 0x0860 Data 0x4d000000

I'd think this would mainly affect nvidia as the screen images are the same as was seen last winter when there was the unity-greeter/lightdm issue.

That was the main reason for mentioning concerning the alt. removal though don't now how widespread this is, last time it started small & then seemed to affect a large number.

Atm the dev's don't think it's much to consider, (& maybe that's true -

Edit - Ventrical - you could try nomodeset option, out of 6 tries it has worked to produce a useable live session  & install  screen twice though haven't yet proceeded with an install
(the other times got a black screen or a flashing window screen once

(As live cd is loading go shift > enter to dismiss language screen > f6 >pick option, also maybe remove splash quiet from the boot options

---

### Post by ventrical on 2012-08-30
> **mc4man said:**
> i did manage to gp to tty3, load X, then load unity. Altough that produced a somewhat 'useable' live session the installer was non-operable.

Looking thru the logs noticed syslog was over 71MB with about 500,000 lines similar to this


I'd think this would mainly affect nvidia as the screen images are the same as was seen last winter when there was the unity-greeter/lightdm issue.

That was the main reason for mentioning concerning the alt. removal though don't now how widespread this is, last time it started small & then seemed to affect a large number.

Atm the dev's don't think it's much to consider, (& maybe that's true -

Edit - Ventrical - you could try nomodeset option, out of 6 tries it has worked to produce a useable live session  & install  screen twice though haven't yet proceeded with an install
(the other times got a black screen or a flashing window screen once

(As live cd is loading go shift > enter to dismiss language screen > f6 >pick option, also maybe remove splash quiet from the boot options

kernel panic - locked right up .. lights blinking on keyboard, etc...

 I am going to try it on an older nvidia.

*edit*Worked on the older nVidia but no Unity .. just Warty with an apport msg saying internal error .. etc..

 Was able to get to terminal . That tower runs with alternate ok with the llvmpipe and Unity3D although painfully slow.

---

### Post by t1497f35 on 2012-08-30
> **ventrical said:**
> kernel panic - locked right up .. lights blinking on keyboard, etc...

 I am going to try it on an older nvidia.

*edit*Worked on the older nVidia but no Unity .. just Warty with an apport msg saying internal error .. etc..

 Was able to get to terminal . That tower runs with alternate ok with the llvmpipe and Unity3D although painfully slow.

I also get a hard system lock up with my GeForce 560 Ti while trying to boot into the live CD to install it. But with my older GeForce 7600 GT anything's fine.

So I install the system with 7600GT, install the nvidia blob (nvidia-current), shutdown, switch back to 560 Ti and it boots fine now. So I guess it's a nouveau issue.

---

### Post by grahammechanical on 2012-08-30
Date: 2012/08/30 or 30/08/2012. Time: 12.30 UTC or 13.30 British Summer Time. And yes, we are expecting rain.

Just run some Live CD tests on ISO image downloaded on 29/08/2012. Here are the results.

Test 1) At 1st purple screen with keyboard and accessibility image allow the live CD to self load.

Result: Get 2nd purple screen with Ubuntu word and 5 dots. This leads on to a corrupted graphics screen due to a failure to flush some video buffer in the video adapter which is Nvidia GT220 which the Details page sees as GT 216 0682vb12. There is no desktop background screen, no Launcher, no top panel, no keyboard response and mouse is inactive.

Test 2) At 1st purple screen press Enter to get the language selector screen, then press Enter to select English as the language, then press enter to select Try Ubuntu without installing as the option.

Result: Get 2nd purple screen with the Ubuntu word and the 5 dots. This leads on to corrupted graphics and does not lead to background image but the Launcher and the top panel do appear but are next to impossible to use because the mouse is not active and keyboard functions are limited and using alt+F10 is difficult because only a ghostly outline of the menu box appears without ant text.

Test 3) At 1st purple screen press Enter to get the language selector screen. then press Enter to select English as the language, then press F6 and select the nomodeset option, then press Esc, then press Try Ubuntu.

Result: Get the 2nd purple screen with the Ubuntu word and 4 dots. The text is in a thinner font than in test 1. This leads to a black screen, which in turn leads to the default Ubuntu background image with the Launcher and the top panel and a working mouse and keyboard.

As a side issue the Ubuntu Software Centre immediately closes unexpectedly.

The Shutdown option leads to a black screen with the word Ubuntu 12.10. The DVD tray does open when shutdown is complete and we are invited to remove the DVD and press enter.

I hope this helps to convince the unbelievers.

I can install using nomodeset with this ISO image. I do not pull in third party software so I do not get the Nvidia driver. Nouveau works fine on my machine. I get 3D graphics. I am just a little bit disappointed the CCSM no longer gives Wobbly Windows. And there is not an email client by default anyone.

Regards.

---

### Post by P-I H on 2012-08-30
I haven't used the live cd since I installed Alpha 3 and with the Live CD I must always use nomodeset. 
My test system with a Geforce GTS250 card only works OK with the proprietary Nvidia driver, and I haven't been able to use the system for some week, but now it is OK since I installed the 304.43 driver.

With the nouveau driver I get the "Failed to Idle Channel #" problem mentioned by ventrical. There is an old bug report about something similar: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/610251](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/610251)

The Vesa driver works to some extend, with reduced resolution, when I boot in recovery mode. This makes it possible to install the proprietary driver using a GUI.

---

### Post by jerrylamos on 2012-08-30
Graphical issues?  Sure.  Now mind you, I'm booting .iso off the hard disk so "live image" is appropo, not CD.
 
The 1366x768 TV screen comes up with 800x600 on the live image.  Usable.  I could do monitor settings if I wanted to take the time.

The install and examples icons are flaky, appearing, disappearing, maybe just slices of the icon, but I could get install opened.  Usable not what they'd want to ship.

Some other screens are flaky example when setting manual partitions the drop down menus appear, disappear, might be partly blanked out, but I can fight through it.  Usable for Alpha not what they'd want to ship.

---

### Post by 3vi1 on 2012-08-31
Attn 560 (and other GF114 card) users with nouveau hangs, I previously opened this bug: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637)

So, users of those cards will have to stick with the newer nVidia blobs for now.

Now, unrelated, but still on the topic of graphical issues, I have noticed new problems on my CR-48 (Intel graphics).  Compiz flickers, particularly where conky and the Unity launcher should appear, and shows the background color (instead of the wallpaper).  This just started about three days ago.  I haven't played with the system enough to try to determine the cause.

---

### Post by kansasnoob on 2012-08-31
VIA openchrome is a total no-go even in Lubuntu:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/1041625)

---

### Post by ventrical on 2012-08-31
> **3vi1 said:**
> Attn 560 (and other GF114 card) users with nouveau hangs, I previously opened this bug: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041637)

So, users of those cards will have to stick with the newer nVidia blobs for now.

Now, unrelated, but still on the topic of graphical issues, I have noticed new problems on my CR-48 (Intel graphics).  Compiz flickers, particularly where conky and the Unity launcher should appear, and shows the background color (instead of the wallpaper).  This just started about three days ago.  I haven't played with the system enough to try to determine the cause.

 I had just went through this and Bowmore had the fix.

[http://ubuntuforums.org/showthread.php?t=2050365](http://ubuntuforums.org/showthread.php?t=2050365)

---

### Post by 3vi1 on 2012-08-31
> **ventrical said:**
> I had just went through this and Bowmore had the fix.

[http://ubuntuforums.org/showthread.php?t=2050365](http://ubuntuforums.org/showthread.php?t=2050365)

Yep, that's almost certainly it... I recall some mesa updates around the timeframe I first noticed the issue.

I'll probably leave it like it is for now, until they upload a newer mesa - since I hardly use that machine for anything except listening to podcasts.

But, I'm glad it's not just me.  I marked the bug as affecting me too.  Thanks for the info!

---

### Post by zeusk on 2012-09-03
I have wierd graphical corruption in unity too, mouse pointer doesn't show up, desktop and windows are badly corrupted however the unity launcher itself looks fine and works fine.

Adapter is Nvidia 9600GT (G94), it worked well with a few builds after alpha 3 (Though it was still unstable) but is broken since then.

---

### Post by martijntje on 2012-09-04
I only get garbled displays. This is with an nVidia 560. On the alpha 3 iso it just shows one bad screen and sticks to it, while the latest daily will show me a variety of different garbled screens.

Too bad the alternate CD is no more... :(

---

### Post by mgmiller on 2012-09-04
I tired an alpha 3 live install on a 4 GB thumb drive and it works perfectly on my Intel HD graphics laptop, as well as my ATI tower.  However, My tower with Nvidia 550ti is a complete no go.  The OP perfectly described the appearance of my screen.  I did try to boot with nomodeset, and that got me to a "usable" desktop, but it did not suggest or show the nvidia binary drivers in the update drivers area.  I installed them with the software center, but on reboot, it still does not work.  ](*,)My mobo has an older built in Nvidia card that I could try booting off of, and then install the binary blob again, but I will probably just wait till the beta comes out and then try again.  I usually don't spend too much time with the alphas.  Although, I must say on my Intel notebook (Lenovo 400T) it worked great.  Very smooth full screen videos, etc.

---

### Post by nm_geo on 2012-09-04
I have a Lenovo T61p with the following nVIDIA Quadro FX 570M graphics. I do get the graphics mess when trying to run the Live CD session.  However,  if I choose nomodeset I can get around it.  Another option that works for me and gets me to a live session is to do Ctrl-Alt-t right after plymouth starts.  You know where the screen with the moving lights starts.

---

### Post by mc4man on 2012-09-04
May as well mark as solved - 
It seems some nvidia hardware will get the corrupted screens, some won't
Sometimes just going shift > enter on lang, enter on either 'try me' or 'install' works, other times you need to choose the nomodeset option
(both of the above can work here with the very same usb boot disk on same laptop though more often than not I need nomodeset

Why this is now occurring no clue, something around Aug. 15-17 brought on. May be specific to *buntu though atm very few live iso similar enough to compare.
(no issue on fedora 18 nightly, the Alpha next week or so may be a closer compare.

---

### Post by zeusk on 2012-09-05
But is the bug notified ? The only reported ones i see in launchpad are regarding ATI or Intel 4000 Adapters.

---

### Post by dmbaker on 2012-09-12
My graphical issue is that I don't have any icons at all to click after I log in.  I move the mouse around the page but no icons appear at all.  Just a beautiful blank page.  Has anyone else experienced that issue?

---

### Post by sgage on 2012-09-12
As of the daily build of 9/9, I still get a scrambled screen upon booting the LiveCD. On a whim, I hit 'enter', and the live desktop came up perfectly, and everything worked great from there. 

I run an Nvidia GeForce 8500 GT.

Also, nvidia-current is running fine for me now - even allows virtual terminals, which it hasn't for months...

---

### Post by amikot on 2012-09-12
On Kubuntu 12.10 daily build (11 Sep 2012) i still have freeze (with trashed screen) when booting with liveCD.

On my desktop with Kubuntu upgraded from 12.04 to 12.10 i have freeze when playing 3D games. Its looks that`s only NVidia driver problem. When using nouveau everything looks stable.

PS. I have GF8600GTS

---

### Post by philinux on 2012-09-13
nVidia 8600GT

Booting starts. I get an error about video mode. Space to continue or scan produce same results. Plymouth looks great in correct resolution then garbage desktop. Multicoloured pixels. Launcher is there as it top panel but no mouse pointer but mouse is there.

Rebooting and using nomodeset works and desktop appears but is very sluggish and compiz crashes. 

I would not install using this. :rolleyes:

I've marked this as unsolved for now.

---

### Post by mc4man on 2012-09-13
> **philinux said:**
> nVidia 8600GT

Booting starts. I get an error about video mode. Space to continue or scan produce same results. Plymouth looks great in correct resolution then garbage desktop. Multicoloured pixels. Launcher is there as it top panel but no mouse pointer but mouse is there.

Rebooting and using nomodeset works and desktop appears but is very sluggish and compiz crashes. 

I would not install using this. :rolleyes:

I've marked this as unsolved for now.
Exact as seen here yesterday on new install. The current state seems to be that doing an install is possible but the live session is barely usable.
If people where to use the live session to judge whether to install or not can't see any of them proceeding.

(- I marked solved as to the question not to the problem which seems to be getting worse.
Basic bug on that's gone a bit stagnate 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

---

### Post by philinux on 2012-09-13
I've me too'd and posted in bug report as per my post above.

---

### Post by mc4man on 2012-09-13
The new 'undefined ...' affects all hardware, 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049650](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049650)

---

### Post by philinux on 2012-09-13
> **mc4man said:**
> Exact as seen here yesterday on new install. The current state seems to be that doing an install is possible but the live session is barely usable.
If people where to use the live session to judge whether to install or not can't see any of them proceeding.

(- I marked solved as to the question not to the problem which seems to be getting worse.
Basic bug on that's gone a bit stagnate 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1043518)

Can you ssh into the busted livecd session and grab the x server logs?

Or get to tty and grab them

---

### Post by mc4man on 2012-09-13
> **philinux said:**
> Can you ssh into the busted livecd session and grab the x server logs?

Or get to tty and grab them
Maybe tonight..
I had saved them on prior install but the info was never requested.

That bug was initally a response to my post last month to the mailing list about removing the alt. installer
I claimed that many users would find the live cd unusable or close to for installing
(at least here at that time that was the case, even nomodeset was only working some of the time.

So they asked for any bugs on, didn't see any so filed one.

Since then nomodeset seems to do the job as far as installing, though the live session has gone from bad to worse.
So in some regards possibly the bug should be re-titled/described..., currently the 2 issues are
Users need to know about using nomodeset & how to.
The live session is potentially bad enough to discourage users from doing an install if they think it's reflective of a 12.10 install

---

### Post by philinux on 2012-09-13
I tried to copy the xsession-errors file to my usb stick and it totally corrupted the device.

---

### Post by mc4man on 2012-09-13
I forget exactly what I did to get all the relevant logs when booting up without nomodeset. (went to a tty, ect.)
 Another reason I didn't  attach was the size of at least one was huge > 70MiB, mentioned in report

I'm sure they are aware & not too sure there is much concern about the viability of the live session for nvidia (or only some nvidia??

Previously in nomodeset you'd get unity-2d, now what you get is ??, if it's that lvmpipe then very non impressive, at least in a live session
(if I had to use it instead of nvidia/nouveau then myself probably wouldn't even bother to use 12.10/compiz

---

### Post by philinux on 2012-09-13
According to the guys in ubuntu+1 irc it's not just nVidia that has screen corruption.

---

### Post by mc4man on 2012-09-13
> **philinux said:**
> According to the guys in ubuntu+1 irc it's not just nVidia that has screen corruption.
That's a good deal then, more reason to address other then release notes

I've tried the recent fedora 18 nightly images which are similar to ubuntu in some regards, no issue at all.  though maybe the alpha or later would be closer

Edit: this was a semi-relevant response to my initial ml post

> Searching for "Live" against
xserver-xorg-video-nouveau shows a couple dozen bugs in this class filed
over the past several releases.  #1040495 and #1037915 are examples.
There's probably a bunch filed against the kernel and other X components
too.  So, it's definitely a legitimate issue.  But it's less common than
Doug suggests.

However, while the alternative CD is one way to work around these kinds
of issues it's not the only way.  For instance, in those bugs the users
used "nomodeset" to work around it.  Obviously, few users will know to
try that, but even so I don't think this is very strong justification
for keeping the alternative CD.  Time would be better spent a) making
the kernel parameter workarounds more obvious to users, and especially
b) solving the actual bugs.


One complication we should consider is that when a user *can't* boot the
CD on their system for whatever reason, filing a bug report about it
becomes *very* hard.  Since they can't boot, they can't invoke
ubuntu-bug to file a bug with auto-collected log files.  They can't
manually collect log files either.  They probably have no idea what
package to file the bug against, and maybe don't even know where to go
to file it (challenge: try getting to the +filebug page from
ubuntu.com).  Chances are high that a lot of these problems are just not
getting reported, at least not through the channels we expect.

Bryce

---

### Post by mc4man on 2012-09-15
at least here the issue with the live cd's seems to be the "splash" boot option.
If I remove it then booting to the live session works fine, nomodeset is not needed.

Also noticed that if trying to boot to an earlier kernel from grub - 
With the default options most times the unity-greeter is corrupted & unuseable
Again removing splash fixes that

(On the live cd I don't see the complete boot line - it ends on the screen with splash --
I assume -- was to the vt7 option, if I saw it would likely remove that too.. but because I can't I leave -- there

---

### Post by mc4man on 2012-09-28
For many nvidia cards affected by this it's been resolved with a kernel patch & in  3.5.0-16.24
"* drm/nouveau: fix booting with plymouth + dumb support"

Once that is included in the daily image the issue should be fixed

Tested here by re-mastering todays image & replacing the kernel, live session booted up with no issue/corruption at all

(the new kernel should also help some ati cards similarly affected

---

### Post by Jonathan D'Orleans on 2012-09-28
Just to confirm I have the same problem with: NVidia GTX 560M and a friend of mine too with: NVidia GT 525M.

Hope it can be fixed to the final version.

---

### Post by mc4man on 2012-09-29
> **Jonathan D'Orleans said:**
> Just to confirm I have the same problem with: NVidia GTX 560M and a friend of mine too with: NVidia GT 525M.

Hope it can be fixed to the final version.
Should be ok starting with the current images of today (09/29), at least for nvidia hardware affected by the plymouth splash induced corruption

---

### Post by darinmiller on 2012-09-29
Hopefully this is not a repeat of a previous post as I did not read all of them...

Another workaround is to hit ```
ctr-Alt-F2
```to exit to a prompt, then type ```
startx
```

This will boot the live desktop.  However, I have yet to figure how initiate install as the message "ubiquity is already running" appears when trying to run "ubiquity kde_ui" from the command line...

---

### Post by philinux on 2012-10-02
nVidia 8600GT - burnt daily live today and it's boots fine. No graphics issues at all.

---

### Post by sgage on 2012-10-02
> **philinux said:**
> nVidia 8600GT - burnt daily live today and it's boots fine. No graphics issues at all.

Working fine for me now, too. 8500GT.

---

### Post by amikot on 2012-10-06
After many hangs on 12.10 i goes back to 12.04 (64bit) and used it with no problem until installed Nvidia drivers 3xx.xx 
Now on 12.04 i have the same issues that on 12.10 - hangs when  playing 3d games.

Now I'm not so sure that livecd hangs are related to my problems - it looks that livecd problems are cosed by kernel, and my problems are caused by nvidia latest drivers.

---

### Post by BigSilly on 2012-10-06
> **philinux said:**
> nVidia 8600GT - burnt daily live today and it's boots fine. No graphics issues at all.

Thanks for this. I had no idea they'd solved the issue. However, I'm finding the live session via USB extremely slow. Is this normal at the moment? The last daily build I used was incredibly fast. Thanks.

---

### Post by philinux on 2012-10-06
> **BigSilly said:**
> Thanks for this. I had no idea they'd solved the issue. However, I'm finding the live session via USB extremely slow. Is this normal at the moment? The last daily build I used was incredibly fast. Thanks.


The one I tested was fairly responsive. With persistence enabled it takes much longer to boot.

---

### Post by BigSilly on 2012-10-06
> **philinux said:**
> The one I tested was fairly responsive. With persistence enabled it takes much longer to boot.

Ah, it could be that then. I did have persistence enabled. Thanks again.

---

