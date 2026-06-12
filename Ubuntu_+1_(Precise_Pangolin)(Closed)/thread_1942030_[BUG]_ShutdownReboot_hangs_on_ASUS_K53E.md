---
title: "[BUG] Shutdown/Reboot hangs on ASUS K53E"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Helios747 on 2012-03-16
Hello, I copied the template from the bug report thread but made a new thread because I was hoping somebody could give me a workaround.


**Bug Short Description:** When shutting down/rebooting via GUI or terminal, system hangs at shutdown splash screen.

**How to Reproduce the bug**: Shutdown via GUI or Terminal.

**Current behavior:** Appears to just hang at the shutdown splash. The animation just freezes.

Attachments: (image, code, files that can contribute to understanding the bug, if any);

**Platform tested: (Ubuntu flavor, related software / package versions, hardware involved, if relevant); **

Ubuntu 12.04 B1 - Latest updates

**Workaround: (only if known by the poster. Full workaround in CODE (for code) or QUOTE (for other procedures) tags. Not a long tutorial targeted at users. A working/usable fix. No external link to workarounds unless really needed (download of package, etc), so one can rapidly learn how to solve the problem when reading this sticky;**

None yet.

Link to Discussion Thread: (if it exists. Full U+1 link, so we can easily click it to open);

Link to Bug Report: (full launchpad link, so we can easily click to open it);

Bug Report Status: (will fix, will not fix, if the status is known and there is a Launchpad report);

**Bug status: (Fixed, Not Fixed, if the status is known and there is a Launchpad report).**

Not fixed.


Also, how would I report this in Launchpad? Normally bug reports would need a bit more information than "It doesn't work lol". But, I just don't know how to get more information in this case.

---

### Post by Gompa on 2012-03-18
did you try the kernel parameter 
reboot=efi

or you could try
reboot=bios

---

### Post by lucazade on 2012-03-18
and also:
acpi=off

try also to completely disable plymouth splashscreen to have more verbosity at startup/shutdown.. You can disable it by removing 'splash' and "vt.handoff=7" from kernel params.
this way you should have a clearer situation of what is happening and what is not working properly.

---

### Post by effenberg0x0 on 2012-03-18
Helios747, please try the procedure I proposed at [http://ubuntuforums.org/showthread.php?t=1916751](http://ubuntuforums.org/showthread.php?t=1916751) . That script is known ro work for most people with current ASUS hardware.

Regards,
Effenberg

---

### Post by dino99 on 2012-03-18
i've not the shutdown issue but only the reboot on a P5wdh. 
Lately Precise have received some updates to get around ([https://bugs.launchpad.net/ubuntu/oneiric/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/oneiric/+source/network-manager/+bug/869635)) but if shutdown verbose mode seems clean now, there is still some issue like reboot. Sometimes it want to reboot while shuting down even if reboot have not been requested.
Looks like some race conflicts and i should say that the system is still not shut down completly (often got complaint about the usb hub). The next reboot immediatly stop as it was receiving a close order after picking a boot line, or fail with a kernel panic, etc.

So i'm hesitating to blame either the asus bios or the microcode from intel, or both.
A quick research on launchpad about "kernel panic" let you know that many users have such trouble.

---

### Post by Gompa on 2012-03-18
did you update your kernel lately ? if i remember correctly a new kernel got released yesterday

---

### Post by Helios747 on 2012-03-18
Wow! I was just about to bump this! Heh.

Updated to latest packages as of 12:30pm PDT.

Still not working.

Tried your script effenberg0x0, shutdown works!

Suspend still doesn't, which is weird, since that's what the script was for! hahaha. I'll make a post in that specific thread.

Marking this as solved. Thanks for the help!

---

### Post by Helios747 on 2012-03-19
bump.

Unfortunately that script did not solve my problem and I'm back to square one. I have no idea why shutdown randomly worked that one time.

Is there a shutdown log stored somewhere that I can post?

---

