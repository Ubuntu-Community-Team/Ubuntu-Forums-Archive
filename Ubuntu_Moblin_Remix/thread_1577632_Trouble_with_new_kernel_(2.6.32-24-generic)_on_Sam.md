---
title: "Trouble with new kernel (2.6.32-24-generic) on Samsung NP-N130"
date: 2010-09-19
forum: Ubuntu Moblin Remix
---

### Post by U-95 on 2010-09-19
Greetings. I've a Samsung NP-N130 in which I installed first the version 9.04 and when it was released the 10.04. I've no complaints, except for this, that caused the system to freeze and to be unable to respond during roughly 30 seconds, a few minutes after starting/exiting of suspend mode/etc:

[  248.655855] Monitor-Mwait will be used to enter C-2 state
[  248.655886] Marking TSC unstable due to TSC halts in idle
[  248.660387] Switching to clocksource hpet
[  286.816160] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  286.816184] ata1.00: failed command: WRITE DMA
[  286.816212] ata1.00: cmd ca/00:08:4f:95:bf/00:00:00:00:00/e7 tag 0 dma 4096 out
[  286.816218]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[  286.816232] ata1.00: status: { DRDY }
[  291.856087] ata1: link is slow to respond, please be patient (ready=0)
[  296.840090] ata1: device not ready (errno=-16), forcing hardreset
[  296.840115] ata1: soft resetting link
[  297.022573] ata1.00: configured for UDMA/133
[  297.022594] ata1.00: device reported invalid CHS sector 0
[  297.022630] ata1: EH complete

I know this alredady has been commented here. I found a repository especifically for that netbook and installing the kernel version that is there I was able to get rid of that -at least, usually-; instead making a dmesg just appeared an inoffensive "clearing spurious IRQ".

The problem is that yesterday I installed the last kernel (2.6.32-24-generic) via the update manager and with it the above problem has returned. Until it can be patched, do you know how I can return to the previous kernel? (2.6.32-23 I think)

---

### Post by Peter-E on 2011-02-05
> **U-95 said:**
> Greetings. I've a Samsung NP-N130 ...

The problem is that yesterday I installed the last kernel (2.6.32-24-generic) via the update manager and with it the above problem has returned. Until it can be patched, do you know how I can return to the previous kernel? (2.6.32-23 I think)

I have the same issue with this netbook. Currently I use UNE 10.04 with kernel 2.6.32-28 and the issue still exists. I did not use 9.04 and I know that with other Linux distros this issue is reported too. I upgraded to the latest (NC06) bios but the problem still exists...:confused:

You can accurately time the issue by starting the sound recorder and make a recording just after system startup. Watch the progression counter time to freeze and continue after 42 seconds. I listened to the recording, during the missing time on replay there is a 42 second silence "gap" I searched the fora all over but a convincing solution was not found, neither a pinpoint on what exactly causes this issue in Linux and not in Windows. 

I have a hunch that this bug is so machine sprecific that only a very skilled kernel guru can crack this issue but if it ends up needing to rebuild the kernel after each upgrade we might as well learn to live with it...

Regards,
Peter

---

