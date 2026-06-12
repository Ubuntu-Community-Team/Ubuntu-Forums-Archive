---
title: "Firewire 1394 DV Capture - How I got mine to work"
date: 2009-11-11
forum: Ubuntu Studio
---

### Post by AZMel on 2009-11-11
I've been trying the past few days to get DV capture through Kino to work with Firewire and I finally have a process that works.

By doing these steps everytime I start up or disconnect and reconnect my DV Cam it all works great.

sudo modprobe -r raw1394 dv1394 ohci1394
sudo modprobe raw1394
sudo modprobe dv1394
sudo modprobe ohci1394
sudo chmod 777 /dev/raw1394

Would be nice if I didn't have to go through it all but at least I have a solution.

Mel

---

### Post by AutoStatic on 2009-11-11
To automate it all:
**sudo gedit /lib/udev/rules.d/50-udev-default.rules**
And add the following line to the 'Firewire' section:
```
KERNEL=="raw1394",			GROUP="video"
```

Make sure you're member of the video group and then add the raw1394 module to /etc/modules:
**sudo gedit /etc/modules**
And add the line:
```
raw1394
```

This works for Jaunty, for Karmic I think the tool Ubuntu Studio Controls automates this for you. I'm not sure, I always set these things manually.

---

### Post by kayosiii on 2009-11-12
rather than writing the udev stuff to /lib/udev/rules.d/50-udev-default.rules it is better to create a new file in the same folder called say 50-raw-firewire.rules and add the line described by Autostatic to that. This way it won't get overwritten by Ubuntu system updates.

---

### Post by AutoStatic on 2009-11-12
You're right kayosiii, that will save you from hours of trying to figure out why your Firewire device doesn't work anymore all of a sudden :)

---

