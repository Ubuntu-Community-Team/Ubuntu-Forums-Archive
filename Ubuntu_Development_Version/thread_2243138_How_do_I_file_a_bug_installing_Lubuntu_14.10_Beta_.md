---
title: "How do I file a bug installing Lubuntu 14.10 Beta for PPC"
date: 2014-09-06
forum: Ubuntu Development Version
---

### Post by wouterlippe on 2014-09-06
I cannot find how to file a bug during installation (booting from the installation dvd). The problem is during the boot process so I cannot use ubuntu-bug.
What I did was: I created a dvd from the Lubuntu 14.10 iso from the 20140906 build. I tried to start my iBook G3 600Mhz with it.
I tried "
[FONT=Helvetica]boot: live[/FONT]
[FONT=Helvetica]Please wait, loading kernel…[/FONT]
[FONT=Helvetica]Claim error, can’t allocate e00000 at 0x2000000[/FONT]
[FONT=Helvetica]Claim error, can’t allocate kernel memory[/FONT]
[FONT=Helvetica]boot: _"
[FONT=tahoma]I have also tried several of the other options but got the same result.
[/FONT][/FONT]
[FONT=tahoma][/FONT]

---

### Post by howefield on 2014-09-06
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by wouterlippe on 2014-09-08
I tried another option. I installed Lubuntu 14.04.1 and upgraded to 14.10 using update-manager. After the reboot I got the same message as with the installation dvd:

[FONT=Helvetica]boot: Linux[/FONT]
[FONT=Helvetica]Please wait, loading kernel…[/FONT]
[FONT=Helvetica]Claim error, can’t allocate e00000 at 0x2000000[/FONT]
[FONT=Helvetica]Claim error, can’t allocate kernel memory[/FONT]

I could boot using:

boot: old

This booted using the Lubuntu 14.04.1 kernel (3.13.0-35-powerpc-smp). The kernel that didn't boot was version 3.16.0-13-powerpc-smp.
Yesterday update-manager delivered a new kernel (3.16.0-14-powerpc-smp) which had the same problem as the previous one (same error message).
My hardware: iBook G3 600Mhz 640Mb

---

