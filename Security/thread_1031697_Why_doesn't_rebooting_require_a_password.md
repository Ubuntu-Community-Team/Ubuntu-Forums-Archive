---
title: "Why doesn't rebooting require a password?"
date: 2009-01-05
forum: Security
---

### Post by Endolith on 2009-01-05
If you reboot from the command line, you need to use sudo.

If you reboot from Gnome, you don't.  How does Ubuntu handle permissions so that regular users can reboot from Gnome?

---

### Post by Unparallelogram on 2009-01-06
There's a daemon running somewhere as root that does the actual rebooting when it receives a message. The logic being that you should need root access to reboot remotely, but that if you have physical access to the machine, it should let you reboot because you might as well be pulling the power cord.

---

### Post by jflaker on 2009-01-06
> **Endolith said:**
> If you reboot from the command line, you need to use sudo.

If you reboot from Gnome, you don't.  How does Ubuntu handle permissions so that regular users can reboot from Gnome?

From a terminal, you can access any system to which you NORMALLY would have access to as a user. Take a company network where you should be allowed to login physically at that computer, then you should be granted rights to the terminal.  Requiring root prevents users from dropping machines across a network.

Conversely, physically accessing a system, like was said, If I can't reboot, I can just hold the power button or unplug the system so lets prevent system damage and allow a proper shutdown.

---

### Post by Endolith on 2009-01-06
> **Unparallelogram said:**
> There's a daemon running somewhere as root that does the actual rebooting when it receives a message. The logic being that you should need root access to reboot remotely, but that if you have physical access to the machine, it should let you reboot because you might as well be pulling the power cord.

What daemon?  What signal?

> **jflaker said:**
> From a terminal, you can access any system to which you NORMALLY would have access to as a user. Take a company network where you should be allowed to login physically at that computer, then you should be granted rights to the terminal.  Requiring root prevents users from dropping machines across a network.

Conversely, physically accessing a system, like was said, If I can't reboot, I can just hold the power button or unplug the system so lets prevent system damage and allow a proper shutdown.

Yes, I understand that.  I should have phrased it as a "how" question instead of a "why" question.  I want to know specifically how this system works.  What function or program does the Reboot button call?

---

### Post by cdenley on 2009-01-07
> **Endolith said:**
> What daemon?  What signal?

I believe gnome-power-manager uses HAL to reboot. HAL has a daemon which runs as root. It is a DBUS signal.
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Sending%20commands%20to%20HAL](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Sending%20commands%20to%20HAL)

---

### Post by Endolith on 2009-01-07
> **cdenley said:**
> I believe gnome-power-manager uses HAL to reboot. HAL has a daemon which runs as root. It is a DBUS signal.
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Sending%20commands%20to%20HAL]("https://wiki.ubuntu.com/DebuggingGNOMEPowerManager#Sending%20commands%20to%20HAL")

Ok, that's helpful.  Those commands don't work as a user, though:

```
~> dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Reboot

Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy: org.freedesktop.hal.power-management.reboot-multiple-sessions auth_admin <-- (action, result)

```It also lists this command:

```
gnome-power-cmd.sh reboot
``` which also doesn't work:
```

~> gnome-power-cmd.sh reboot
Rebooting
Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy: org.freedesktop.hal.power-management.reboot-multiple-sessions auth_admin <-- (action, result)
Failed

```gnome-power-cmd.sh just sends a D-Bus signal, too:

[php]#!/bin/sh
# Copyright (C) 2007 Richard Hughes <richard@hughsie.com>
#
# Licensed under the GNU General Public License Version 2
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

#$1 = method name
execute_dbus_method ()
{
    dbus-send --session --dest=org.freedesktop.PowerManagement        \
          --type=method_call --print-reply --reply-timeout=2000    \
          /org/freedesktop/PowerManagement             \
          org.freedesktop.PowerManagement.$1
    if [ $? -ne 0 ]; then
        echo "Failed"
    fi 
}

if [ "$1" = "suspend" ]; then
    echo "Suspending"
    execute_dbus_method "Suspend"
elif [ "$1" = "hibernate" ]; then
    echo "Hibernating"
    execute_dbus_method "Hibernate"
elif [ "$1" = "reboot" ]; then
    echo "Rebooting"
    execute_dbus_method "Reboot"
elif [ "$1" = "shutdown" ]; then
    echo "Shutting down"
    execute_dbus_method "Shutdown"
elif [ "$1" = "" ]; then
    echo "command required: suspend, shutdown, hibernate or reboot"
else
    echo "command '$1' not recognised, only suspend, shutdown, hibernate or reboot are valid"
    exit 1
fi
[/php]See related threads:
 
_[http://ubuntuforums.org/showthread.php?t=935115](http://ubuntuforums.org/showthread.php?t=935115)_[]("http://ubuntuforums.org/showthread.php?p=6514405#post6514405")
[http://ubuntuforums.org/showthread.php?t=772574](http://ubuntuforums.org/showthread.php?t=772574)

---

### Post by Endolith on 2009-01-07
That command doesn't even work as root:

```
~> sudo gnome-power-cmd.sh reboot
Rebooting
Error org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 0
Failed
```The longer dbus-send one does, though.

I used this command to watch for dbus messages:
```
dbus-monitor --session "type='signal',interface='org.freedesktop.PowerManagement'" | tee dbuslog3.txt

```and I did not see any messages:
```

signal sender=org.freedesktop.DBus -> dest=:1.76 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.76"
signal sender=(null sender) -> dest=(null destination) path=/org/freedesktop/DBus/Local; interface=org.freedesktop.DBus.Local; member=Disconnected

```It didn't send any power messages for Log out, Restart, or Shut down, whether I did it from FUSA or the System menu, so I'm not sure that this is really how it's done by the system.  With FUSA, if you Restart, it makes sure you don't have anything open first, same as if you Log out.  With System --> Shut Down --> Restart, it just restarts instantly.  The messages it displays ("Interrupting program may cause you to lose work.") are part of gnome-session, so I guess that's the next place to look.

---

### Post by apanloco on 2009-04-24
Did you solve this?

---

### Post by Endolith on 2009-04-27
I don't know any more than is in this thread

---

