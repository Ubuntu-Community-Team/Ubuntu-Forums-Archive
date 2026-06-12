---
title: "Laptop randomly boots into black screen"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cecil on 2012-10-04
I did a fresh install of Xubuntu 12.10 Beta2 last night. It works, but it will randomly boot into a black screen, forcing me to force shutdown and boot it back up. The laptop is an HP 2000z-400 with the following specs;

AMD E-300 with Radeon HD Graphics
2GB RAM
320GB HDD

I'm not sure on the model of the Radeon gfx, I know it's integrated into the cpu.

---

### Post by pqwoerituytrueiwoq on 2012-10-04
[LIST]
[*]Integrated Radeon HD 6310 GPU with 80 shader units runs at 488 MHz
[*]Processor supports memory up to DDR3-1066
[/LIST]
have you checked your log files?
```
ls /var/log/Xorg.*
```
using amd's driver or opensource?

---

### Post by Cecil on 2012-10-04
Okay, checking my Xorg.0.log file, first thing that comes at me is a warning that it cannot load the fglrx module, which if I remember right would be the proprietary ATI driver, then an error also saying it can't load it. Then it loads ati_drv.so, which says it has the vendor of X.org Foundation, and searching for the ATI drivers in the software center shows they are not installed, so I'm assuming I have the opensource driver. I'll go ahead and try installing the proprietary ATI fglrx drivers from the software center and see how my laptop acts with those.

---

### Post by Cecil on 2012-10-04
Looks like installing the proprietary driver fixed the problem. Tested by restarting a few times, and shutting it down completely then starting back up. First thing I noticed was now the Xubuntu loading screen appears when it boots up, when before the screen would remain black until it got to the login screen, or it would remain black indefinitely. But it appears to be fixed now. *crosses fingers*

---

### Post by pqwoerituytrueiwoq on 2012-10-04
if you hare having a low resolution issue at boot this is what i did with my nvidia system
[FONT=Courier New]sudo sh -c "echo FRAMEBUFFER=y > /etc/initramfs-tools/modules"[/FONT]
[FONT=Courier New]sudo sh -c "echo scroll=y >> /etc/initramfs-tools/conf.d/splash"[/FONT]
made these changes to this file (my resolution is 1366x768****)
                               ```
~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash** nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap**"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=1366x768
GRUB_GFXPAYLOAD_LINUX=1366x768[/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
[FONT=Courier New]sudo update-grub[/FONT]
[FONT=Courier New]sudo apt-get install v86d;[/FONT]

---

### Post by baizon on 2012-10-05
Got the same problem with two AMD E-450 laptops. Will try pqwoerituytrueiwoq's solution and report.

---

