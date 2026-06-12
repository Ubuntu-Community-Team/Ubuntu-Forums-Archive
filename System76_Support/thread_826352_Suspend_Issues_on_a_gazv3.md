---
title: "Suspend Issues on a gazv3?"
date: 2008-06-11
forum: System76 Support
---

### Post by andyanderso on 2008-06-11
First of all thanks to all the folks at System76.  You guys are great. 

Now to my question.  I just recently (in the last few months became interested in using the suspend function on my Gazelle Value laptop. The computer will go to sleep just fine and seems like it wakes up but the screen never comes back on.  I tried the brightness keys and I tried changing my acpi-support file (I saw this might work in another post) and nothing seems to work so far.  Has anyone got any ideas?  I pasted a copy of my acpi-support file into the bottom of this post.  Here is the info on my kernal:
[INDENT]andy@hermes:~$ uname -a
Linux hermes 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
[/INDENT]
My system76 driver is version 2.2.1
I have a gazv3 running Ubuntu Hardy Heron 64bit ....

any help?
[INDENT]
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12[/INDENT]

---

### Post by thomasaaron on 2008-06-12
Just tried suspend on a GazV3 with a fresh install of 64-bit hardy and it worked like a charm out of the box. Here is the acpi-support file it has.


# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
#SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by andyanderso on 2008-06-16
I made my acpi-support file look just like the one below and still my system will not wake back up.

I am also running a fresh install of the 64 bit hardy...

any other thoughts? 

andy

> **thomasaaron said:**
> Just tried suspend on a GazV3 with a fresh install of 64-bit hardy and it worked like a charm out of the box. Here is the acpi-support file it has.


# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
#SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by thomasaaron on 2008-06-16
I tried looking for your name in our database so that I can examine your configuration, but I don't see you in there (or at least what I'm guessing your name is by virtue of your ubuntu handle.

DON'T post your name or order# here. But either post more detail about your configuration here (CPU, RAM, in particular). Or email me with your name or order number.

One other thing to try: Go to System > Preferences > Appearance > Visual Effects and turn off your desktop effects to see if it will suspend and resume.

---

### Post by andyanderso on 2008-06-17
Thanks for the help. I tried turning off my desktop effects but to no avail.  Still will not resume from suspend. I sent you a private message through the forum with my name and order #.
Here is some info on my machine -->

-Computer-
Processor		: 2x Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
Memory		: 1020MB (690MB used)
Operating System		: Ubuntu 8.04
Date/Time		: Tue 17 Jun 2008 01:57:32 PM MDT
-Display-
Resolution		: 1280x800 pixels
OpenGL Renderer		: Mesa DRI Intel(R) 945GM 20061017
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 PC Speaker
 Power Button (FF)
 Lid Switch
 Power Button (CM)
 Sleep Button (CM)
 Video Bus
 SynPS/2 Synaptics TouchPad
-Printers (CUPS)-
PDF
-IDE Disks-
-SCSI Disks-
ATA HTS541010G9AT00
TSSTcorp CD/DVDW TS-L632D



> **thomasaaron said:**
> I tried looking for your name in our database so that I can examine your configuration, but I don't see you in there (or at least what I'm guessing your name is by virtue of your ubuntu handle.

DON'T post your name or order# here. But either post more detail about your configuration here (CPU, RAM, in particular). Or email me with your name or order number.

One other thing to try: Go to System > Preferences > Appearance > Visual Effects and turn off your desktop effects to see if it will suspend and resume.

---

### Post by arch_o_median on 2008-06-25
Hi Andy.
   I have a very similar problem, and system (Gazelle Performance 3, some system details listed in my signature). I was wandering if the thread you mentioned that had the suggestions about altering acpi-support was this one:  

[http://ubuntuforums.org/showthread.php?t=350265&highlight=acpi-support+suspend](http://ubuntuforums.org/showthread.php?t=350265&highlight=acpi-support+suspend)

  or if there's another more relevant one?

  Have you found an acpi-support configuration that allows any version of suspend?

---

### Post by andyanderso on 2008-07-03
I tried as many combinations of the settings mentioned in that post as I could and never got my suspend to work.

Have you found anything that works?  

> **arch_o_median said:**
> Hi Andy.
   I have a very similar problem, and system (Gazelle Performance 3, some system details listed in my signature). I was wandering if the thread you mentioned that had the suggestions about altering acpi-support was this one:  

[http://ubuntuforums.org/showthread.php?t=350265&highlight=acpi-support+suspend](http://ubuntuforums.org/showthread.php?t=350265&highlight=acpi-support+suspend)

  or if there's another more relevant one?

  Have you found an acpi-support configuration that allows any version of suspend?

---

### Post by arch_o_median on 2008-07-03
Hi Andy.   I've changed to a 64-bit kernel by install from liveboot CD and changed some other things.  I am able to hibernate by running the hibernate.sh script as sudo.   Unfortunately I do not have that system available and will not until July 17.  When I _do_ get it back I will update this info.

---

### Post by AusIV4 on 2008-07-09
I also have a Gazelle V3 that I have been unable to suspend in Hardy. It hasn't been much of a concern to me, as I encrypt my hard drive and hibernate to my encrypted swap (suspending would basically leave my hard-drive unlocked all the time), but I would like to see a solution to suspend in case I'm just carrying my laptop from one room to another or something.

Gazelle Value 3
Core 2 Duo 2.0 Ghz
1.5 GB RAM
64 bit Hardy

---

### Post by thomasaaron on 2008-07-09
OK, could you guys post the output of...

swapon -a

and 

cat /etc/fstab

---

### Post by AusIV4 on 2008-07-10
```
swapon -a
```Produces no output.
```
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/mapper/AusIVPortable-root_1

UUID=1a698c8c-8201-4f70-9e93-c8ce59288311 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1

UUID=5c6ef2fa-4bac-4849-9616-e46fb84310f9 /boot           ext3    defaults        0       2

# /dev/mapper/AusIVPortable-home

UUID=749b565b-b5ec-4a82-876f-0559593ae566 /home           ext3    defaults        0       2

# /dev/mapper/AusIVPortable-swap

UUID=73a30d89-b521-4ee5-872a-e70c2f4e30e9 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```I encrypt my system, which is why root, home, and swap are in /dev/mapper.

To be clear, hibernate works just fine. Suspending to RAM is where I have problems.

---

### Post by andyanderso on 2008-07-17
Here is what I get:
> **thomasaaron said:**
> OK, could you guys post the output of...

swapon -a

[INDENT]andy@hermes:~$ swapon -a
andy@hermes:~$ 
[/INDENT]
> **thomasaaron said:**
> and 

cat /etc/fstab

[INDENT]andy@hermes:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2e6b3a31-9318-45e8-813e-c29352f7c915 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d63db41e-0419-405d-99f0-18001eb17c0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
andy@hermes:~$ 
[/INDENT]

Thanks for trying to help with this.

Andy

---

### Post by andyanderso on 2009-01-20
Anyone solved this issue yet?  I am still having trouble getting suspend and hibernate to work...

---

### Post by thomasaaron on 2009-01-20
What version are you running now?
And is it 32-bit or 64-bit?
If 32-bit, have you tried 64-bit?

---

### Post by andyanderso on 2009-01-20
Running 8.10 64 bit.

here are the outputs from "swapon -a, cat /etc/fstab/, and uname -a"
```
andy@hermes:~$ swapon -a
andy@hermes:~$ 
andy@hermes:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2e6b3a31-9318-45e8-813e-c29352f7c915 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d63db41e-0419-405d-99f0-18001eb17c0d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
andy@hermes:~$ uname -a
Linux hermes 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
andy@hermes:~$ 
```

Also here is my acpi-support file:
> #
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf.  

---

### Post by andyanderso on 2009-02-26
Has anyone else made any progress on this issue? 

I have tried a few more things the I found in the Ubuntu forums:
1. A fresh intrepid 64 bit install. - No luck
2. Changed the video section of the xorg config file to look like this:
> Section "Device"
	Identifier	"Configured Video Device"
        Driver          "intel"
to try and make sure the computer saw the intel driver.
3. Fiddled with the settings in the acpi-suppport file changed these:
> SAVE_VBE_STATE=true
POST_VIDEO=true
ENABLE_LAPTOP_MODE=true
ACPI_SLEEP_MODE=standby
4. Added these lines to the /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux file after this line "elif ! env | grep -q HAL_PROP_POWER_MANAGEMENT_QUIRK; then" per this forum thread [http://ubuntuforums.org/showthread.php?t=991403&highlight=suspend+quirk](http://ubuntuforums.org/showthread.php?t=991403&highlight=suspend+quirk) :
> HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_BIOS=true
HAL_PROP_POWER_MANAGEMENT_QUIRK_S3_MODE=true
HAL_PROP_POWER_MANAGEMENT_QUIRK_DPMS_SUSPEND=true

So far nothing seems to work. I still get the black screen of death after I try to resume from suspend. I will also post an update to [this bug]("https://bugs.launchpad.net/system76/+bug/271806") with what I have tried.

on different note I know that this is an old problem and that most of the machines affected by it are probably no longer have the paid support that folks bought with the computer. Even still you guys at system76 seem to be spending your time on helping with this. How could those of us affected by this bug help out more? Pay for some of your time? With some direction maybe we could put a more systematic approach into debugging this (ie more of our time volunteered)? anyway just some thoughts.  I hope we can all figure this out. I know I would like to have suspend.

---

