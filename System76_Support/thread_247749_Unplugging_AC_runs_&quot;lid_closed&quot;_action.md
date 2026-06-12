---
title: "Unplugging AC runs &quot;lid closed&quot; action"
date: 2006-08-31
forum: System76 Support
---

### Post by lord trousers on 2006-08-31
Pangolin Value, normal setup + buncha apps installed.

When I unplug the AC, gnome-power-manager runs the action associated with closing the lid whether the lid is closed or not. If it helps, here's /var/log/acpid from when I unplug the AC to when I move the mouse to turn the screen back on:

```
[Thu Aug 31 02:38:11 2006] received event "ac_adapter AC0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 31 02:38:11 2006] BEGIN HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] END HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] action exited with status 0
[Thu Aug 31 02:38:11 2006] completed event "ac_adapter AC0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 31 02:38:11 2006] BEGIN HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] END HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] action exited with status 0
[Thu Aug 31 02:38:11 2006] completed event "battery BAT0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] received event "hotkey ATKD 00000057 0000000e"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] completed event "hotkey ATKD 00000057 0000000e"
[Thu Aug 31 02:38:11 2006] received event "ac_adapter AC0 00000080 00000000"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 31 02:38:11 2006] BEGIN HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] END HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] action exited with status 0
[Thu Aug 31 02:38:11 2006] completed event "ac_adapter AC0 00000080 00000000"
[Thu Aug 31 02:38:11 2006] received event "battery BAT0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] executing action "/etc/acpi/power.sh"
[Thu Aug 31 02:38:11 2006] BEGIN HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] END HANDLER MESSAGES
[Thu Aug 31 02:38:11 2006] action exited with status 0
[Thu Aug 31 02:38:11 2006] completed event "battery BAT0 00000080 00000001"
[Thu Aug 31 02:38:11 2006] received event "processor CPU1 00000080 00000000"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] completed event "processor CPU1 00000080 00000000"
[Thu Aug 31 02:38:11 2006] received event "processor CPU1 00000081 00000000"
[Thu Aug 31 02:38:11 2006] notifying client 4714[108:108]
[Thu Aug 31 02:38:11 2006] completed event "processor CPU1 00000081 00000000"
```

---

### Post by crichell on 2006-08-31
That's an interesting one - I'll get to playing with it.  What do your power management settings look like?  (/etc/default/acpi-support & settings in the System > Preferences > Power Management)

---

### Post by lord trousers on 2006-08-31
New data: it only does this if the lid has been closed and reopened since logging in. It might be that  gnome-power-manager doesn't poll /proc/acpi/button/lid/*/state like /etc/acpi/lid.sh does (I've verified that this always has the correct value), but uses some other, less reliable mechanism.

Here's my ~/.gconf/apps/gnome-power-manager/%gconf.xml:

```
<?xml version="1.0"?>
<gconf>
        <entry name="action_ac_button_lid" mtime="1157012963" type="string">
                <stringvalue>blank</stringvalue>
        </entry>
        <entry name="lock_use_screensaver_settings" mtime="1156464795" type="bool" value="true">
        </entry>
        <entry name="lock_on_suspend" mtime="1156464790" type="bool" value="false">
        </entry>
        <entry name="lock_on_hibernate" mtime="1156464789" type="bool" value="false">
        </entry>
        <entry name="lock_on_blank_screen" mtime="1156464789" type="bool" value="false">
        </entry>
        <entry name="ac_sleep_display" mtime="1156017583" type="int" value="600">
        </entry>
        <entry name="can_hibernate" mtime="1156464776" type="bool" value="true">
        </entry>
        <entry name="action_sleep_type" mtime="1154910698" type="string">
                <stringvalue>suspend</stringvalue>
        </entry>
        <entry name="battery_sleep_computer" mtime="1154910667" type="int" value="1800">
        </entry>
        <entry name="action_battery_button_lid" mtime="1157013265" type="string">
                <stringvalue>blank</stringvalue>
        </entry>
        <entry name="can_suspend" mtime="1157013180" type="bool" value="true">
        </entry>
        <entry name="action_button_suspend" mtime="1154910315" type="string">
                <stringvalue>suspend</stringvalue>
        </entry>
        <entry name="display_icon_policy" mtime="1154378313" type="string">
                <stringvalue>always</stringvalue>
        </entry>
</gconf>
```

Here's /etc/default/acpi-support:

```
# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

Too bad all this stuff isn't controlled by a single process.

---

### Post by crichell on 2006-09-01
In addition this only occurs on Asus laptops.  Looks like a bug in gnome-power-manager - we may need to pull together a bug report to get it fixed.

---

### Post by nemik on 2007-09-15
I am experiencing this same problem on my Lenovo Thinkpad T61.

---

### Post by gattanegra on 2008-04-07
):P Hello all!

I have the same problem with my Prestigio Visconte 1300 notebook.
:shock:
It does exactly what you mentioned here : 
When the AC is unplugged it suspends. It is quite annoying.
Please, anyone .. help ?
I can not solve this alone .. 

Thank you!

---

