---
title: "Recovery Mode In Dapper Drake"
date: 2006-10-03
forum: Sun Sparc Users
---

### Post by shawnerz on 2006-10-03
All,
How do I get into the ability to boot into "recovery" mode?
I'm running a SunBlade 100, OpenBoot 4.5.

A friend went to configure Apache and wanted to "fix" the "problem" of not having the root account enable.  He edited the /etc/sudoers file and messed it up in the process.  Now, my admin account can't 'sudo' anything.
My plan is to reboot into recovery mode, then run "aptitude reinstall sudo."

Thanks,
-Shawn

---

### Post by dcaonbireal on 2006-10-04
write out everything that it says on the error and i can help

---

### Post by shawnerz on 2006-10-04
I'm not sure how this will help, but here it is:
>>> sudoers file: syntax error, line 0 <<<
sudo: parse error in /etc/sudoers near line 0

The file is crrupt and I need to replace it.  From what I read, I need to reboot into recovery mode.  How do I get into recovery mode?
-Shawn

---

### Post by shawnerz on 2006-10-04
More specifically, I need to know, when I'm at the OpenBoot prompt, what command line options do I pass to Ubuntu so it will come up in recovery mode?
Most Linux installations have GRUB.  GRUB allows you to select which mode to boot in to.
On a Sun, you have OpenBoot.  OpenBoot gives you a prompt saying "boot" and you have to pass the parameters.
I tried vmlinuz=recovery" and a few other variations.  Nothing worked.
Any ideas?
-Shawn

---

### Post by calixtine on 2006-10-04
Do you mean single-user mode? This will dump you at a console root prompt without the need for a password.

To do this you need to get to the SILO prompt which looks like 
```
SILO Version 1.4.10
boot:
```
and type 
```
Linux single
```

OpenBoot is the equivalent of the BIOS on an i386 system, whereas SILO is the sparc equivalent of GRUB/LILO.

hth,
Andy

---

### Post by shawnerz on 2006-10-04
I was able to fix my own problem.  It is actually called "Rescue" mode.  To get into Rescue mode with a SUnBlade, do the following:

Insert the Dapper Drake CD into the CDROM drive.
When OpenBoot starts, press F1 to stop OpenBoot at the "boot " prompt.
Type "halt"
At the "ok " prompt, type "reboot cdrom"
When the computer reboots, OpenBoot will stop waiting for an input.  Type "rescue"
The next screens will be the same as the initial installation screens, (keyboard tyoe, language, etc) but you will notice "Rescue" in the top left of the screen.
After hardware detection, you will be asked which partition to mount as the root partition.
Select the partition and then select the 'shell' option.  You will then be in the shell and have a prompt so you can make your changes.

Good luck.
-Shawn

---

