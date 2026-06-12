---
title: "star3 gnome-power-manager"
date: 2010-09-16
forum: System76 Support
---

### Post by tanderson on 2010-09-16
Problem:
gnome-power-manager reaches "laptop battery is charged" and never changes status regardless of many power cord removals or suspend sequences. This is quit annoying as power saving features do not get activated and severely shortens battery life. I can get the battery level from the terminal with acpi -V, so not a huge.

I believe the problem is with upower that the gnome-power-manager is based on. I don't have steps to reproduce, but happens often enough that I believe others will experience the same problem with normal use. I hunted quit a bit to see if I could at least set up a script to restart the upower daemon, I didn't find any help with that. I looked through log files but didn't see any reference to "power".

some terminal dumps:

upower -d
Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0
  vendor:               Clevo CO.
  model:                M1100
  power supply:         yes
  updated:              Tue Sep 14 11:39:59 2010 (75034 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    energy:              22.4553 Wh
    energy-empty:        0 Wh
    energy-full:         22.4553 Wh
    energy-full-design:  24.42 Wh
    energy-rate:         0.0111 W
    voltage:             14.8 V
    percentage:          100%
    capacity:            91.9545%
    technology:          lithium-ion

Daemon:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no		//wrong! should be yes!
  on-low-battery:  no 
  lid-is-closed:   no
  lid-is-present:   yes


acpi -V		//run at same time as above. battery0 discharging.
Battery 0: Discharging, 25%, rate information unavailable
Battery 0: design capacity 2200 mAh, last full capacity 2023 mAh = 91%
Thermal 0: ok, 62.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 103.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10


upower -v
TI:08:59:28	FI:egg-debug.c	FN:egg_debug_post_parse_hook,415
 - Verbose debugging 1 (on console 1)
UPower client version 0.9.1
UPower daemon version 0.9.1


upower daemon log. Not much here for clues.
Monitoring activity from the power daemon. Press Ctrl+C to cancel.
[09:59:25.655]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   yes
  lid-is-present:   yes

[17:57:05.179]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[17:57:05.576]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[19:00:24.749]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   yes
  lid-is-present:   yes

[19:18:35.581]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[20:36:11.719]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      yes
  on-low-battery:  no
  lid-is-closed:   yes
  lid-is-present:   yes

[22:05:03.964]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[22:05:05.058]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[22:20:55.847]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   yes
  lid-is-present:   yes

[08:12:43.609]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

[08:51:05.190]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   yes
  lid-is-present:   yes

[08:52:18.917]	daemon changed:
  daemon-version:  0.9.1
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:   yes

---

### Post by isantop on 2010-09-17
Seems to me that the actual daemon is functioning, at least a little, since there are a few times the "on-battery" field gets changed from no to yes and back. Perhaps it has to do with the way upower reads from the daemon. I'll do some testing on our Starling to see what I can dig up.

---

### Post by tanderson on 2010-09-18
It acts like the daemon functions normally until the battery gets fully charged. Then it hangs there and the only thing that fixes it, is a reboot. Let me know if you need anymore info. I will keep working on this. Thanks.

---

### Post by tanderson on 2010-09-18
this bug might be relevant.
[467825]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/467825")

to restart the daemon from site:
```
sudo killall upowerd
sudo /usr/lib/upower/upowerd
```

---

### Post by tanderson on 2010-09-20
unfortunately the above restart of upower daemon doesn't solve everything. It updates the battery state on the gnome-power-manager, but power saving features like the dimming of the screen are not functioning after restart.

---

