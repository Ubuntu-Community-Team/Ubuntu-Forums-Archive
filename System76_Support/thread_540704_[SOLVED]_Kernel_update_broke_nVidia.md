---
title: "[SOLVED] Kernel update broke nVidia"
date: 2007-09-01
forum: System76 Support
---

### Post by eadwacer on 2007-09-01
Installed the latest kernel update on my new Ratel this morning (1 Sep), and the reboot said there was an API mismatch between nvidia (9755) and Xmodule (9631).  RTFing the forums and associated sites, it looks like the same thing happened last September and last March - with the same numbers.  I changed xorg.conf to use nv and am limping along with some overscan but no major issues.  My n00b question is, will this be fixed in a later update, or do I have to download/install/compile/refactor something?
Steve Shervais

---

### Post by greg_g on 2007-09-01
The latest kernel update didn't mess with my video on my Ratel, but it did mess with my sound system.

After the restart the login screen sound was endlessly repeating.  I logged in and went to the Services list under System->Administration and unchecked ALSA, the sound stop.  Rechecked it, the sound began again endlessly repeating.  I had to do a reboot.  

Then we I rebooted the "PCM" setting was set to mute and I thought it was not working, but I unmuted that and all is good now.

So, I'm thinking the kernel update didn't like Ratels in general.

---

### Post by thomasaaron on 2007-09-04
You gotta love Kernel updates! ](*,)

So, I'm not clear on whether everything is back to normal, or if we need to work out some issues related to the kernel update. Let me know.

Also, there were some issues with other models that were fixed by running the System 76 driver.

Best,
Tom

---

### Post by eadwacer on 2007-09-04
Tom
Have not wanted to do anything rash until I checked.  So I can run the 'install drivers' task from the System76 driver installer ap and that will make it all better (or at least won't do anything harmeful)?
Steve Shervais

---

### Post by thomasaaron on 2007-09-04
Yes, try running the driver. I'd use the restore tab. If you have Beryl installed though, it might mess up your configuration. You'll just have to lay it out again like you want it.

---

### Post by eadwacer on 2007-09-05
Tom
No joy. In fact, made things worse. I ran the Sys76 driver wizard, using the 'restore' tab.  On reboot I get the same API mismatch error when I try to use the nVidia device drivers, and now it can't find "nv" when I edit xorg.conf.  Do you have a quick workaround that will get me some GUI capability while I'm working on the real problem?
Steve Shervais

---

### Post by thomasaaron on 2007-09-05
Try this:

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

Then run:
sudo dpkg-reconfigure xserver-xorg

Use all default settings, except choose "nvidia" as your driver.
If that doesn't get you a GUI, re-run it and choose "nv" as your driver.


Did you,by chance re-installed in the past and downloaded the drivers from nvidia's website? If so, they will probably go down with every kernel update. It's better to use the driver out of the repos. (Yes, I realize I'm assuming, here. I just wanted to put as much info out there as might be relevant).

If that does not work, though, you might want to give me a call so we can expedite this for you. I hate to go back and forth on the forum when you don't even have a GUI!

Best,
Tom

---

### Post by eadwacer on 2007-09-05
Tom
This is a new box, redelivered ten days ago or so (the one with the sound card problem), no reinstalls, no Beryl, just the existing defaults. Fortunately (I never thought I'd say this) I still have my old Win2K box, so I can get online and find stuff out, but all my work is now on the Ratel.  I'll try your suggestions and get back to you asap.
Steve

---

### Post by thomasaaron on 2007-09-05
Oh, I remember that one, Steve.

OK, well, before you do all of that, run...

sudo apt-get update && sudo apt-get --assume-yes dist-upgrade

...just in case Ubuntu has sent something else down that might fix the problem. I think I saw another kernel update.

If it won't boot after that, try the previous suggestions.

Best,
Tom

---

### Post by eadwacer on 2007-09-05
We probably need to talk.  I jumped over to my Ratel and ran your original set of instructions.  
dpkg didn't want to run because xorg.conf had been changed to 'nv', so I changed it back.  Then I didn't see the nVidia choice, because it was off-screen and it wasn't obvious that there were more choices. Anyway, it failed. I tried again, and this time it paused to do a disk check, since I'd rebooted 31 times, then gave me a whole string of "cannot open output file /lib/modules/2.2.20-16-generic...nvidia...ko" and dumped me out without a cursor.  I'm depressed.
Steve

---

### Post by thomasaaron on 2007-09-05
Cheer up. If it weren't for kernel updates, we'd have nothing to look forward to!

Give me a call when you can commit a few minutes to working through this, and we'll get it straightened out.

---

### Post by eadwacer on 2007-09-05
So, I have the rest of the day - it's not like I"m doing any work!  Can you email me a phon number?
Steve

> **thomasaaron said:**
> Cheer up. If it weren't for kernel updates, we'd have nothing to look forward to!

Give me a call when you can commit a few minutes to working through this, and we'll get it straightened out.

---

### Post by eadwacer on 2007-09-07
Well, the advice and hand-holding paid off.  I got Envy, ran it, and all's right with the world.  Thanks to everyone who helped.
Steve Shervais

---

### Post by thomasaaron on 2007-09-07
What a ride!

I'm still curious as to what hosed your nVidia in the first place. I'd think if it had been a kernel upgrade, you wouldn't be the only one I've heard from. And the fixes that should have worked didn't. I'm perplexed. Probably won't sleep tonight either. ](*,)

---

### Post by eadwacer on 2007-09-07
Well, the box did wander around a bit before I took final delivery (and for the assembled lurkers, I should say the wanderings were part of excellent customer service, not ineptitude), and some configuration or other might have gotten changed.  In any event, thanks again, and I think you'll like the latest xkcd:

[Insomnia]("http://www.xkcd.com/313/")

> **thomasaaron said:**
> What a ride!

I'm still curious as to what hosed your nVidia in the first place. I'd think if it had been a kernel upgrade, you wouldn't be the only one I've heard from. And the fixes that should have worked didn't. I'm perplexed. Probably won't sleep tonight either. ](*,)

---

### Post by thomasaaron on 2007-09-07
Yep. 
That's me, alright.

---

### Post by steveneddy on 2007-09-09
> **eadwacer said:**
> Well, the box did wander around a bit before I took final delivery 

I don't understand - did you tweak the box a little before you took it home, or that it traveled many miles on a freight truck. 

Please tell us what you did to the box previous to this incident to have this problem.

---

