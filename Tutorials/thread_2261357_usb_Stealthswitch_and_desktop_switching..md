---
title: "usb Stealthswitch and desktop switching."
date: 2015-01-18
forum: Tutorials
---

### Post by lee295012-gmail on 2015-01-18
Found out how to do this years ago but never wrote it up, may be a better way but it works for me.
Different versions and makes of switch will likely have a different output and id.

programs to be used:
inputlirc - Zeroconf LIRC daemon using input event devices (**watches for presses from the stealthswitch**)
lirc - infra-red remote control support (**needed for irexec program**)
wmctrl - control an EWMH/NetWM compatible X Window Manager (**for switching between virtual desktops**)

```
sudo apt-get install inputlirc lirc wmctrl
```

neeed to find the right id for the device.
```
lee@kubuntu:~$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 Jan 18 12:38 usb-04d9_USB_Laser_Game_Mouse-event-if02 -> ../event6
lrwxrwxrwx 1 root root 9 Jan 18 12:38 usb-04d9_USB_Laser_Game_Mouse-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 Jan 18 12:38 usb-04d9_USB_Laser_Game_Mouse-if01-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 Jan 18 12:38 usb-04d9_USB_Laser_Game_Mouse-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 Jan 18 12:38 usb-StealthSwitch_by_H-Mod_Inc_StealthSwitch_by_H-Mod_Inc-event-kbd -> ../event3
lee@kubuntu:~$ 

```

Edit /etc/default/inputlirc and add the device.
```
lee@kubuntu:~$ cat /etc/default/inputlirc 
# Options to be passed to inputlirc.
EVENTS="/dev/input/by-id/usb-StealthSwitch_by_H-Mod_Inc_StealthSwitch_by_H-Mod_Inc-event-kbd"
OPTIONS="-g -m 0 -c"

```

restart the service.
```
sudo service inputlirc restart
```

if you run irw (part of lirc) from a terminal you should see output like this when you press the pedal.
```
lee@kubuntu:~$ irw
6 0 CTRL_SHIFT_ALT_KEY_5 /dev/input/by-id/usb-StealthSwitch_by_H-Mod_Inc_StealthSwitch_by_H-Mod_Inc-event-kbd

```

Contents of my .lircrc file
```
lee@kubuntu:~$ cat .lircrc 
begin
remote = /dev/input/by-id/usb-StealthSwitch_by_H-Mod_Inc_StealthSwitch_by_H-Mod_Inc-event-kbd
prog = irexec
button = CTRL_SHIFT_ALT_KEY_5
config = /home/lee/Documents/workspace_cycle.sh
end

```

Create the file irexec will run when the pedal is pressed, i only need 2  desktops, you'll need to figure out a script if you need more.
don't forgot to chmod +x the file to make it executable.
```
lee@kubuntu:~$ cat Documents/workspace_cycle.sh 
#!/bin/sh
num=$(wmctrl -d |grep  "*" | cut -b1-1)
echo $num

if [ $num = 0 ]; then
 wmctrl -s 1
fi

if [ $num = 1 ]; then
 wmctrl -s 0
fi

```

irexec needs to run all the time, you will have to autostart for which ever window manager you use.

---

