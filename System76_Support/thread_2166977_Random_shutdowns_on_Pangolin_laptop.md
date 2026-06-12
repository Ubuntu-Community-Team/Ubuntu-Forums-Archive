---
title: "Random shutdowns on Pangolin laptop"
date: 2013-08-11
forum: System76 Support
---

### Post by Medeo on 2013-08-11
Hi,

Posting this in the System76 forum for now because I don't really know if it's a hardware or a software issue. My PanP9 keeps losing power randomly, 2-3 times a week (sometimes twice in a day). Doesn't seem to be triggered by anything in particular; I'll just be typing or watching a video or something, and BAM, blank screen. This seems to happen on both AC and battery. Most of the answers I found on Google blamed it on overheating, but I'm almost certain that's not the issue; I always keep the machine well-ventilated and I rarely do anything all that CPU intensive (like I said, this happens when I'm just doing normal stuff like browsing). This behavior started about a month ago.

There is also a bit of a delay before it happens. I notice this especially if I'm typing: it becomes unresponsive to keyboard and mouse input for a second or two before the machine shuts off. I haven't noticed any video or audio freezing, though.

I'm currently running Linux Mint 14 with kernel version 3.5.0. I don't know which logs or whatever would be useful, so please let me know any further information I should provide about my system. Thanks for any help you can give me with this annoying problem!

---

### Post by golfdiesel on 2013-08-12
I think you should check the temperatures. My Gazelle Pro gets ridiculously hot even when doing nothing (CPU well above 45 degrees and the SSD a whopping 72 degrees (all celcius that is)). This is when I am just browsing the web and/or watching some Youtube clips.

---

### Post by Boab1993 on 2013-08-12
Before going any futher i agree with golf diesel, check your temperature of your CPU next time its on the blink in the BIOS or by downloading pSensor/lm-sensors

The CPU can easily overheat during something graphically heavy if not properly cooled, given that your running mint and watching videos, id say its entirely plausable.

One measure i know you can always do is disable 'smart cooling' (or called similar) within your BIOS, this makes the fans on your system always run at maximum speed.

---

### Post by Medeo on 2013-08-12
Thanks, I'll try keeping an eye on the temperature and see if anything's amiss. It is August, after all :) CPU temp is currently 52 C, which is fine I think. I should also note that the fan has never been running fast when the shutdown happens.

---

### Post by Boab1993 on 2013-08-13
Think the threashold of most modern processors is around about 75-80C, so yes you should be fine, watch a video and see if it spikes.

However 52C is a fine temperature, so time to explore other options, when your computer goes blank screen, does it actually switch off?
Did you make any software/hardware changes at the point where this problem occured?

---

### Post by phxpx on 2013-08-13
I have GazP9 it is about 26C out here and my CPU temperature is around 55C. System76 told me this is normal but I think it is overheating. Also I can't read my sdd temperature. I don't know why.
I am planning to install kernel with PHC-Patch to undervolt my CPU until better drivers are released for haswell.

---

### Post by isantop on 2013-08-13
If it it's happening on non-CPU intensive tasks, and it isn't happening on *all* CPU intensive tasks, then the problem can't be heat.

Make sure that the charging light on the front of the laptop is on (either orange or green), and if the light stays on and the system still shuts down, I would start looking at software, which you can rule out by running from a live disk.

---

### Post by Medeo on 2013-08-13
> **Boab1993 said:**
> Think the threashold of most modern processors is around about 75-80C, so yes you should be fine, watch a video and see if it spikes.

However 52C is a fine temperature, so time to explore other options, when your computer goes blank screen, does it actually switch off?
Did you make any software/hardware changes at the point where this problem occured?

Yes, but it doesn't just lose power immediately; it sort of "freezes" for a few seconds beforehand, if that makes sense. Like when you tell it to go to sleep, only instead of sleeping, it just shuts down. I haven't made any hardware changes, and no major software ones; I only install software from the Ubuntu repositories and run updates about once a week. Maybe an update inadvertently messed up the power management settings or something?

[QUOTE=isantop]
Make sure that the charging light on the front of the laptop is on (either orange or green), and if the light stays on and the system still shuts down, I would start looking at software, which you can rule out by running from a live disk. [/QUOTE]

Thanks, I'll look for that next time it happens. Guess I just have to play the waiting game for now.

---

### Post by Boab1993 on 2013-08-14
Right this can be a number of software problems, you actually brought up on i never would have thought of.

Im going to rule out power management because you mentioned in your post it happens on AC, so should not be a problem, however you might aswell check that all is in order.

Software-wise a whole list of problems could be the problem, please post your kernel log.

It can be found here /var/log/kern.org.

---

### Post by Medeo on 2013-08-14
> **Boab1993 said:**
> Software-wise a whole list of problems could be the problem, please post your kernel log.

It can be found here /var/log/kern.org.

I assume you mean /var/log/kern.log?

It's like 4000 lines, though. I wrote down the time when the problem last occurred (Aug 11 at 5:17 PM) so I'll just post that section. Let me know if you need the whole thing and I'll attach it.

```

Aug 11 17:17:09 jonathan-laptop kernel: [175583.499405] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.499416] ACPI Error: Method parse/execution failed [\_SB_.BAT0.UPBS] (Node ffff880213865e88), AE_TIME (20120320/psparse-536)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.499426] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff880213865eb0), AE_TIME (20120320/psparse-536)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.499433] ACPI Exception: AE_TIME, Evaluating _BST (20120320/battery-455)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.999164] ACPI: EC: input buffer is not empty, aborting transaction
Aug 11 17:17:09 jonathan-laptop kernel: [175583.999174] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.999190] ACPI Error: Method parse/execution failed [\_SB_.BAT0.UPBS] (Node ffff880213865e88), AE_TIME (20120320/psparse-536)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.999206] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff880213865eb0), AE_TIME (20120320/psparse-536)
Aug 11 17:17:09 jonathan-laptop kernel: [175583.999220] ACPI Exception: AE_TIME, Evaluating _BST (20120320/battery-455)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.498903] ACPI: EC: input buffer is not empty, aborting transaction
Aug 11 17:17:10 jonathan-laptop kernel: [175584.498913] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.498929] ACPI Error: Method parse/execution failed [\_SB_.BAT0.UPBS] (Node ffff880213865e88), AE_TIME (20120320/psparse-536)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.498944] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff880213865eb0), AE_TIME (20120320/psparse-536)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.498957] ACPI Exception: AE_TIME, Evaluating _BST (20120320/battery-455)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.998644] ACPI: EC: input buffer is not empty, aborting transaction
Aug 11 17:17:10 jonathan-laptop kernel: [175584.998655] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.998672] ACPI Error: Method parse/execution failed [\_SB_.BAT0.UPBS] (Node ffff880213865e88), AE_TIME (20120320/psparse-536)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.998688] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff880213865eb0), AE_TIME (20120320/psparse-536)
Aug 11 17:17:10 jonathan-laptop kernel: [175584.998703] ACPI Exception: AE_TIME, Evaluating _BST (20120320/battery-455)
Aug 11 17:17:11 jonathan-laptop kernel: [175585.498369] ACPI: EC: input buffer is not empty, aborting transaction
Aug 11 17:17:11 jonathan-laptop kernel: [175585.498375] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20120320/evregion-501)
Aug 11 17:17:11 jonathan-laptop kernel: [175585.498384] ACPI Error: Method parse/execution failed [\_SB_.BAT0.UPBS] (Node ffff8802Aug 11 17:17:46 jonathan-laptop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug 11 17:17:46 jonathan-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 11 17:17:46 jonathan-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 11 17:17:46 jonathan-laptop kernel: [    0.000000] Linux version 3.5.0-17-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 (Ubuntu 3.5.0-17.28-generic 3.5.5)
Aug 11 17:17:46 jonathan-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=37d08e73-1a60-4049-aed0-d5a76827b7f7 ro quiet splash vt.handoff=7

```

So it looks like some kind of ACPI issue after all?

---

### Post by Boab1993 on 2013-08-15
Quite right on your correction. Oops.

Ill be damned. 

'BAT0' im pretty sure is the laptop battery and by the sound of it, its not co-operating.
This is a first for me, given that it also does it on AC power, ill have to do some reading.

However can i get a bit of the kernel log up until 17:17:09, lets say from 17:16:30?

Have you checked the power management settings and made sure it asks when power is low etc?

---

### Post by Medeo on 2013-08-16
Sure, here's the preceding lines. Doesn't seem to be related, but who knows.

```
Aug 11 17:04:46 jonathan-laptop kernel: [174840.573749] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=468 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:04:46 jonathan-laptop kernel: [174840.880693] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=470 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:04:47 jonathan-laptop kernel: [174841.494893] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=473 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:04:47 jonathan-laptop kernel: [174842.416037] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=474 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:04:50 jonathan-laptop kernel: [174844.565268] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=484 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:04:54 jonathan-laptop kernel: [174848.556930] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=489 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:05:02 jonathan-laptop kernel: [174856.540197] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=494 PROTO=UDP SPT=5351 DPT=5350 LEN=20 
Aug 11 17:05:18 jonathan-laptop kernel: [174872.813762] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:23:12:fb:50:06:08:00 SRC=10.0.1.1 DST=224.0.0.1 LEN=40 TOS=0x00 PREC=0x00 TTL=1 ID=504 PROTO=UDP SPT=5351 DPT=5350 LEN=20 

```

Edit: Forgot to answer the second part. Everything seems fine with the power settings.

---

### Post by Boab1993 on 2013-08-16
Well,

There is a way you can turn ACPI off in ubuntu, but that leaves you without battery and power monitors or even stop your computer from booting properly, so we'll leave that till later and see if theres anything else that can work.

We can try first updating your kernel : [https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

Be sure to read the roll-back and unistallation at the bottom of the page, as this can make it worse depending on your systems support, easy to change though.

Try this link, given that yours is battery related, this may, or may not help: [https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery), this is a long shot, but basically i want to try everything before turning acpi off.

If none of this works, we'll explore disabling it.

---

### Post by isantop on 2013-08-16
There are no ACPI compatibility issues with our Pangolin laptops. If he's still having trouble, this is likely a hardware failure, and we should bring the system in for repair.

---

### Post by Boab1993 on 2013-08-16
> **isantop said:**
> There are no ACPI compatibility issues with our Pangolin laptops. If he's still having trouble, this is likely a hardware failure, and we should bring the system in for repair.

Thats fair enough, i was treating this as a general problem not a system76, as i don't know much about them, therefore no point in speculating.

Any advice you can give im sure will be much more useful to him, considering you have a 76 yourself

---

### Post by isantop on 2013-08-16
I actually work for System76 support. ;-)

Medo: I'd recommend opening a support ticket our website. This either sounds like a major software corruption issue or a hardware issue (memory or hard drive are the first things that come to mind).

---

### Post by RichardET on 2013-08-17
> **Medeo said:**
> Hi,

Posting this in the System76 forum for now because I don't really know if it's a hardware or a software issue. My PanP9 keeps losing power randomly, 2-3 times a week (sometimes twice in a day). Doesn't seem to be triggered by anything in particular; I'll just be typing or watching a video or something, and BAM, blank screen. This seems to happen on both AC and battery. Most of the answers I found on Google blamed it on overheating, but I'm almost certain that's not the issue; I always keep the machine well-ventilated and I rarely do anything all that CPU intensive (like I said, this happens when I'm just doing normal stuff like browsing). This behavior started about a month ago.

There is also a bit of a delay before it happens. I notice this especially if I'm typing: it becomes unresponsive to keyboard and mouse input for a second or two before the machine shuts off. I haven't noticed any video or audio freezing, though.

I'm currently running Linux Mint 14 with kernel version 3.5.0. I don't know which logs or whatever would be useful, so please let me know any further information I should provide about my system. Thanks for any help you can give me with this annoying problem!


I would call their support squad and complain!  Several years ago I bought a cheapo Dell Vostro A860, ripped the 32 bit Windows right off ran several different 64 bit Linux's on it, never had any issues, even with suspend.  Where is it now?  My 15 yr has it, and of course within 6 months, he has managed to break off a key.

---

### Post by Medeo on 2013-08-20
Sorry for the slow reply, I've been away for the last few days.

> **Boab1993 said:**
> Well,

There is a way you can turn ACPI off in ubuntu, but that leaves you without battery and power monitors or even stop your computer from booting properly, so we'll leave that till later and see if theres anything else that can work.

We can try first updating your kernel : [https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

Be sure to read the roll-back and unistallation at the bottom of the page, as this can make it worse depending on your systems support, easy to change though.

Try this link, given that yours is battery related, this may, or may not help: [https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery), this is a long shot, but basically i want to try everything before turning acpi off.

If none of this works, we'll explore disabling it.

Thanks, I'll upgrade the kernel and see what happens. I was already forced to upgrade on this laptop once before, since the 3.2 kernel that shipped with Ubuntu 12.04 made it randomly freeze up (that was a known problem with the Ivy Bridge processor and not my machine or System76 specifically, however).

[quote=isantop]Medo: I'd recommend opening a support ticket our website. This either sounds like a major software corruption issue or a hardware issue (memory or hard drive are the first things that come to mind). [/quote]

Can I still open a support ticket if my warranty has expired?

---

### Post by isantop on 2013-08-21
> **Medeo said:**
> Can I still open a support ticket if my warranty has expired?

Of course! We never turn away tech support because of an expired warranty.

---

