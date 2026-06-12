---
title: "using VGA w/projector and my silver GV"
date: 2007-02-17
forum: System76 Support
---

### Post by Nangineer on 2007-02-17
I have a silver Gazelle Value I bought last October. I want to be able to use its VGA port (or S-video) with a Dell 1200MP projector to show presentations (the projector when disconnected searches for input from VGA, S-video, composite video, etc.). Will this work out of the box, or is any additional configuration necessary? Graphics are GMA 950.

---

### Post by crichell on 2007-02-17
It should work out of the box.  One of the FN key switches between LCD, then LCD + VGA, then VGA.  Check if i810switch is installed if you have any trouble.

sudo apt-get install i810switch

---

### Post by Nangineer on 2007-03-02
I tried it today and it didn't work. The projector cycled through the messages "searching for VGA", "searching for S-video", composite video, etc. When it got to VGA, the light dimmed a little, and the "searching for VGA" message was gone, but it didn't mirror the screen on the laptop.

---

### Post by reacocard on 2007-03-02
I recall seeing a thread like this once, for another system76 laptop even. All that had to be done was adding
```
	Option		"MonitorLayout"		"CRT+TV,LFP"
	Option		"Clone"			"True"
```
to the "Device" section of the xorg.conf. I might be forgetting something, but this should at least put you on the right track.

EDIT: here's the thread: [http://ubuntuforums.org/showthread.php?t=244590](http://ubuntuforums.org/showthread.php?t=244590)

---

### Post by Nangineer on 2007-03-16
I tried it with "CRT,LFP" and got the same result. The projector output just dimmed a little as it cycled, but it kept cycling, trying to find another signal.

By the way, I'm running Edgy. (If I need Dapper or Feisty to do this, please let me know.)

It does work on a Macbook, if that helps.

---

### Post by Nangineer on 2007-03-28
It works after all. I had to change resolution from 1280x800 to 1024x768. I didn't need to edit xorg.conf or anything.

---

