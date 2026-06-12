---
title: "serp6 Serval Professional wont boot after required restart"
date: 2010-09-18
forum: System76 Support
---

### Post by lagesvantner on 2010-09-18
I just got my Serval a few days ago and it was working beautifully.  Battery life was far shorter than I had expected but that was the only annoyance I came across.  Last night however, I was running update manager to upgrade my system and the last upgrade I ran included packages for the linux kernal (I dont remember what version(s) of the kernal it was for, but I am assuming it was one of the more recent ones).  I was told that a restart was required, so when I was finished with everything I ran the restart.  What happened was that my monitor displayed a black screen with a flashing underscore in the top-left corner.  The system never shut down and after a few hours I had no option other than a hard shutdown.  Then when I tried to turn it on my monitor displayed the same black screen after running through BIOS.  I enabled "system beep on bootup" (wording might be off a bit, but there is an option in system utilities after pressing f2 in the s76 splash page that causes the system to beep when the BIOS boots the OS).  After restarting the system and letting the BIOS run I heard the beep that is supposed to signify that the OS is being loaded, however after that beep I am shown a black screen with a flashing underscore in the top-left corner.  Any suggestions?

---

### Post by UberGeekInc on 2010-09-25
Same issue here.  I'm on a Lemur2, x86_64, doing beta testing for 10.10. Error is on: 

  /opt/system76/system76-driver/src/uvc_kernel_update.py

Here is my apt-get upgrade output:

Setting up linux-headers-2.6.35-22-generic (2.6.35-22.33) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/header_postinst.d/uvcinstall 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
python: can't open file '/opt/system76/system76-driver/src/uvc_kernel_update.py': [Errno 2] No such file or directory
run-parts: /etc/kernel/header_postinst.d/uvcinstall exited with return code 2
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-22-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-headers-2.6.35-22-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeff@Gimli:~$ uname -a
Linux Gimli 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:18:18 UTC 2010 x86_64 GNU/Linux

Removing the System76 driver should do the ticket.  I'm gonna try that myself in a few moments.  (gonna backup first :-))

---

### Post by UberGeekInc on 2010-09-25
Followup to my earlier message.

System76 driver was not installed, it got removed on the 10.04->10.10 upgrade process.  Yet it left several pyc files.  Removing /opt/system76/ does not fix the problem - same error on upgrade.

IMO this is a system76 driver bug, as it left configuration that breaks the kernel-header upgrade.

Won't boot my system until this is resolved.  :-/

---

### Post by UberGeekInc on 2010-09-25
Oh - reinstalling System76 Driver did not fix the problem.

---

### Post by isantop on 2010-09-27
Actually, this sounds like a weird Grub problem. Check [these](http://knowledge76.com/index.php/Restore_Grub_Bootloader) instructions for reinstalling Grub to see if that clears it up.

---

