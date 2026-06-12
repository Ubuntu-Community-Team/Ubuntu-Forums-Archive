---
title: "CPU spike while on battery power = Serp6 black screen lockup"
date: 2010-07-28
forum: System76 Support
---

### Post by natieo on 2010-07-28
The problem: a CPU spike while on battery power causes the system to try to execute the power saving procedure for "battery power is critically low".  I know it's trying to use that action because it does slightly different things depending on what I've chosen.  The basic sequence goes like this:

[LIST=1]
[*]Unplug the power
[*]Launch Chromium
[*]Usually that's enough to cause the problem, but if it's still going all I have to do is use Flash by watching a video on Youtube.
[*]The screen freezes and everything becomes unresponsive for a few seconds, like it's going to suspend or something.
[*]The screen goes completely black.  The fan stays running.  There's nothing in the either powermanagement log, and nothing in messages or syslog - although I can see the wifi being scanned in this period where it's unresponsive.
[/LIST]

That's it.  Sometimes I can force shut it down and it will come back, but more often it hangs with a black screen a blinking cursor.  I was able to reinstall grub a few times to get back up, but this last time nothing works and I'm reinstalling Ubuntu.

I'm running a Serp6 with these details:
[LIST]
[*]Graphics Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Video Memory
[*]Hard Drive 80 GB Intel X25-M Solid State Drive
[*]Memory 8 GB - DDR3 1333 MHz - 2 DIMMs This upgrade option only available with Intel Core i7-720QM or Core i7-820QM CPU
[*]Operating System Ubuntu 10.04 (Lucid Lynx) 64 Bit Linux
[/LIST]

Can anyone replicate this?  It's EXTREMELY reproducable for me and it sucks to not be able to use this thing on a battery evern for a few minutes.

Thanks,
Nate

---

### Post by natieo on 2010-07-28
FYI just did my 4th re-install in 24 hours, a fresh brand new 10.04 on formatted partitions.  Pulled system updates, rebooted, pulled Nvidia drivers, rebooted, all seems well.  On a hunch, since it seems like the System76 drivers actually make things worse, I left them out for now.

Downloaded and installed Chromium & the restricted drivers.  Unplugged the power, so I'm running on battery.  Started Chromium.  Hit a youtube page: [http://www.youtube.com/watch?v=PMZiNQcEang&feature=related](http://www.youtube.com/watch?v=PMZiNQcEang&feature=related)  (soccer goals, SFW)

... and kablam.  Seemed more like an XServer restart this time?  I'm done testing this, though, because of how often it messes up my system and makes it unbootable.  I really hope the System76 team can give some tips on this - seems like running anything on the battery isn't an option for Servals at the moment.  Am I seriously the only one hitting this??

Also, the system seems great right now without the System76 drivers.  I can tell from [http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver) or [http://knowledge76.com/index.php/System76_Driver_Changelog](http://knowledge76.com/index.php/System76_Driver_Changelog) what it's supposed to be doing for me on a Serp6, is it really needed?

Thanks,
Nate

---

### Post by PabloH on 2010-07-29
I can't get mine to do that. I have google-branded Chrome, but the same setup otherwise. I turned the display up to max and the cpu settings to performance, yanked the plug out and started Chrome and watched YouTube videos with the volume going out the pc speakers. No shutdowns, reboots, etc.

I have the same graphics, the 160GB harddrive, 8GB of 1333 and the 820 processor.

---

### Post by natieo on 2010-07-29
Thanks for trying.  That gives me hope there might be a solution out there.  Anyone from System76 able to try this on a fresh install?  Do I have bum hardware, if I'm the only one getting this?

Again: brand new format and reinstall, nothing else done to the system, and I have this problem.  Can I dump more system info to help debug?  What might you need to know?

---

### Post by isantop on 2010-07-29
> **natieo said:**
> FYI just did my 4th re-install in 24 hours, a fresh brand new 10.04 on formatted partitions.  Pulled system updates, rebooted, pulled Nvidia drivers, rebooted, all seems well.  On a hunch, since it seems like the System76 drivers actually make things worse, I left them out for now.

Downloaded and installed Chromium & the restricted drivers.  Unplugged the power, so I'm running on battery.  Started Chromium.  Hit a youtube page: [http://www.youtube.com/watch?v=PMZiNQcEang&feature=related](http://www.youtube.com/watch?v=PMZiNQcEang&feature=related)  (soccer goals, SFW)

... and kablam.  Seemed more like an XServer restart this time?  I'm done testing this, though, because of how often it messes up my system and makes it unbootable.  I really hope the System76 team can give some tips on this - seems like running anything on the battery isn't an option for Servals at the moment.  Am I seriously the only one hitting this??

Also, the system seems great right now without the System76 drivers.  I can tell from [http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver) or [http://knowledge76.com/index.php/System76_Driver_Changelog](http://knowledge76.com/index.php/System76_Driver_Changelog) what it's supposed to be doing for me on a Serp6, is it really needed?

Thanks,
Nate

I'm so sorry about this. You seem to be hitting every single known issue we have affecting this system. The inability to boot after installing is actually caused by a grub update, see [here](http://ubuntuforums.org/showthread.php?t=1540155).

The other issue, or X resets, are a known issue on the Nvidia driver with fresh installs. You can use the open source driver or try the version 173 of the proprietary driver to get it working. We're working on a more acceptable solution, and I think we're close.

---

### Post by natieo on 2010-07-29
Thanks a million for the update, @isantop -- good to know there's a reason for most of what I'm seeing, and it sounds like it's not bum hardware.

I reverted to v173 of the Nvidia driver and will see if that helps.

The only thing that makes me nervous still is that when the system did more than just an X restart and the screen stayed black with the fans running, I had to hold the power button to shut it down.  I'd roughly guess that a third of the time it would boot up fine the next time, and a third of the time wouldn't but a GRUB install would fix it.  That last third, however, resulted in the hung black screen with blinking cursor, despite multiple GRUB install attempts.  (as described [here]("http://ubuntuforums.org/showthread.php?t=1509043")) Those required reinstalls of the OS...

But, if the 173 driver makes the problem moot, than I'm less worried about trying to track that down!

Thanks again for the update, I really appreciate you listening and filling me in on the progress of these issues.

Nate

---

