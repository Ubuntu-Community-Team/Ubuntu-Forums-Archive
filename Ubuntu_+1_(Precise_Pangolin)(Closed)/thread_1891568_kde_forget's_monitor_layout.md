---
title: "kde forget's monitor layout"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jordanwb on 2011-12-05
I've already files a bug on launchpad about this but I'm wondering if anyone else has this problem. I use two monitors in a side by side layout. I go to "System Settings" -> "Display and Monitor display settings" then set up my monitors as I wish, click "Apply" then "Save as Default" On reboot the monitors are back to mirroring mode.

---

### Post by buzzmandt on 2011-12-06
I'll mark this as a me too, please link your bug report so i can me too it pls

---

### Post by Jordanwb on 2011-12-06
Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/898390](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/898390)

---

### Post by Jordanwb on 2011-12-26
I ended up writing a xorg.conf file:

```
Section "Monitor"
	Identifier	"DVI-0"
	Option		"Primary"	"True"
EndSection

Section	"Monitor"
	Identifier	"DVI-1"
	Option		"RightOf"	"DVI-0"
	Option		"Primary"	"False"
EndSection

Section	"Device"
	Identifier	"Card0"
	Driver		"radeon"
EndSection

Section	"Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"DVI-0"
	DefaultDepth	24
	Subsection "Display"
		Modes	"1920x1080"
		Virtual	3840	1080
	EndSubsection
EndSection

```

---

