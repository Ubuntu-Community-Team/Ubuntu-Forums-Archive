---
title: "Mouse battery level warning, disable or calibrate"
date: 2013-08-19
forum: Ubuntu Development Version
---

### Post by Smask on 2013-08-19
Either something got updated a couple of days ago or it got updated quite a while ago but the battery level of my mouse passed the threshold level this weekend. It's a Logitech M570 wireless trackball connected via unified receiver.The mouse got a battery warning LED so I don't need Ubuntu to remind me every second minute that the level is less than 1%. There's obviously juice left because the LED is off (as early warning the LED lights when rousing the mouse from sleep and then the LED is off. The LED blinks then the battery is actually giving up the ghost.)

Support for Logitech Unifying receiver were added in Saucy, either in kernel or some driver, because I didn't get these warnings in Raring.

So I need direction where I can configure the threshold value, or turn those warnings off.

---

### Post by kurt18947 on 2013-08-19
I am subscribing to this thread.  I have a Logitech keyboard with the unifying receiver.  I'm getting this warning in gnome-shell even though a digital meter shows 1.5 volts in both AA batteries.

---

### Post by mc4man on 2013-08-19
The wireless mouse battery level deal showed up a while ago & sometimes works correctly, many times not.
(currently it's not working here

The 'defining' point is whether I get the new?  indicator icon which is vertical. That one correctly idenifies the mouse & current battery level (or close enough

When I get the old horizontal icon then it initially may or may not recognize the mouse but after a bit it does. 
The icon then turns red & says 1% which is clearly wrong.
In the last couple of days I almost always get the old icon & eventual incorrect status

edit - screens of 'good' icon & resultant correct panel (rarely see anymore, screens from 08/12

---

### Post by cariboo on 2013-08-19
I have the same problem with my M570 trackball, I get a message saying the battery is a 1%, but when right clicking the horizontal battery icon and choosing M570, it shows the battery at 85%. When the indicator first starts up, it does say that the battery level is at 85%.

---

### Post by Ian_Worrall on 2013-08-19
I'm using [Solaar](http://pwr.github.io/Solaar/index.html) for this, and it seems to work fine.

---

### Post by Smask on 2013-08-25
Sorry, I've been busy for a couple days.

I'm running on flashback and I don't have the battery indicator so here's my "upower -d" output:

 ```
fredrik@AMDx2:~$ upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0004
  native-path:          /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6.4/1-6.4:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004
  vendor:               Logitech, Inc.
  model:                M570
  power supply:         no
  updated:              Sun Aug 25 08:42:17 2013 (215 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          90%

 Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no
 
```
That was when the notfication was quiet for a moment.
Here's output while popping the message:

 ```
fredrik@AMDx2:~$ upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0004
  native-path:          /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6.4/1-6.4:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004
  vendor:               Logitech, Inc.
  model:                M570
  power supply:         no
  updated:              Sun Aug 25 08:59:17 2013 (9 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          1%
  History (charge):
    1377413957    1.000    discharging

 Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no


```

---

### Post by kurt18947 on 2013-08-26
> **cariboo907 said:**
> I have the same problem with my M570 trackball, I get a message saying the battery is a 1%, but when right clicking the horizontal battery icon and choosing M570, it shows the battery at 85%. When the indicator first starts up, it does say that the battery level is at 85%.

I'm using 13.10 & gnome-shell.  My erroneous indicator is no longer showing up,  I guess an update fixed it.

Edit:  Well, it was fixed for a short time.:frown:

---

### Post by Smask on 2013-09-06
> **kurt18947 said:**
> I'm using 13.10 & gnome-shell.  My erroneous indicator is no longer showing up,  I guess an update fixed it.

Edit:  Well, it was fixed for a short time.:frown:

Seems like they fixed it by removing the code...
```
fredrik@AMDx2:~$ upower -d
Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no

```

---

### Post by cariboo on 2013-09-06
I still occasionally get the error pop up even though upower looks like it is detected properly:

```
upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0006
  native-path:          /sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/0003:046D:C52B.0006
  vendor:               Logitech, Inc.
  model:                M570
  power supply:         no
  updated:              Fri Sep  6 19:53:19 2013 (53 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          80%
  History (charge):
    1378522339	80.000	discharging

Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no
```

It does seem to be detecting the wrong type of battery though, as I've just got a normal AA battery in it.

---

### Post by Smask on 2013-09-07
> **cariboo907 said:**
> I still occasionally get the error pop up even though upower looks like it is detected properly:

Weird. I'm still on the factory battery (This is my second m570. The first one died when I tried to replace the scroll wheel button.) and the led lights up when I raise it from sleep now. 

> It does seem to be detecting the wrong type of battery though, as I've just got a normal AA battery in it.

Yeah, I saw that when the detection routine still "worked".

Update:

Got me some Upower 0.9.21-3ubuntu1 after I wrote this and I noticed the Logitech fixes in the changelog. The upower dump is as you posted. I'll pop over to LP and notice them about the "rechargable" mouse.

---

### Post by cariboo on 2013-09-07
I just did an update, and got the latest version of upower, now when I run:

```
upower -d
```

I get a change in the output, it now shows the the serial number of the device:

```
upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0006
  native-path:          /sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/0003:046D:C52B.0006
  vendor:               Logitech, Inc.
  model:                M570
  serial:               6351C11D
  power supply:         no
  updated:              Sat 07 Sep 2013 08:17:30 AM PDT (57 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          85%

Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no
```

---

### Post by xc3RnbFO8P on 2013-09-07
Here is mine, Logitech K400 with mousepad (no need to display as 2):

```
rig@rig-Aspire-R3600:~$ upower -d
Device: /org/freedesktop/UPower/devices/mouse_0003o046DoC52Bx0004
  native-path:          /sys/devices/pci0000:00/0000:00:04.0/usb2/2-5/2-5:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004
  vendor:               Logitech, Inc.
  model:                Wireless Touch
  serial:               77057893
  power supply:         no
  updated:              lør 07 sep 2013 21:53:53 CEST (44 seconds ago)
  has history:          yes
  has statistics:       no
  mouse
    present:             no
    rechargeable:        yes
    state:               unknown
    percentage:          0%

Device: /org/freedesktop/UPower/devices/keyboard_0003o046DoC52Bx0005
  native-path:          /sys/devices/pci0000:00/0000:00:04.0/usb2/2-5/2-5:1.2/0003:046D:C52B.0003/0003:046D:C52B.0005
  vendor:               Logitech, Inc.
  model:                K400
  serial:               DE47FF36
  power supply:         no
  updated:              lør 07 sep 2013 21:53:53 CEST (44 seconds ago)
  has history:          yes
  has statistics:       no
  keyboard
    present:             yes
    rechargeable:        yes
    state:               discharging
    percentage:          70%

Daemon:
  daemon-version:  0.9.21
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       no
rig@rig-Aspire-R3600:~$
```

---

