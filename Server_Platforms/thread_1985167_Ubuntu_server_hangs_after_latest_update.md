---
title: "Ubuntu server hangs after latest update"
date: 2012-05-22
forum: Server Platforms
---

### Post by hoodwink55 on 2012-05-22
I'm running server 11.10 64bit on a Gigabit board, amd proc, ATI chipset. I'm a nube, so I use Webmin to admin the server...so far so good. Nothing major going on with it, just a home file/media server. Anyway, today it popped up w/ 3 updates (sorry for the crappy memory) and I do believe that one of them was to the kernel. It finished all the updates w/ no errors. I had to shut down the server because I needed to do some electrical work (turning off/on breakers) in the house. I used Webmin's web button to shut it down. Everything seemed to be halted (said so), but never turned off the server...so I held down the power button to force it along (I know...not the way to do it but had to get jobs done). Fast fwd a few hours later, turn everything back on, and the server hangs after the following:

Begin: Running /scripts/init-bottom ... done.
done.
[    15.598705] SP5100 TCO timerr: mio address 0xfec000f0 already in use
[    77.024119] r600_cp: Failed to lead firmware "radeon/RS780_pfp.bin" [    77.024155] [drm:r600_startup] *ERROR* Failed to load firmware!
[    77.024187] radeon 0000:01:05.0: disabling GPU acceleration

...and then it just hangs there :confused:
I've try all the "Previous Linux versions"...no go..
Also, I've tried to boot off of 11.10 & 12.04 cd's, "F12", asks me which device, I select "CD" and goes and stops at the famous "GNU GRUB version 1.99-12ubuntu5" screen and sits there...no count down...I have to hit enter. Could it be hardware related...it's a new system.

Please help!
Thanks

---

### Post by hoodwink55 on 2012-05-23
Bump..

---

