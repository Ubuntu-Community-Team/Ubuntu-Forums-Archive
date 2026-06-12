---
title: "Laptop randomly shuts down when using battery"
date: 2020-02-18
forum: Ubuntu/Debian BASED
---

### Post by random turnip on 2020-02-18
I've been running Pop OS on an old Samsung laptop for about a week now and I love it, however I have one seemingly random problem which may or may not be related to Pop.

When on battery power the laptop will, seemingly at random shut off, and its not like its shutting down properly, its instant. I've noticed this only happens when its using battery power, and normally you can use it for about 10 minutes and it won't do it, but once it's done it, when you reboot it won't be long before you do it again. I don't think its done it a single time while plugged in (I think).

Now my first instinct was that this is hardware, a loose connection or something, but in that case why would being on battery power make a difference? And I don't believe it did it at all when it had Windows running. The only hardware change I've done is swapping a traditional HDD to an SSD.

Any suggestions? Like I say, this may have nothing to do with Pop, maybe something to do with overheating (not that I'd know where to begin with this)?

---

### Post by DuckHook on 2020-02-18
Given the symptoms you describe, the likeliest reason is a failing battery (I used to play around with a lot of old laptops: this was a recurring problem). The laptop may report a "full" battery, but this can sometimes only mean that it is charged up to maximum charge&#8212;what's not conveyed is that "maximum" has deteriorated to pathetic amperage.

I'm not at all familiar with PopOS, so have no idea how it implements power management/reporting. Can't help you with specifics; only point you in a certain direction to explore further.

---

### Post by random turnip on 2020-02-19
Thank you, it makes sense that it would be the battery.  I assumed the battery was alright, because without the random turning off, it was lasting for well over an hour on battery power, which is better than I expected for its age.

I'll look for some way if checking battery condition.  A new battery for these machines isn't expensive either.

---

### Post by random turnip on 2020-02-19
I ran the upower dump...
```
paul@pop-os:~$ upower -d
Device: /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:03:20 GMT (482 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

Device: /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:11:20 GMT (2 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              20.7792 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         10.2564 W
    voltage:             12.338 V
    time to full:        34.3 minutes
    percentage:          78%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582135880	78.000	charging
  History (rate):
    1582135880	10.256	charging

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:11:20 GMT (2 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               charging
    warning-level:       none
    energy:              20.7792 Wh
    energy-full:         26.64 Wh
    energy-rate:         10.2564 W
    time to full:        34.3 minutes
    percentage:          78%
    icon-name:          'battery-full-charging-symbolic'

Daemon:
  daemon-version:  0.99.11
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep 
```

This seems to mean there aren't any warnings coming from the battery, but I have no idea if the energy rates or voltage readouts are bad or alright.  Does the "Capacity 46%" basically mean that its now only capable of 46% of the charge?  Can anyone see anything here that would point to the battery being knackered?

The other part that catches my eye is "energy-full: 26.64 Wh" when the following line is "energy-full-design:  57.72 Wh".  Does this mean that the battery is now only kicking out about half the power that it was designed to?

I also ran the command to monitor in detail, then unplugged the charger and re-plugged it in to see what it did...
```
paul@pop-os:~$ upower --monitor-detail
Monitoring activity from the power daemon. Press Ctrl+C to cancel.
[18:19:39.244]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.247]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.249]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.253]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.258]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.260]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         8.0031 W
    voltage:             12.344 V
    time to empty:       2.7 hours
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:39.261]	device changed:     /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              no
    icon-name:          'ac-adapter-symbolic'

[18:19:39.261]	device changed:     /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:39 GMT (0 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              no
    icon-name:          'ac-adapter-symbolic'

[18:19:39.261]	daemon changed:
  daemon-version:  0.99.11
  on-battery:      yes
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep

[18:19:46.172]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.175]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.182]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.183]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.185]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.187]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.188]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging

[18:19:46.190]	device changed:     /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

[18:19:46.190]	device changed:     /org/freedesktop/UPower/devices/line_power_ADP1
  native-path:          ADP1
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:46 GMT (0 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

[18:19:46.190]	daemon changed:
  daemon-version:  0.99.11
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep

[18:19:47.034]	device changed:     /org/freedesktop/UPower/devices/battery_BAT1
  native-path:          BAT1
  vendor:               SAMSUNG Electronics
  model:                SR Real Battery
  serial:               123456789
  power supply:         yes
  updated:              Wed 19 Feb 2020 18:19:47 GMT (0 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              21.8448 Wh
    energy-empty:        0 Wh
    energy-full:         26.64 Wh
    energy-full-design:  57.72 Wh
    energy-rate:         9.324 W
    voltage:             11.795 V
    time to full:        30.9 minutes
    percentage:          82%
    capacity:            46.1538%
    technology:          lithium-ion
    icon-name:          'battery-full-charging-symbolic'
  History (charge):
    1582136360	82.000	charging
  History (rate):
    1582136386	9.324	discharging
    1582136379	8.003	discharging
    1582136360	8.070	charging 
```

---

### Post by DuckHook on 2020-02-19
> **random turnip said:**
> I ran the upower dump...

This seems to mean there aren't any warnings coming from the battery, but I have no idea if the energy rates or voltage readouts are bad or alright.  Does the "Capacity 46%" basically mean that its now only capable of 46% of the charge? 
Yes, that's what it means. Your battery doesn't seem to be the problem. It is still capable of holding almost half its design capacity, which would definitely be more than 10 minutes. Of course, with old components, built-in self-diagnostics are not entirely reliable, but even if the reporting was off by half, it's still not just 10 minutes of charge.

> The other part that catches my eye is "energy-full: 26.64 Wh" when the following line is "energy-full-design:  57.72 Wh".  Does this mean that the battery is now only kicking out about half the power that it was designed to?
Only 46% to be precise. This is only to be expected. Li-ION batteries slowly lose capacity over time until they give up the ghost. Yours appears to be functioning properly for its age. Diminished capacity does not mean compromised output and 12 V 10 W conforms to expectations. It should not be the source of your problems.

Next step would be to look at your initial suspicions: temperature. I don't know what PopOS has in its repos, but all Linux distros that I'm aware of have *lm-sensors*. Install that, keep tabs on your various temps and see if there are any correlations. You might also consider installing *hddtemp*. Don't underestimate the value of listening to your fan and cleaning out your heat sinks with canned air either. Both are elementary processes but often overlooked.

Look at your logs for clues. *dmesg* is useless after a crash, but *syslog* might have recorded something.

---

### Post by random turnip on 2020-02-21
I installed a Gnome extension which shows core temps, HDD temp and voltage inputs.  So far everything looks pretty normal, cores seem to hover around 50 deg C, got up to 60 when watching a video and listening to Spotify, any small rise and the fans get louder and they cool again, so that seems to be as it should.  The SSD seems to stay around 32-36 deg C, no idea if that's about right but doesn't sound particularly hot.  The voltage goes from 12v when plugged in to 11.8v when on battery, so minimal change.  I checked this with lm-sensors and they were basically all the same.

I'm struggling how to find out how to check the syslog files in Pop OS at the moment, but I guess that's my next port of call and check after a crash.

I'm thinking of opening it up and giving the fans a clean anyway cause it can't hurt, but other than that I'm pretty confused how I can have a hardware problem only when on battery power.

Typically with these sorts of problems, now I'm trying to make the crash happen again to see if its related to CPU usage, it isn't happening even though I'm trying to replicate what I was doing the last couple of times it happened (watching Twitch and in Writer).

---

### Post by DuckHook on 2020-02-22
On old boxes, I've experienced this problem due to everything from failing PSUs to faulty RAM modules to cracked MOBOs to bad GPUs. And that's only the the HW side. They are nasty problems to chase down and the only way to do it is to replace each component to isolate the fault. The possibility of SW corruption only adds to the complexity of possible causes. 

It's not really possible to narrow it down without more clues, so keep up the data-gathering.

---

### Post by random turnip on 2020-02-26
Well I'm now really confused and starting to think it might be the battery afterall, and maybe I need to accept the cost and get a new one just to try it to put my mind at rest.  I'm thinking this because I used it on battery power for about an hour without issue while word processing, having a Twitch stream running in the background as well as listening to music all at the same time, then all of a sudden it cut out, after being used for an hour without problem, battery reading about 20%.  I tried to re-boot and it cut out on the login screen, sooner than it normally does.  Plugged in, worked fine.

Next day, I used it on battery mode for about 30 mins, then put it to sleep.  Picked it up today, still sleep mode but still on and sitting at something like 70%.  Used for maybe 10 mins then it cut out again.  Booted back on, cut out while typing my password again.  This time, when I plugged it in and rebooted it was saying 1% battery, and after maybe 30 seconds of charging it jumped to 100%, which obviously can't be right, but this is the first sign I've seen of the battery failing.

I was starting to think it was an overheating problem, as I noticed that the fans are sometimes louder when i reboot than when in the OS, which made me think the OS isn't telling the fans to go fast enough.  But when it cut out today the cores weren't particularly hot, so I doubt it is.

---

### Post by DuckHook on 2020-02-26
There are no guarantees that the problem is the battery. All I can say is that it's the likeliest possibility among a long list of other possibilities. If the laptop is an old one, you can try looking in electronic shops or with on-line vendors for cheaper replacements. Before parting with your hard-earned cash, you can also take the battery into an electronics shop and have them test it on a power analyzer. Don't settle for a plan old amp-meter or watt-meter since you are already getting questionable readings from those circuits on your laptop.

---

### Post by random turnip on 2020-03-03
Well, I decided to just take the plunge and get a cheap-ish battery, and that seems to have fixed it.  Obviously the problems were at random, so hard to say for sure, but I've probably used the laptop for a range of tasks on battery power for about 3 hours at this point and no cutting out, and the battery percentage drain seems more consistent.

So I guess if you find yourself with this problem, it's worth trying a different battery first.

---

