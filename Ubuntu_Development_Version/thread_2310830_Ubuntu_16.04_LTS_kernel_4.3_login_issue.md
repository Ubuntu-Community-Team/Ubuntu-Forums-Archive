---
title: "Ubuntu 16.04 LTS kernel 4.3 login issue"
date: 2016-01-22
forum: Ubuntu Development Version
---

### Post by globetrotter-roma on 2016-01-22
Ubuntu 16.04 LTS
kernel 4.3.x.xx
Acer Aspire 5610

Video memory corruption.
A black window partially cover the login area after boot. Change video memory size don't give effect to the issue.
Work well until kernel 4.2.0-19                 

Tks ciao ):P

---

### Post by dino99 on 2016-01-22
you should enabled the 'proposed' archive if it is not yet done (via synaptic), then update/upgrade and boot with 4.4 kernel
then check for possible error(s) by running 'journalctl' into a terminal (errors are listed with red lines, warnings/custom settings with brighten white lines)

---

### Post by globetrotter-roma on 2016-01-22
In kernel 4.3 is impossible to work more then login.
In kernel 4.2 no error were log, everything works fine

---

### Post by MikeMecanic on 2016-01-22
Let's try something but first copy/paste the Grub settings content. Open the terminal and run this command line:

```

gksu gedit /etc/default/grub
```
Enter your password 

Up to black screen,do you see Ubuntu boot image and/or boot messages (loading services)?  Are you on an upgrade or a fresh install?

---

### Post by globetrotter-roma on 2016-01-25
Thank for your suggest, but in last working kernel (4.2) no bug or issues are present in logs, and in last kernels 4.3.0-x
 it's impossible to open a terminal because the huge black window that cover 80% of screen :-(
I'm on upgraded system.

---

### Post by globetrotter-roma on 2016-01-25
> **MikeMecanic said:**
> Let's try something but first copy/paste the Grub settings content. Open the terminal and run this command line:

```

gksu gedit /etc/default/grub
```
Enter your password 

Up to black screen,do you see Ubuntu boot image and/or boot messages (loading services)?  Are you on an upgrade or a fresh install?

This is for 4.2 kernel:


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by MikeMecanic on 2016-01-25
Nothing abnormal there. In Vivid I was having the same issue.  In Ubuntu, when the boot sequence is complete we ear a sound when login screen opens.  Try to create a user account with no password in 4.2.  Shut down from this account and then turn on the computer.  After the sound you should be able to login by pressing enter.  
That's how I get rid of that bug and on the first login the black screen was gone after.
You may also wanna try automatic login to see if you can load 4.3.

---

### Post by globetrotter-roma on 2016-01-26
I can boot and login on 4.3 but black window overlay the 80% of the desktop so i'm able to do nothing ;-(

---

### Post by globetrotter-roma on 2016-02-08
Issue solved with kernek 4.4
Tks to all

---

