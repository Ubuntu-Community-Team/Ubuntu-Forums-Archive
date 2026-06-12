---
title: "Maverick logs - One Quebecker's adventure in Linuxland"
date: 2010-12-31
forum: Testimonials &amp; Experiences
---

### Post by 3602 on 2010-12-31
Happy New Year, guys.
Basically I feel like writing. New computer and a new Ubuntu release is something. To me, anyway. I used Jaunty before on an old computer so this isn't the first time I use Linux.
And there doesn't seem to have a blog anywhere...

30 Dec, 10
Acquired Gateway ID59C-04h portable computer. Burnt an Ubuntu 10.10 32-bit CD from father's computer.
Install. Installation went through fine. Saw some* I/O error, sector ######* jabber. Reboot. Got 197 updates, reboot. Then I got a notice about a Restricted nVidia driver.  Fine, install that for 3D Acceleration, not that I'll ever need it except for playing Tux Racer. Reboot.
  Fun part: No GUI. Directly boots into kernel.
  Shutdown, re-insert CD, re-install.
  Second installation was also smooth. Although upon reboot the bottom  panel cannot load applets. Skipped the 197 updates and went directly to  the nVidia driver. Reboot.
  Even worse: Now there isn't even a kernel boot. It went to "Check battery state" (fsck) and everything stopped there.
  Third installation. Upon reboot I picked Maverick-proposed, so I got 216  updates. Had that installed and reboot. Didn't dare the nVidia driver.
  Internet was fine. The screen was too bright and the built-in brightness  keys don't work. Thought this was driver-related, posted here on UF and went  to sleep (2AM). All that was done while Grant was trying to kill the  Gorn in the background (Mythbusters, anyone?).


31 Dec, 10
  Wake up. Magically the brightness works, all hail the great Tux indeed. It became apparent that I have nVidia Optimus technology which  FUBARs Ubuntu installations. Linux hybrid graphics is far from perfect  and nobody seems to know how to contact Megatron. Guess I&#8216;ll just have  to live with it.
  Acer/Gateway computer keyboards don't have built-in Caps Lock lights  (indicators). That was a large piece of PITA indeed. Installed an applet (Key Lock) to solve this.
  Installed Chinese input. Now the touchpad won't glow (well, never did since Linux). Oh well. GPointer didn't help.
  Installed a couple more applets as I did back in 9.04. Now the fan is  always on (albeit very quiet and slow) and CPU temps are good (only hope  that XSensors is correctly interacting with ACPI).


 *Later that day...*
Read through some posts about Optimus and Linux. Played Tux Racer, WXGA. Solid frame rates at around 30. glxgears still show Vsync, 60 (59.9 actually) FPS. Grep rendering returns Yes. So what card am I using, huh.
Found out the headphone jack doesn't work. Searched a lot, installed some packages and still didn't work. Figured out card is Conexant CX20585, which isn't listed in those triggers. Read somewhere to try *model=thinkpad*, So I did and the headphone jack worked.
Tried to install a piece of software from Central. Failed. Read the report and *alsa-drivers-linuxant* is somehow failing. Uninstall that from Synaptics. Also removed some driver package (linux-backports). Reboot.
Headphone jack again did not work. Reinstalled linux-backports, reboot. Finally audio works, and without the *alsa-drivers-linuxant*, I can build packages again.
Found out weird little problem when running on battery power. Posted about that, also posted about the brightness controls that are not so correct after all.


...who knows what else awaits me.

Sorry, just wanted to get all that out. If anyone of you can share your Linux journey, it'd be a great read indeed.
Thanks.

---

### Post by cariboo on 2011-01-01
Moved to Testimonials, as this isn't a Cafe thread.

---

### Post by dmizer on 2011-01-01
I'd just like to say ... I admire your determination.

---

### Post by 3602 on 2011-01-01
> **dmizer said:**
> I'd just like to say ... I admire your determination.


Thanks. I've seen much worse in Windows and I came out alive.

---

### Post by Arthur_D on 2011-01-01
Woah, great read, especially for those later who gets trouble with same computer, and can then read what caused you trouble/how far you got. :)
My desktop computer is mostly working great, so I have not that much to share, unfortunately.

---

### Post by 3602 on 2011-01-01
Jan 1, 11
New Year. Found two small blocks of wood and propped up the rear (battery) side of the computer. Fan is now off (sometimes comes on). XSensors report around 35°C while without the wood, it can get to 40°C and that's why the fans was constantly on. Put System Monitor and Hardware Sensors applets in panel so I can see CPU usage and temperatures.
Went around Ubuntu China and finally understood nVidia Optimus. Compiled some info then posted [this here]("http://ubuntuforums.org/showthread.php?t=1657660"). Was able to disable the GT 420M card using a link in that post. Now the fan stays off for even longer intervals (rarely spins now).
Disabling the card did not affect *grep rendering* nor* glxgears* results. Although in glxgears, instead of getting constantly 59.9, I now actually get 60. 
About to test Tux Racer.
Tux Racer practice run went fine. Still solid FPS values around 30. Fan was on all the time and CPU temps fell to 34°C.

[I]Later that day...
[/I]Fixed hard drive constantly spinning up-and-down by installing *laptop-mode-tools*. It removed the previous *pm-utils*. Reboot. This causes problems: Suspend and Hibernate functions are no longer available. An ugly but working fix and be found here: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/638307)
Follow posts #11 and #13. Reboot. Battery life seems to be "wrong" but it may just be the fact that it (consumption rate) fluctuates a lot, and I arrived checking it at unlucky points in time. Should read the rate graph for a rough average.
Posted over at Linux Hybrid Graphics about whether shutting off the nVidia is permanent (or it comes back on-line at each boot/reboot).
Brightness problem remains. Hopefully I can solve it within a week (well, all the above gunk are solved in three days) so I may finally enjoy a functional system and play Tux Racer for a day or so.

---

### Post by Tamlynmac on 2011-01-01
> cariboo907
Moved to Testimonials, as this isn't a Cafe thread. 	

Reads more like an journal (even dated). :rolleyes:
Perhaps, the forums needs a new section - "Journals & Diaries". :p


To the OP:

Thanks for sharing your experience & Good Luck.

---

### Post by s3a on 2011-01-01
You should consider Debian or stick to Ubuntu LTS and wait like 6 months after each LTS release to use it. That should give you give you a problem-less environment if you're the unlucky type when it comes to computer issues.

---

### Post by 3602 on 2011-01-02
Thanks for all the appreciation, guys. Although I doubt that someone is going to purchase exactly the same computer and install Maverick... Linux ain't good for gaming, and this computer really has overkill specs.
Also I hope this thread is somewhat less disturbing and more helpful than Facebook updates...

Jan 2, 11
Figured out that the card won't stay down after each reboot. Asked [here]("http://ubuntuforums.org/showthread.php?t=1657941") and eventually figured it out myself. Battery life can increase by a full hour with the card off, which means 3:30 to 4:00 of battery time. Gateway reports maximum of 6 hours, but that's just best case scenario, running Win7. 
Couple of small things left now. Real small things. One, the brightness bug's severity has been pushed from "Minor" to "Trivial" since I really can live with it (and I'll most likely never going to use it full-blast). Two, the touchpad is reported as PS/2 Generic Mouse, which means no speed control, no pinch action either. But the pad works and I really don't need that many controls.
Three, and probably most important, you may have read that I installed laptop-mode-tools then a re-rolled pm-utils to stop the hard drive spinning up and down. Well, the re-rolled pm-utils cannot be upgraded. I'll need to find a way around this, although Launchpad is confirming this bug and is (hopefully) working on it. Interesting though, PowerTOP told me "Press W to stop all the access" or something so maybe it has something to do with that? I don't know.

*Later that day...*
Decided to stop worrying about these little problems and game myself some. Torcs has horrible FPS (6-10) so removed that. Neverball is insane: ever tried to use the touchpad and arrow keys at the same time? Whoa.
Triggers controls are loose, the car would slide and flip real easy. But heck it's fun. Getting some graphics bugs with Tux Cart, a thin black/white flashing line across the screen sometimes, but doesn't really hinder gameplay.
If no more errors surface, then the logging part should be it. If I do somethin' major or screw somethin' up then I'll come logging. Thanks for reading.

---

