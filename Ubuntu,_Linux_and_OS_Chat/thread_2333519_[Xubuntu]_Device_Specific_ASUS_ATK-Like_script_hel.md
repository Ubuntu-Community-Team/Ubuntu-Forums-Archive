---
title: "[Xubuntu] Device Specific ASUS ATK-Like script help"
date: 2016-08-10
forum: Ubuntu, Linux and OS Chat
---

### Post by techyzen101 on 2016-08-10
I've been trying to create custom scripts for hot-keys and properties for my net-book, ASUS X102BA, so I can have a painless transfer of my device specific customizations to newer Ubuntu (Xubuntu) versions.
  I'm planning to make it support other models I may get my hands on in the future, but I'm not sure how to pull off a proper configuration file and how it is used for each, and if there are better suited commands and optimizations for the scripts.

x102ba-touchpad:
```

#!/bin/bash
# Required to make notify-send work for udev event
export DISPLAY=:0
user=(`who | head -n1 | sed 's/ .*//'`)
export XAUTHORITY="/home/$user/.Xauthority"
DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"

# Icon
icon=input-touchpad-symbolic

# Script to toggle the touchpad
devicename="ETPS/2 Elantech Touchpad"
device=$( xinput list --short "$devicename" | grep -Po '(?<=id=)[0-9]+' )
state=`xinput list-props "$device" | grep "Device Enabled" | grep -ic ":.*1"`

if [ $1 ]; then
    if [ $EUID -eq 0 ] && [ -f $DIR/dnotify ] && [ $1 -ne $state ]; then
        xinput set-prop $device 'Device Enabled' $1
        if [ $1 -eq 0 ]; then
            su $user $DIR/dnotify 'Touchpad' 'Disabled: Mouse Connected' 5000 $icon
        elif [ $1 -eq 1 ]; then
            su $user $DIR/dnotify 'Touchpad' 'Enabled: Mouse Disconnected' 5000 $icon
        fi
    fi
else
    if [ $state -eq 1 ]; then
        xinput set-prop $device 'Device Enabled' 0
        notify-send -i $icon -t 5000 "Touchpad" "Disabled"
    else
        xinput set-prop $device 'Device Enabled' 1
        notify-send -i $icon -t 5000 "Touchpad" "Enabled"
    fi
fi
```

x102ba-touchscreen:
```

#!/bin/bash
# Script to toggle the touchscreen
devicename="USBest Technology SiS HID Touch Controller"
device=$( xinput list --short "$devicename" | grep -Po '(?<=id=)[0-9]+' )

# Icon
icon=video-display-symbolic

state=`xinput list-props "$device" | grep "Device Enabled" | grep -ic ":.*1"`

if [ $state -eq 1 ];then
    xinput set-prop $device 'Device Enabled' 0
    notify-send -i $icon -t 5000 "Touchscreen" "Disabled"
else
    xinput set-prop $device 'Device Enabled' 1
    notify-send -i $icon -t 5000 "Touchscreen" "Enabled"
fi
```

x102ba-wireless:
```

#!/bin/bash
# Script to toggle wifi (nmcli method)
STATUS=`nmcli r wifi`

# Icon
icon=network-wireless-symbolic

if [ "$STATUS" == "disabled" ]; then
    nmcli r wifi on
    notify-send -i $icon -t 5000 "Wireless Receiver" "Enabled"
else
    nmcli r wifi off
    notify-send -i $icon -t 5000 "Wireless Receiver" "Disabled"
fi
```

99-touchpad-control.rules
```

SUBSYSTEM=="input", ACTION=="add",    KERNEL=="mouse[0-9]", ATTRS{bInterfaceProtocol}=="02", ATTRS{bInterfaceClass}=="03", ATTRS{bInterfaceSubClass}=="01", ENV{ID_CLASS}="mouse", RUN+="/usr/local/bin/x102ba-touchpad 0"
SUBSYSTEM=="input", ACTION=="remove", KERNEL=="mouse[0-9]", ENV{ID_INPUT_MOUSE}=="?*", ENV{ID_CLASS}="mouse", RUN+="/usr/local/bin/x102ba-touchpad 1"
```

---

