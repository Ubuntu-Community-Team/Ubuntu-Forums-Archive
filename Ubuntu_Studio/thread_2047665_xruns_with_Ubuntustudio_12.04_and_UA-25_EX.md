---
title: "xruns with Ubuntustudio 12.04 and UA-25 EX"
date: 2012-08-25
forum: Ubuntu Studio
---

### Post by DARKAD on 2012-08-25
I installed the new Ubuntustudio 12.04 using my UA-25ex as main interface on qjackctl with 44100/512frames/2buffer.
I just got the automated - update.
While I'm inserting some notes on rosegarden staff and listening to them with qsynth (/usr/share/sounds/sf2/FluidR3_GM.sf2 142MB).
I see an xrun every five minutes.

I did the changes that the realTimeConfigQuickScan.pl suggests([https://code.google.com/p/realtimeconfigquickscan/](https://code.google.com/p/realtimeconfigquickscan/)).

This is what the realTimeConfigQuickScan.pl says:

== GUI-enabled checks ==
Checking if you are root... no - good
Checking filesystem 'noatime' parameter... found - warning
/ does not have the 'noatime' parameter set
/boot/efi does not have the 'noatime' parameter set
For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#filesystems)
Checking CPU Governors... CPU 0: 'performance' CPU 1: 'performance'  - good
Checking swappiness... 10 - good
Checking for resource-intensive background processes... none found - good
Checking checking sysctl inotify max_user_watches... >= 524288 - good
Checking access to the high precision event timer... readable - good
Checking access to the real-time clock... readable - good
Checking whether you're in the 'audio' group... yes - good
Checking for multiple 'audio' groups... no - good
yes - good.
Checking the ability to prioritize processes with chrt... yes - good
Checking kernel support for high resolution timers... found - good
Kernel with Real-Time Preemption... not found - not good
Kernel without real-time capabilities found
For more information, see [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#installing_a_real-time_kernel)
Checking if kernel system timer is set to 1000 hz... found - good
Checking kernel support for tickless timer... found - good
== Other checks ==
Checking filesystem types... ok.
not found.
** Warning: no tmpfs partition mounted on /tmp
   For more information, see:
   - [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#tmpfs)
   - [http://lowlatency.linuxaudio.org](http://lowlatency.linuxaudio.org)
** Set $SOUND_CARD_IRQ to the IRQ of your soundcard to enable more checks.
   Find your sound card's IRQ by looking at '/proc/interrupts' and lspci.

Do you think that installing a realtime kernel can really change the things?

This is mine: 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT x86_64 x86_64 x86_64 GNU/Linux
cpu dual core duo T8100 2.10 GHz

Could you please suggest me any other improvement just to avoid the xruns?

---

### Post by CrocoDuck on 2012-08-25
Hi. I had a similar issue. Here the solution: [http://ubuntuforums.org/showthread.php?t=1976254 .]("http://ubuntuforums.org/showthread.php?t=1976254")
You can find a solution here too: [http://ubuntuforums.org/showthread.php?t=2045576](http://ubuntuforums.org/showthread.php?t=2045576)
[]("http://ubuntuforums.org/showthread.php?t=1976254")

---

### Post by DARKAD on 2012-08-29
Thank you CrocoDuck,

I arranged some more changes by this two sites:

[https://github.com/koppi/renoise-refcards/wiki/HOWTO-fine-tune-realtime-audio-settings-on-Ubuntu-11.10]("https://github.com/koppi/renoise-refcards/wiki/HOWTO-fine-tune-realtime-audio-settings-on-Ubuntu-11.10")

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration")

And it works better!

---

