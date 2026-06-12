---
title: "Dim Screen after upgrade to Hardy"
date: 2008-05-12
forum: System76 Support
---

### Post by MarkID on 2008-05-12
Finally upgraded to Hardy.  For the most part, went smoothly.  But the screen is very dim, like the backlight is off.  How to I adjust creen brightness?  Daru1

---

### Post by MarkID on 2008-05-12
OK.  Problem solved, but kinda counterintuitive.  Suspend still  problem.  Will advise.

---

### Post by TomLawell on 2008-05-13
I had same problem while still using the 302 firmware. Upgrade to 305 allow the Fn f5 f6 keys to aid brightness control. 
Did your wireless break?
I still can not connect to my secured or unsecured Belkin PreN. I can connect with three other Win laptops and my daru1 worked until the reboot after 8.04 upgrade!

TomL

---

### Post by thomasaaron on 2008-05-13
For instructions on upgrading your firmware, please contact me at support(at)system76(dot)com.

---

### Post by MarkID on 2008-05-13
> **MarkID said:**
> OK.  Problem solved, but kinda counterintuitive.  Suspend still  problem.  Will advise.

Not completely solved.

What I did, while squinting at the dim screen, was to add the brightness control to my panel, and use that.  But when I reboot (which is necessary too often since suspend doesn't work) the screen is dim again, and I must reset using the brightness control.  If there is a better solution, let me know please.  However, wireless is working AOK.

---

### Post by thomasaaron on 2008-05-13
If you would like for me to create a start-up script that will set your computer to full-brightness on boot-up as a default, contact me at support.

At the moment, that is about the only way I know to fix it. You could remove the start-up script later down the road when a fix comes down through Ubuntu.

---

### Post by pp77 on 2008-05-13
I solved a similar problem by installing xbacklight and putting it on startup programs in sessions preferences with xbacklight -set 100 (the value is up to you).

---

### Post by ctsdownloads on 2008-05-13
> **pp77 said:**
> I solved a similar problem by installing xbacklight and putting it on startup programs in sessions preferences with xbacklight -set 100 (the value is up to you).

This is a good idea, I will have to see if this works on my notebook as well. :)

---

### Post by riseringseeker on 2008-05-27
Having the same trouble with my trusty (white) Darter Ultra.  For now have used pp77's idea of having xbacklight at start, it's better than nothing, but does not help when switching users, or when coming out of screensaver.  It *sometimes* is normal brightness when it comes to the progress bar, never when the login window shows up.  It also is sometimes dim on the bar during shutdown.

I guess there is at least one bug report on it already, at least I see a few, though none have my exact problems.  I only have one other problem (knock on wood) since I installed Hardy (64), but that will be the subject of another post.

Tom, I know you run a daru1, have you installed Hardy, and do you see the same problem?

---

### Post by thomasaaron on 2008-05-27
No, neither Carl nor I have this problem. We have seen other DarU1 that have it, though. It definitely doesn't affect all of us. Unfortunately, we've been unable to reproduce it in house.

Does that xbacklight program use a config file in your home directory? If so, I wonder if it would work if you copied that file into your other home directories (for different users).

With coming out of suspend, we might be able to put a script in the resume.d directory that would help.

What BIOS version are you running?

---

### Post by riseringseeker on 2008-05-27
> **thomasaaron said:**
> No, neither Carl nor I have this problem. We have seen other DarU1 that have it, though. It definitely doesn't affect all of us. Unfortunately, we've been unable to reproduce it in house.

Does that xbacklight program use a config file in your home directory? If so, I wonder if it would work if you copied that file into your other home directories (for different users).

With coming out of suspend, we might be able to put a script in the resume.d directory that would help.

What BIOS version are you running?

I have the xbacklight run as a startup program in both user accounts (System -> Preferences -> Sessions -> Startup Programs).  It does not brighten when switching users, it always defaults to the lowest setting, nor does it come up bright for either user when coming out of screensaver mode.  When switching, or coming out of screensaver though the screen comes up to full bright as soon as I hit FnF5, no gradual increase, just pop.

I have seen others complain about this, using non-`76 computers, so I doubt that it is a `76 *only* problem.

More often than not it will be normal brightness at start, going into grub and during the progress bar loading (but not always).  It is *always* dim at the login window.  Before I added the xbacklight trick, it would not allow FnF5 until the desktop finished loading.

As far as the BIOS, I have done at least one update of it, using a guide you sent me.  I guess I would have to reboot to find out, which I will as soon as I gather info for another problem I am having.

---

### Post by riseringseeker on 2008-05-27
> **thomasaaron said:**
> No, neither Carl nor I have this problem. 

Not picking on you Tom, but it seems Carl *is* having something of the same problem.  I haven't setup a virtual machine yet, but this sounds a lot like what I am seeing:

[https://bugs.launchpad.net/system76/+bug/228294/comments/2](https://bugs.launchpad.net/system76/+bug/228294/comments/2)

---

### Post by thomasaaron on 2008-05-27
I stand corrected. I think. He has two DarU1 lappies.

---

### Post by riseringseeker on 2008-05-30
[QUOTE=thomasaaron;5056390
What BIOS version are you running?[/QUOTE]

Sorry it took me this long to answer the question.  Looking at the BIOS, it says:

BIOS Version         305
VGA BIOS Version     1256.I06107.006

and at the bottom it says it's version 02.59 copyright (blah blah) Megatrends.

---

### Post by thomasaaron on 2008-05-30
Well, that is the correct BIOS version.

Our sales manager today figured out that there may be some minor differences between installing Hardy Beta and upgrading and installing Hardy Alpha and upgrading. Theoretically, that should not be the case. But, in reality...

In other words, you don't end up with the exact same product in the end. I'll spare you the boring details, since his experiment wasn't on a Darter anyway.

I'm starting to wonder if this problem is related to how people upgraded: online vs. CD vs. Fresh install with Beta vs. Fresh install with Alpha, blah blah blah.

If those still watching this post could sound off with 1) How you upgraded and 2) Do you have the dimming problem.

I'll be re-imaging my Darter again this weekend with the current Hardy image.

---

### Post by beuno on 2008-05-31
I upgraded to the first hardy beta from Gutsy, and have the "dimming problem".

---

### Post by riseringseeker on 2008-05-31
> **thomasaaron said:**
> Well, that is the correct BIOS version.

That's good to know.

> Our sales manager today figured out that there may be some minor differences between installing Hardy Beta and upgrading and installing Hardy Alpha and upgrading. Theoretically, that should not be the case. But, in reality...

In other words, you don't end up with the exact same product in the end. I'll spare you the boring details, since his experiment wasn't on a Darter anyway.

I'm starting to wonder if this problem is related to how people upgraded: online vs. CD vs. Fresh install with Beta vs. Fresh install with Alpha, blah blah blah.

If those still watching this post could sound off with 1) How you upgraded and 2) Do you have the dimming problem.

I'll be re-imaging my Darter again this weekend with the current Hardy image.

Complete fresh install well after the final release was put out.  Backed up my 7.10 install and installed clean.   (Chance to do housekeeping).  It was dim on first boot, and after restoring System76 driver (and ever since).

I then pulled in documents, music, photos and bookmarks/passwords off the backup.  I did not import any desktop setting or anything like that, as I changed from 32 bit to 64 bit and was worried about compatibility.

It was dim with the install disk (both 32 and 64 bit), until it got to the desktop, as I mentioned on the phone.  Was hoping it was an install disk problem, and/or it would be promptly fixed.

---

### Post by riseringseeker on 2008-06-03
Tom;

Just wondered, do you know if this problem also exists when 8.04 is installed from the alternate CD?

I will have about 3 days to kill in Hong Kong later in the week, and am willing to try a re-install if you think that may be the culprit.

---

### Post by beuno on 2008-06-03
If it helps, I **did** install Gutsy from the alternate CD, so I could install with an encrypted hard drive.

---

### Post by riseringseeker on 2008-06-05
> **beuno said:**
> If it helps, I **did** install Gutsy from the alternate CD, so I could install with an encrypted hard drive.

Well then I guess I won't bother, was hoping something would fix it.  This is pretty much the only problem I have with Hardy, that and the fact that the 3D portion of the compiz cube crashes the cube.

---

### Post by perce on 2008-06-06
I've just tried Hardy from the live CD - no upgrade yet for me. The live CD had the dim problem at boot and shutdown.

---

### Post by riseringseeker on 2008-06-13
> **perce said:**
> I've just tried Hardy from the live CD - no upgrade yet for me. The live CD had the dim problem at boot and shutdown.

It was the same for me from both the 32 and 64 bit live CD's, was hoping that either A) This was simply a problem with the live CD's and would go away when I installed, or B) It would see a quick fix.

Still hoping....

---

### Post by riseringseeker on 2008-06-17
Already called this in to Tom, but thought I would put it here as well to generate more feedback for the gurus at System76.

I attached an external monitor onto the daru1 (HP 1703) and booted up.  Both monitors were displaying as it booted, and the laptop LCD went dim where it (now *almost*) always does, at the login screen.  The 17 inch monitor though on the same display was *not* dimmed!!!

If anyone else is experiencing the dimming problem, try connecting another monitor and let us all know if it does it on both, or just the LCD.

---

### Post by werewolves on 2008-07-25
I am experiencing the same issue.  I bought a new Daru2 a while back that came w/ Gutsy, and did the system upgrade option to Hardy from the update manager.  Screen is dim, and the brightness control function keys do not work.  They worked in Gutsy.  Not sure of my bios version as the LT is at home.

---

### Post by thomasaaron on 2008-07-25
Hardy is still very problematic on the DarU2. It runs much better on 64-bit Hardy.

Some of the power detection issues can be worked around by following crichell's directions here...
[http://ubuntuforums.org/showthread.php?t=609722&page=15](http://ubuntuforums.org/showthread.php?t=609722&page=15)

That workaround will kill the brightness function keys.

You probably want to post future acpi-related issues for the DarU2 here...
[http://ubuntuforums.org/showthread.php?t=772722&highlight=daru2](http://ubuntuforums.org/showthread.php?t=772722&highlight=daru2)

---

### Post by riseringseeker on 2008-08-08
> **thomasaaron said:**
> Hardy is still very problematic on the DarU2. It runs much better on 64-bit Hardy.

Some of the power detection issues can be worked around by following crichell's directions here...
[http://ubuntuforums.org/showthread.php?t=609722&page=15](http://ubuntuforums.org/showthread.php?t=609722&page=15)

That workaround will kill the brightness function keys.

You probably want to post future acpi-related issues for the DarU2 here...
[http://ubuntuforums.org/showthread.php?t=772722&highlight=daru2](http://ubuntuforums.org/showthread.php?t=772722&highlight=daru2)

Still no update other than Carl's hack?  Other than that, I am fairly happy with (64 bit) Hardy, but the dimming issue needs to be fixed!

---

### Post by riseringseeker on 2008-08-28
Bump

---

### Post by thomasaaron on 2008-08-28
Unfortunately, there has been no fix found for this bug yet. We've not forgotten it, though. It is still on the radar.

---

### Post by beuno on 2008-10-02
For what it's worth, I upgraded to Intrepid and now this problem is gone (I now have a whole lot of new problems, but that's a different story...).

---

