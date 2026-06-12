---
title: "dbus commands"
date: 2011-06-04
forum: The Cafe
---

### Post by jazzerit on 2011-06-04
Ok guys: Let's see what you can do with dbus! Here's two to get you started:
Turn off the computer from the command line without root:
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

toggle banshee play/pause:
```
 dbus-send --session --type="method_call" --dest='org.bansheeproject.Banshee' '/org/bansheeproject/Banshee/PlayerEngine' 'org.bansheeproject.Banshee.PlayerEngine.TogglePlaying'
```

Now, let's see what else we got. Don't forget the command!

---

### Post by cariboo on 2011-06-05
When posting commands, you should use the [noparse]```

```[/noparse] tags.

---

