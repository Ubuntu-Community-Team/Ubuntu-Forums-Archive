---
title: "Gazelle Value Suspend/Hibernate Problems"
date: 2007-06-08
forum: System76 Support
---

### Post by organicveggie on 2007-06-08
I have a Gazelle Value running Feisty 7.0.4 and Beryl. Neither Suspend nor Hibernate work correctly. I followed the instructions here:

[https://bugs.launchpad.net/system76/+bug/108253]("https://bugs.launchpad.net/system76/+bug/108253")

That didn't seem to help. I'm seeing the following behavior:

**Suspend**
[LIST]
[*]Fan kicks into overdrive
[*]At least half of the time it won't come out of suspend.
[*]Most of the time the desktop is MIA when it comes out of suspend. The mouse cursor is visible, but nothing else.
[*]Some times when the desktop is MIA, I can kill X with CTRL+ALT+Backspace and login again.
[*]Wireless adaptor disappears
[/LIST]

**Hibernate**
[LIST]
[*]Fan kicks into overdrive
[*]99% of the time it won't come out of hibernate
[/LIST]

Swap is enabled. Here's the output from swapon:

```
$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       3907864 0       -1
```

And here's the relevant portion from top:

```
top - 16:05:10 up 25 min,  1 user,  load average: 0.26, 0.36, 0.35
Tasks: 123 total,   4 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.2%sy,  0.0%ni, 98.3%id,  0.2%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2075900k total,   813576k used,  1262324k free,    53144k buffers
Swap:  3907864k total,        0k used,  3907864k free,   424088k cached
```

Here's what my *acpi-support* looks like:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
#ACPI_SLEEP_MODE=mem
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel snd_hda_codec"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

Any suggestions?

-Sean

---

### Post by AusIV4 on 2007-06-08
I have a Gazelle value that works fine (for the most part), the only difference that jumped out at me is I have ENABLE_LAPTOP_MODE set to false.

---

### Post by organicveggie on 2007-06-08
> **AusIV4 said:**
> I have a Gazelle value that works fine (for the most part), the only difference that jumped out at me is I have ENABLE_LAPTOP_MODE set to false.

Setting ENABLE_LAPTOP_MODE to false helped a little bit. I can now resume from both suspend and hibernate consistently. However, I'm still having a number of problems:

[LIST]
[*]Fan still goes into overdrive while suspended and just keeps running. Doesn't happen in hibernate.
[*]Wireless adapter on eth1 disappears after resume. Nothing in ipconfig or iwconfig.
[*]The power management software is always confused after resuming. It usually thinks I'm out of battery power and plugging in the power cord doesn't register.
[*]Very sluggish after resuming from suspend. No disk activity, just slow.
[*]Beryl causes some big problems with the display after resuming from both suspend and hibernate. For some reason, the mouse cursor is visible, but nothing else. Restarting X solves the problem. When Beryl is disabled before going into suspend or hibernate, the display works fine after resuming.
[/LIST]

Any thoughts?

-Sean

---

### Post by palintheus on 2007-06-09
You may take a look at these below, these threads have similar problems to some you listed.


> **organicveggie said:**
> 
[*]Wireless adapter on eth1 disappears after resume. Nothing in ipconfig or iwconfig.


[http://ubuntuforums.org/showthread.php?t=425474](http://ubuntuforums.org/showthread.php?t=425474)

> The power management software is always confused after resuming. It usually thinks I'm out of battery power and plugging in the power cord doesn't register.

[http://ubuntuforums.org/showthread.php?t=441353](http://ubuntuforums.org/showthread.php?t=441353)

---

### Post by organicveggie on 2007-06-09
> **palintheus said:**
> You may take a look at these below, these threads have similar problems to some you listed.

Excellent! Another helpful suggestion! Following the discussion in this thread, particularly the 2nd page, fixed my disappearing wireless adapter problem:

[http://ubuntuforums.org/showthread.php?t=425474]("http://ubuntuforums.org/showthread.php?t=425474")

I edited /etc/acpi/resume.d/60-asus-wireless-led.sh and swapped the two "setLEDAsusWireless" lines. The file looks like the following for me now:

```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
#    setLEDAsusWireless 1
    setLEDAsusWireless 0
else
#    setLEDAsusWireless 0
    setLEDAsusWireless 1
fi

```

Unfortunately, while the other link confirmed that other people are having the same problems with power management after resuming, there don't appear to be any solutions forthcoming. This bug:

[https://bugs.launchpad.net/system76/+bug/114932]("https://bugs.launchpad.net/system76/+bug/114932")

is open and "confirmed", but has a low priority and no solution. I know it's not specific to Kubuntu, because I have the stock Gazelle Performance and later I added the Kubuntu packages, since I like to use both Gnome and KDE. The power management problems happen using either window manager and happened before I installed KDE.

The other major problem for me is still Beryl. The mouse cursor is visible after I resume, but nothing else. Very strange and very annoying, since I really like using Beryl and that's part of the reason I sprang for the Gazelle Performance instead of the Value. *sigh* Could it be something with OpenGL? I'm grasping at straws here...

-Sean

---

