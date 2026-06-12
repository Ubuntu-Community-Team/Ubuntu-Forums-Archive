---
title: "PanP5 Power Management hopelessly broken"
date: 2009-10-14
forum: System76 Support
---

### Post by HotShotDJ on 2009-10-14
There are several issues with power management on my PanP5 in both Jaunty and Karmic -- but I'll focus on Jaunty since Karmic is not (yet) supported:

1)  Cannot properly detect Battery vs. AC power

This is a rather strange one, since the screen will dim and the power-manager icon will change when I unplug the AC adapter.  Plugging back in will brighten the screen and the icon will change back.  But that is the extent of power management.  The system is unable to calculate time remaining on the battery, and the nvidia x-server settings / powermizer information screen states that the system is on battery power, but behaves has if it is on AC power.

These issues are related to ACPI AC being compiled into the kernel.  I compiled a custom kernel based on the standard 2.6.28-15-generic (AMD64) Jaunty kernel with ACPI AC compiled as a module.  This fixed the above issues and, very interestingly, enabled some pretty aggressive power management settings when on battery power.  VERY cool stuff! Unfortunately, my skills at custom compiling kernels for Ubuntu are almost non-existent, and I also introduced other problems related (I think) to initramfs and dkms.

This problem continues to exist in Karmic (Beta) with the 2.6.31-14 kernel.

2) CPU Frequency locked at 800 MHz when resume from suspend.

This problem exists in Jaunty and persists in Karmic (Beta) with the 2.6.31-14 kernel --  I also tested it with previous Karmic kernels (2.6.31-11 and 2.6.31-13).  I honestly have no idea where to begin to debug this one.  Extensive searching (in forums as well as Google) provided no insight for me.


EDIT:  I didn't like the negativity of my original thread title.  Fixed (sort of).

EDIT2:  Working on a fix for #1 -- if it works with Jaunty, will test in Karmic too (involves a recompile using various tools.. this looks promising.)

---

### Post by thomasaaron on 2009-10-14
We've heard that this would be fixed in Karmic, so we haven't put a lot of work into finding the fix. We're not really in the kernel compiling business. But if it doesn't get straightened out for Karmic, then we just might have to go that route. It seems *fixable* though, so that's a good thing.

---

### Post by HotShotDJ on 2009-10-14
> **thomasaaron said:**
> It seems *fixable* though, so that's a good thing.I gave up with Jaunty, but was successful in Karmic.  Although the power management in Karmic is crippled, a simple recompile of the stock kernel (using a modified version of [THIS]("http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/") howto) is working, or I should say, hasn't broken anything that I've noticed.

NVidia Settings now can detect AC vs Battery.  An AC icon now shows up in the Power Statistics.  CPU Frequency is throttled back on Battery Power to maximum of 1.63 and returns to normal when I plug the AC adapter back in. Now I'll see if I've improved my battery run time.  I'll post back. :)

EDIT:  Still testing, but so far, no problems that I can attribute to the customized kernel.  In fact, very few problems that I can even attribute to running a Beta level OS. ;)

Tom:  Let me know if you'd like me to send you the kernel I compiled for you to test (linux-headers-2.6.31-14-system76_2.6.31-14.46_amd64.deb & linux-image-2.6.31-14-system76_2.6.31-14.46_amd64.deb).  I'll pull new sources from git when a new kernel appears in karmic updates.

---

### Post by thomasaaron on 2009-10-15
OK, thanks. I'm passing all of that info to the appropriate folks. I'm sure they won't want to move on it until all is finished with Karmic testing.

---

### Post by HotShotDJ on 2009-10-15
> **thomasaaron said:**
> I'm sure they won't want to move on it until all is finished with Karmic testing.That's quite sensible.  With a little luck, everything will work "out of the box" with Karmic final, leaving everything that I did as simply a learning exercise. :)

---

### Post by HotShotDJ on 2009-10-16
UPDATE:  It looks like things are getting sorted in the standard kernel with Karmic.  I wish I could just delete this thread and pretend I never started it. :)  On the up-side... I learned a lot about how do create custom kernels for Ubuntu.

---

### Post by justin.waters on 2009-10-29
I'm still having issues with CPU frequency scaling after suspend when using Karmic on my panp5.  When I return from suspend, the CPU will never go higher than 800 MHZ, unless I set the CPU governor to "Performance".  Then, it will never drop below full speed.  I had the same problem in Jaunty.

On the plus side, everything else seems to be working great!  Especially the whole battery/AC detection issue.

---

### Post by val67 on 2009-10-30
> **justin.waters said:**
> I'm still having issues with CPU frequency scaling after suspend when using Karmic on my panp5.  When I return from suspend, the CPU will never go higher than 800 MHZ, unless I set the CPU governor to "Performance".  Then, it will never drop below full speed.  I had the same problem in Jaunty.

On the plus side, everything else seems to be working great!  Especially the whole battery/AC detection issue.

Thomas, can you confirm if this problems occurs on the latest Pangolin as well? (P6)

Thanks.

---

### Post by HotShotDJ on 2009-10-30
> **justin.waters said:**
> I'm still having issues with CPU frequency scaling after suspend when using Karmic on my panp5.  When I return from suspend, the CPU will never go higher than 800 MHZ, unless I set the CPU governor to "Performance".  Then, it will never drop below full speed.  I had the same problem in Jaunty.I can confirm this on my system as well.  Additionally, when it wakes from suspend, screen brightness is set all the way down, even when plugged in.  Brightness is returned to normal using Fn + F9 key-presses.
> **justin.waters said:**
> On the plus side, everything else seems to be working great!  Especially the whole battery/AC detection issue.Since I did a complete reinstall yesterday evening (so I could make sure I got rid of any self-inflicted bugs from my Karmic Beta & RC experimentations), I haven't had time to do a lot of testing of the rest of power management.  However, I can confirm that "Power Statistics" does not seem to "see" the ac power adapter, nor does nvidia-settings.  Also, I am unable to get discharge rates or charge rates.  However, it appears that as long as "use_time_for_policy" under gnome-power-manager is disabled (for proper low battery warning and proper action when critical), this is purely a cosmetic issue.

---

### Post by val67 on 2009-10-30
Still haven't found out if PanP6 has the same power mgmt issues..

Anybody?

---

### Post by HotShotDJ on 2009-10-30
> **val67 said:**
> Still haven't found out if PanP6 has the same power mgmt issues..Be patient, val67 (I know, easier said than done ;)).  The folks at System76 have been working on getting the drivers out in time for Karmic.  Additionally, the problems that are being discussed in this thread are rather old regressions that started with Jaunty and  now, to everybody's surprise, persist in Karmic.  Give Tom a little bit of time (a few days should do it.. LOL) to catch his breath.  They didn't do much with this bug because they were under the impression that it was being corrected in Karmic.  Tom has said in a previous thread that they will begin work on it if it persists.  So I believe we can expect some new information soon.

I'd like to also point out that the problem with Battery and AC power seems to be effecting other laptop brands as well (see [Bug #444881]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/444881")).  I strongly suggest that people experiencing that issue also place a comment in that bug report.

I'm thinking that we should probably let this thread die the death it deserves (I'm still embarrassed by the Title I gave this thread in a moment of frustration) and begin new threads for these two issues.  But that's just my 2 cents.

---

