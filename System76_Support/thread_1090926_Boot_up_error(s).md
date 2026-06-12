---
title: "Boot up error(s)"
date: 2009-03-08
forum: System76 Support
---

### Post by mayerg on 2009-03-08
I received a Wild Dog Performance with Ubuntu 8.10 (Intrepid Ibex) 64-bit, a Quad core (Q9550) and 8Gb memory a few days ago. I have been experiencing intermittent boot up errors such as "Out of Memory - System Halted" or, more commonly, "CRC Error - System Halted". It gets through the "System76" splash screen, and the "GRUB loading stage2" screen quickly. Then shows, "Starting Up...". Next, after a brief pause, it displays one of those errors. Unless I'm mistaken, it beeps once at the very beginning when it works, three times if it's going to fail. After hitting the reset button or shutting down and restarting, it sometimes boots and sometimes doesn't.

Taking a page from my video issue, I specifically checked the memory and it all seems to be seated properly with all of the white connetors fully in the locked position. All other components and connectors also seem to be in proper position.

All info online that I've seen frequently talks about this issue with dual-boot. No such case here, Ubuntu-only.

Anyone with any ideas?

Regards,

- Gary

---

### Post by Guille Damke on 2009-03-09
It seems that something inside got loose, probably a RAM module or the Graphic Card. Wait for more input anyway, but I think you'll have to open it and check that everything is set in place and tight.

---

### Post by thomasaaron on 2009-03-09
I second that. Also, make sure your hard drive cables are set (both at the drive and at the motherboard. It sounds like something took a bump.

---

### Post by mayerg on 2009-03-15
For the past week now, I have performed additional troubleshooting on the machine. I have seated and reseated everything... twice. I have run memtest and was told my memory passed. During the course of my testing and getting boot up errors, here’s some additional information that I’ve gathered:

The “CRC Error” comes up ~90% of the time when there is an error. In addition to the “Out of Memory” and “CRC Error”, I also get auto-reboot right after it displays “Starting up…” and then pauses for a few seconds, I get “Invalid Compressed Format (err=1) - System halted” , and I have seen where it just hangs indefinitely after displaying “Starting up…”  While it always fails when it triple-beeps, that’s rare. It often only beeps once and fails anyway.

I have isolated the problem to the DVD drive. The error typically comes when I first boot up the machine after it has been off for at least a couple of hours. Once I receive the error, I typically have to reboot (usually shutting down the machine completely) about a half dozen times before, if I’m lucky, it boots correctly. If it does boot normally, it sometimes keeps booting, sometimes does not. However, I have found that, consistently, if I remove the SATA cable from the DVD drive, it will boot normally even on the first, second or whatever try I’d normally expect it to still throw errors. I’ve then been able to get it to consistently reboot and/or boot from shutdown to a normal boot over a dozen times in a row (without the DVD drive plugged in). This is whether I let it sit 10 seconds after shut down or a few hours. But, if I let it sit a few hours, plug the SATA cable back into the DVD drive and boot up, I immediately get an error again. I have tried swapping cables, swapping/changing SATA ports on the mobo, etc. It always comes down to whether or not the DVD drive is connected to the SATA bus.

Now, whether it is a physical drive problem (there is no DVD in the drive when I boot up, ever), or a driver issue, I do not know. The drive in question is the one that came with the Wild Dog: a Sony NEC Optiarc, Model AD-7221S, manufactured Nov 2008. It's a CD/DVD rewritable with lightscribe.

Edit: I should add that I find the "wait time for error" behavior odd. If it is a physical error, I would suspect a bad capacitor. Note: I have checked the mobo for domed caps. None that I can see.

- Gary

---

### Post by jdb on 2009-03-15
> **mayerg said:**
> For the past week now, I have performed additional troubleshooting on the machine. I have seated and reseated everything... twice. I have run memtest and was told my memory passed. During the course of my testing and getting boot up errors, here’s some additional information that I’ve gathered:

The “CRC Error” comes up ~90% of the time when there is an error. In addition to the “Out of Memory” and “CRC Error”, I also get auto-reboot right after it displays “Starting up…” and then pauses for a few seconds, I get “Invalid Compressed Format (err=1) - System halted” , and I have seen where it just hangs indefinitely after displaying “Starting up…”  While it always fails when it triple-beeps, that’s rare. It often only beeps once and fails anyway.

I have isolated the problem to the DVD drive. The error typically comes when I first boot up the machine after it has been off for at least a couple of hours. Once I receive the error, I typically have to reboot (usually shutting down the machine completely) about a half dozen times before, if I’m lucky, it boots correctly. If it does boot normally, it sometimes keeps booting, sometimes does not. However, I have found that, consistently, if I remove the SATA cable from the DVD drive, it will boot normally even on the first, second or whatever try I’d normally expect it to still throw errors. I’ve then been able to get it to consistently reboot and/or boot from shutdown to a normal boot over a dozen times in a row (without the DVD drive plugged in). This is whether I let it sit 10 seconds after shut down or a few hours. But, if I let it sit a few hours, plug the SATA cable back into the DVD drive and boot up, I immediately get an error again. I have tried swapping cables, swapping/changing SATA ports on the mobo, etc. It always comes down to whether or not the DVD drive is connected to the SATA bus.

Now, whether it is a physical drive problem (there is no DVD in the drive when I boot up, ever), or a driver issue, I do not know. The drive in question is the one that came with the Wild Dog: a Sony NEC Optiarc, Model AD-7221S, manufactured Nov 2008. It's a CD/DVD rewritable with lightscribe.

Edit: I should add that I find the "wait time for error" behavior odd. If it is a physical error, I would suspect a bad capacitor. Note: I have checked the mobo for domed caps. None that I can see.

- Gary

Good troubleshooting!!

It sounds like the DVD is sometimes responding when it shouldn't & is clobbering the hard drive data.

A piece of "killer hardware" like that is very hard to find.

jdb

---

### Post by thomasaaron on 2009-03-16
Yes, great troubleshootiing!

Fill out this form, and we'll get you a new DVD drive...
[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

In the mean time, press the "Del" key when you see the manufacturer splash screen and go into the BIOS set-up. Make sure the Hard Drive is set as the first boot device. This *should* eliminate the problem until you get the new drive.

---

### Post by mayerg on 2009-03-17
After a week of consistent performance, it seems the computer refuses to be troubleshot so easily. ](*,)   I think you guys jinxed me with early congrats.

I go to turn it on today to see what order the boot order was set, there is no power to the DVD drive. I missed the BIOS menu anyway and so it started booting. I get:

[ 0.275492] ACPI: Aborted because no cpio magic
[17.857069] crc error
[17.883175] Kernel panic - not synching: VFS: Unable to mount root fs on unknown - block(0,0)

reboot and get "crc error"

reboot, check BIOS, BTW, the boot order was always for the hard drive first. Then go into Recovery mode.  boots normally after telling it to continue normal boot.

reboot and get:
[ 0.274211] ACPI: Aborted because junk in compressed archive
[17.857118] crc error
[17.883239] Kernel panic - not synching: VFS: Unable to mount root fs on unknown - block(0,0)

reboot and get:
[ 0.275639] ACPI: Aborted because broken padding
[17.857060] crc error
[17.883145] Kernel panic - not synching: VFS: Unable to mount root fs on unknown - block(0,0)

If I boot again and go through the Recovery mode, it works.

So, most everything I see resembling this on line indicates a kernel corruption. However, I do not know Linux (let alone Ubuntu kernel) well enough to state cause and effect. It almost seems to me as if the constant testing over the past week might have ruptured something in its bits and bytes of the kernel.

It would appear, to properly determine what's wrong, that the OS should be reinstalled and see if all this CRC error stuff happens all over. Tom, I will respond to you privately with additional commentary.

Regards,

- Gary

---

### Post by thomasaaron on 2009-03-17
OK. You probably should email me at support(at)system76(dot)com. I see private messages about once a year.:D

---

### Post by mayerg on 2009-03-21
In hopes that this is useful to someone else with similar issues, I continue...

I have now downloaded the latest Ubunto 8.10 64-bit desktop .iso. After verifying the MD5 sum hash, I burnt the .iso to CD using 1x speed. Almost two hours later, :-\", I had my CD. I also checked the disk with the disk checker in the boot menu. I have reinstalled the OS twice and tested it. Both times, I have consistently gotten the CRC Errors at boot.

I have also discovered two things. First, if I boot the machine after being off for a few hours, get the CRC Error, and reboot, I continue to get the CRC Error (as before). However, if I leave the machine sit for ~20+ minutes after the first CRC Error, and then reboot, it boots normally. This reaffirms my belief that it's likely a hardware issue, specifically capacitance. Second, I noticed that if I shut down right after a CRC Error, and remove the SATA cable from the DVD without removing it from the mobo, I get an ACPI error. But, if I completely remove the SATA cable from the drive and mobo, I do not. So, while I'm not certain of the exact cause of the ACPI errors, they do seem to be symptomatic of the CRC Error problem, vice the other way around.

Of course, if anyone out there has any further suggestions, I'd be happy to hear them.

Regards,

- Gary

---

### Post by jdb on 2009-03-21
> **mayerg said:**
> In hopes that this is useful to someone else with similar issues, I continue...

I have now downloaded the latest Ubunto 8.10 64-bit desktop .iso. After verifying the MD5 sum hash, I burnt the .iso to CD using 1x speed. Almost two hours later, :-\", I had my CD. I also checked the disk with the disk checker in the boot menu. I have reinstalled the OS twice and tested it. Both times, I have consistently gotten the CRC Errors at boot.

I have also discovered two things. First, if I boot the machine after being off for a few hours, get the CRC Error, and reboot, I continue to get the CRC Error (as before). However, if I leave the machine sit for ~20+ minutes after the first CRC Error, and then reboot, it boots normally. This reaffirms my belief that it's likely a hardware issue, specifically capacitance. Second, I noticed that if I shut down right after a CRC Error, and remove the SATA cable from the DVD without removing it from the mobo, I get an ACPI error. But, if I completely remove the SATA cable from the drive and mobo, I do not. So, while I'm not certain of the exact cause of the ACPI errors, they do seem to be symptomatic of the CRC Error problem, vice the other way around.

Of course, if anyone out there has any further suggestions, I'd be happy to hear them.

Regards,

- Gary

Have yor tried a different SATA cable??

jdb

---

### Post by thomasaaron on 2009-03-21
That's a good suggestion, but I doubt he has one.

I can send out a new DVD drive (and SATA cable) or bring it in for repair. It could be Mobo related too.

---

### Post by mayerg on 2009-03-22
jdb, thanks for the suggestion. Thomas is right, I do not have an extra. However, I did try swapping the cables and ports between the hard drive and DVD as I did when I first started testing. Not as thoroughly as last time but same results so far.

I did think of one more test that I can run. :idea: It may isolate whether this is a mobo issue or a DVD issue but it really depends on how much faith one has in my capacitance theory. I can remove power and SATA cx from the DVD, turn on the machine and let it run ~20+ minutes, power down, plug the DVD back in and boot back up. If I can consistantly boot with no error, then it's power to the mobo that's making a difference. If, however, I still get boot errors, I can then try removing the SATA cable and leaving power to the DVD. If, upon reboot, I then don't get the errors, then it is the DVD. In my previous testing, I had not paid carefull attention to this variable. And I have rebooted with both scenarios (power to and removed from DVD).

But, this does come back to how much one accepts the capacitance theory and time. Time to let the box sit between boots to discharge.

---

### Post by DrLongGhost on 2009-05-31
I also recently got this error and was able to resolve it and get my system to boot.  First, a little history.

I have a 2 year old PC that I built myself.  I ran XP on it for a couple years but eventually, I found XP to be too flaky.  My PC would regularly crash after being left on for a week or so.  Occassionaly, I'd get disk errors, so I'd do a scandisk that would find some stuff, but not make the problem go away completely.

Fast forward to last week when I removed XP and installed Jaunty Jackalope.  Under Ubuntu, I still see occassional crashes, after my PC has been on for a couple days.  This leads me to suspect something in my hardware craps out eventually (maybe memory, or something overheating).

This morning I got the errors mentioned in this post:
acpi: aborted because no cpio magic
crc error
kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

After restarting my PC, it still wouldn't boot.  In reviewing this post, the above errors seemed to indicate any number of problems, so I cracked my case open and did the following:

  * Sprayed everything with compressed air to remove the considerable dust that had been deposited since my last time cleaning the inside of the PC
  * Removed both my sticks of RAM and reseated them in each other's slot
  * I noticed that the main mobo power cord was resting and coming into direct contact with one of the RAM sticks.  I used a zip tie to put some tension on it so it would no longer come in contact with the RAM.
  * Swapped out my harddrive SATA cable with a spare.
  * Checked all the other cables to make sure everything was tight.

I rebooted my PC and it started right up.  Time will tell whether or not I've fixed the issues with it crashing after sitting idle for a couple days.  I doubt it.  But, I'm happy that it's just starting up again now.  Hopefully this post will be useful to someone else getting this error.

---

### Post by thomasaaron on 2009-06-01
We've seen this issue now on two computers. In both cases, re-seating the memory fixed the problem.

---

