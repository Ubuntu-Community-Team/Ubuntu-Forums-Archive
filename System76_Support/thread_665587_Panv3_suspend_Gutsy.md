---
title: "Panv3 suspend Gutsy"
date: 2008-01-12
forum: System76 Support
---

### Post by Zxaos on 2008-01-12
I've been running into a problem running suspend on my panv3. Ever since installing Gutsy, when I go to suspend the machine appears to suspend correctlly (screen turns off, power light remains flashing like it had been in feisty)

However, when I go to resume using the machine, the screen lights up and displays "Linu" followed by a flashing cursor. It stays there indefinitely until I power off the machine with the power switch again. After that, it boots cleanly, as if it had been shut down normally.

Any thoughts?

---

### Post by thomasaaron on 2008-01-14
I've seen that a number of times in the past. I'm sick at home today, so I don't have access to my notes.

Are you running the /etc/default/acpi-support configuration that came with the machine? It should look pretty much like this.

```

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
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

---

### Post by Zxaos on 2008-01-14
Yep, my version of that file is identical to that.

---

### Post by thomasaaron on 2008-01-14
I'll try to re-create the problem when I get back in the office tomorrow.
It is a fairly common bug. See this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/13747s](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/13747s)

I believe it is either a module or a swap issue, though.
What is the output of swapon -s

---

### Post by Zxaos on 2008-01-15
That link is not working :)

The output of swapon -s is 
```
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       2441840 34864   -1

```

---

### Post by thomasaaron on 2008-01-15
Sorry. I must've clipped the link or something. Anyway a quick google search pulled these up.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81548](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81548)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg477780.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg477780.html)

I'm trying to re-create the problem. 

Are you using the image that came on the machine (+ upgrading to Gutsy) or have you put a fresh image on it at some point?

(Regarding the swapon -s, I just wanted to make sure your swap partition was in place. Looks like it is.)

---

### Post by Zxaos on 2008-01-15
I put a fresh Gutsy install on after it was released, and then used the System76 driver.

If I recall correctly, it needed some fiddling to work correctly even on the Feisty image that shipped with the machine. However, I don't recall what changes were made, though.

---

