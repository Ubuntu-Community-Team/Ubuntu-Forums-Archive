---
title: "Just Released - system76-driver-2.0.5"
date: 2007-06-21
forum: System76 Support
---

### Post by crichell on 2007-06-21
Hello Everyone,

system76-driver-2.0.5 has just been uploaded to our repositories.  This version includes numerous bug fixes and little enhancements for almost every machine.  I recommend that everyone run the new driver.  After installing the new driver go to System > Administration > System76 Driver.  Click the "Install Drivers" tab and then click "Install".

Change log:

Version 2.0.5

   1. Fix Suspend on all laptops (gazv4 still buggy)
   2. Fix gazv3 suspend Bug #108253
   3. Fix nVidia rotation Bug #118854
   4. Fix Darter Feisty Suspend and LCD Brightness on Resume Bug #114675
   5. Fix network-manager wireless interface recognition after resume
   6. Fix Darter (daru1) FN+F8 monitor switching Bug #116107
   7. Remove build-essential dependency fixing bug #121405 

We need your feedback too.  Many of these bug fixes are tested via fresh installs from our imaging server and customer reports.  If you experience a bug please don't hesitate to report it in launchpad:

[https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by greg_g on 2007-06-21
Quick simple question:

Is there a log of what the driver does?  As in, I updated the driver, ran the "install drivers" bit and all it said was "done, restart your computer..." (not direct quote)  Just wondering if I can see what it did.

But either way, thanks for the great support.

greg

---

### Post by crichell on 2007-06-21
There isn't a log created although that's a good idea.  For many machines Install Drivers is very fast.  Generally it is systems that require custom Alsa support that take a couple minutes.

Info about what the driver does and a complete change log is located here:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

---

### Post by greg_g on 2007-06-21
Mainly I am just wondering if I have to restart my machine (Rat3).  
The only thing in the change log that might pertain to this machine is the nvidia rotation bug.  Went to the bug page and it looks like that will only effect me if I do a Restore since that is only added to the xorg.conf file (and it isn't in my xorg.conf right now after the Install Drivers).

Thanks

---

### Post by crichell on 2007-06-21
> The only thing in the change log that might pertain to this machine is the nvidia rotation bug. Went to the bug page and it looks like that will only effect me if I do a Restore since that is only added to the xorg.conf file (and it isn't in my xorg.conf right now after the Install Drivers).

That's precisely right.  A reboot is not necessary for your machine.  The next major 2.1 release will feature reboot-refinement.  See the blueprint here:

[https://blueprints.launchpad.net/system76-driver/+spec/reboot-refinement](https://blueprints.launchpad.net/system76-driver/+spec/reboot-refinement)

---

### Post by MasterPi on 2007-06-28
I've installed the latest drivers, and I am still having problems with suspend-to-ram with my Pangolin Value (PANV2) running Feisty.  After suspending and resuming (which seems to go fine), the following problems occur:
 - Randomly when I am typing I end up with long strings of one character, as if I had been holding down each key for a while.  Other time-based events seem to be shortened as well, such as my Gaim auto-away going on very quickly (w/in a second sometimes).
 - The system no longer powers down after halting, or during reboot, but instead stalls at the very end of the progress bar (with no orange remaining).  At this point I am forced to hold down the power button until it resets the machine.

Any suggestions?  I've had this system about a year now and I'd really appreciate being able to suspend to ram finally.

---

### Post by kevinlyfellow on 2007-06-28
My Gazp1 still doesn't have functional suspend.  When I first got the machine, it was thought that there was an issue with the bios.  Before I submit a bug on launchpad, where can I check to see if there is a bios update?

---

### Post by thomasaaron on 2007-06-28
kevinlyfellow and MasterPi, are either of you running Kubuntu?

kevinlyfellow, I doubt a BIOS update will affect your Suspend. If everything else is working well on your computer, I'd recommend not updating the BIOS.

Could both of you post the output of the following command:
swapon -s

---

### Post by tedrampart on 2007-06-28
I'm also having problems with suspend (running a gazp3 with the new driver).  

when I return from suspend I have to disable wireless then re-enable it right after to be able to join a network over wireless.  sometimes though, (if I leave the computer on suspend for a few hours) I have to reboot to get wireless working again.  once every 5 resumes, the video doesn't recover and I have to reboot as well.

I only tried hibernate once, and it didn't resume, but I'll try it again.

---

### Post by kevinlyfellow on 2007-06-29
> **thomasaaron said:**
> kevinlyfellow and MasterPi, are either of you running Kubuntu?

kevinlyfellow, I doubt a BIOS update will affect your Suspend. If everything else is working well on your computer, I'd recommend not updating the BIOS.

Could both of you post the output of the following command:
swapon -s

I don't run kubuntu.  And here's the output you wanted

```
$swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       2096472 0       -1

```

Oh, and I'll describe how suspend doesn't work.  It seems to go into suspend ok, but when I bring it out, it acts like its coming back on (hd and cd spin) but the screen stays black.

---

### Post by thomasaaron on 2007-06-29
When you resume from suspend, perhaps the back-light isn't coming back on.
Does anything happen if you press Fn-F4 or Fn-F5 (or whatever brightens the LCD on the Gazelle...)?

If that's the problem, I think we can fix fairly easily.


Regarding the wireless not coming back, there are some solutions on this thread towards the bottom of the page:
[http://ubuntuforums.org/showthread.php?t=425474&page=2](http://ubuntuforums.org/showthread.php?t=425474&page=2)

--ane here---
[http://ubuntuforums.org/showthread.php?t=455006&highlight=wireless](http://ubuntuforums.org/showthread.php?t=455006&highlight=wireless)

---

### Post by kevinlyfellow on 2007-06-29
> **thomasaaron said:**
> When you resume from suspend, perhaps the back-light isn't coming back on.
Does anything happen if you press Fn-F4 or Fn-F5 (or whatever brightens the LCD on the Gazelle...)?

If that's the problem, I think we can fix fairly easily.


Regarding the wireless not coming back, there are some solutions on this thread towards the bottom of the page:
[http://ubuntuforums.org/showthread.php?t=425474&page=2](http://ubuntuforums.org/showthread.php?t=425474&page=2)

--ane here---
[http://ubuntuforums.org/showthread.php?t=455006&highlight=wireless](http://ubuntuforums.org/showthread.php?t=455006&highlight=wireless)

Your right, the backlight does not come back on.  I get no response when I press the lcd controls

---

### Post by tedrampart on 2007-07-01
okay, I'll try that link you sent for wireless..

as far as hibernation, it seems to come back alot more stable, but continues to give me this error.  the battery reports that its in critical, and will shut down, even though its completely charged.  a quick reboot shows that the battery is infact full.  anyone else experience this?  how would I go about fixing this?

---

### Post by MasterPi on 2007-07-01
No, I am not running Kubuntu, and here's the output:
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       3196892 0       -1

I did install suspend2 and that works great for hibernate but I'm still having the same issue with suspend.  I'm thinking it has something to do with the clock or cpu frequency scaling.

---

### Post by steveneddy on 2007-07-01
My SD Card reader works again on my Serval Performance.

Yay!

---

### Post by thomasaaron on 2007-07-02
> I did install suspend2 and that works great for hibernate but I'm still having the same issue with suspend. I'm thinking it has something to do with the clock or cpu frequency scaling.

So, are you having these problems with Suspend2, then? I'm not familiar with that application.

The recent System76 driver was supposed to fix suspend and hibernate functionality with the oem suspend scripts. Do those not work? And will they begin working if you uninstall Suspend2?

---

### Post by MasterPi on 2007-07-02
Hibernate was shaky at best, that's why I tried suspend2, which only deals with suspend-to-disk or hibernate, not suspend-to-ram.  Suspend-to-ram behaves exactly the same as it did before I installed suspend2 (with the current System76 driver), so I have no reason to believe that if I uninstalled it it would make any difference.  I've also tried uswsusp which seems to have the same problems, though it can't detect my machine type and I haven't played with the workarounds just a straight -f switch.

---

