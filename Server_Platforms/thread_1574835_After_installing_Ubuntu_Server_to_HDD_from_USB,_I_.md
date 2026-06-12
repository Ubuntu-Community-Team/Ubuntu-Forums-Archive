---
title: "After installing Ubuntu Server to HDD from USB, I can only boot with the USB in"
date: 2010-09-14
forum: Server Platforms
---

### Post by soulspit on 2010-09-14
Hi everyone,

I want to turn an old laptop (one that worked flawlessly with Ubuntu until the graphics card fried - it can still do VGA graphics though) into a server for files and perhaps, at some point, hosting my web site.  I installed the latest 32-bit Ubuntu server edition from a USB drive, and the install went fine but I can't boot up my computer from the hard drive - I just get a blinking cursor, and no GRUB even if I hold shift while booting up.

If I boot from the USB, however, the installation works, even though I know that I installed it to the hard drive - once I have booted up, I can remove the USB drive and access everything on the hard drive and see that this is, indeed, where the server has been installed.  I'm guessing that somehow, GRUB or something boot-related ended up on the USB drive, so that I can only boot the hard drive by telling the BIOS to boot from the USB, which then points everything towards the hdd.  During the installation it asked me if I wanted to overwrite the master boot record, and I said yes (because the server will be the only OS on the computer) - do you think somehow this put the boot record on the USB drive?

I don't know that much about boot records, but since the server runs fine off the hard drive when I boot from the USB, I'm assuming the problem is boot related.  Searched google and the forums for people with similar problems but couldn't find any.  CD drive on my computer is broke so I can't install from a disc.  Any help would be appreciated.  Thanks!

---

### Post by soulspit on 2010-09-15
Bump!  Hasn't anyone seen this problem before?

---

### Post by arrange on 2010-09-15
Can you post the output of the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"). (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)
WITH the USB attached?

---

### Post by oldfred on 2010-09-15
It is probably this. If not post boot info script as above.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by soulspit on 2010-09-15
Thanks for the responses guys - yeah, it definitely was a variation of the problem in the SourceForge article.  I don't know if this is a bug in the guided installation, but certainly when it asked me "do you want GRUB installed to the MBR?" and I said yes, it went for the external drive the installation was being run off of, instead of the internal drive it was being installed on.

I'm not particularly savvy with this stuff yet, so I went with what seemed like the easier option of re-installing from my occasionally-functioning CD drive instead of trying to fix the install or doing an advanced installation.  The CD drive held up long enough to install, and clearly there was only one MBR for GRUB to be written onto, and so everything works as it should now.  The good and bad thing about Linux, for me, is that everything is a learning experience - thanks for your help.

---

