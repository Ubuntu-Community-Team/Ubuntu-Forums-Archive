---
title: "Ubuntu server 12.10 - SANE"
date: 2013-01-17
forum: Server Platforms
---

### Post by pikoli on 2013-01-17
Hello guys,

I have a problem regarding SANE. We have Canon MP500 multifunctional machine and I was able to configure printer corectly using CUPS, but scanner is not working.

I have installed sane-backends 1.0.23, and many other sane packages (one of them was enormous btw, - 120Mb) but sane-find-scanner doesn't find a thing. 
Still, I can see my scanner using lsusb:
```
Bus 001 Device 005: ID 04a9:170c Canon, Inc. PIXMA MP500 Scanner
```

I am new to linux and I have no idea what do do...

---

### Post by pikoli on 2013-01-17
bump, nobody had similar problem?

---

### Post by pdc on 2013-01-17
I suspect this has to do with "permissions":

this ubuntu help 

[https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

suggests you edit the file by coping and pasting into a terminal

> [COLOR="Red"]sudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

that opens the text editor gedit and then paste into it

> [COLOR="SeaGreen"]# Canon MP500
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="170c", ENV{libsane_matched}="yes"[/COLOR]

......>>I have edited this from the Ubuntu example that uses a lido scan;

SAVE CLOSE REBOOT

.......the good thing you can take from this is linux is fussy about who accesses what......sometimes it bites us all though..

.....let us know if this advice above is helpful......

---

### Post by pikoli on 2013-01-17
I appreciate your help, but this line was actually already in the file.

got anything else? :D

---

### Post by pdc on 2013-01-17
what does 

> scanimage -L give you ..and if no joy, 

> sudo scanimage -L

.........so you are running this canon MP500 via a usb cable from a standalone computer without a USB hub interfacing........ 

my suspicion is that this is all to do with permissions;

---

### Post by pikoli on 2013-01-18
both commands return the same resault:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

yep, MP500 is directly conected to ubuntu serverv via USB cable.

---

### Post by spectrepaul on 2013-02-12
I had exactly the same issue which was driving me nuts,

sudo scanimage -L

gave me the scanner

scanimage -L

couldn't find it


this is a permissions problem, I followed all the advice and changed all the settings like you with no luck and the lines for the scanner were already in the file.

Then all I did was this

sudo chmod a+w /dev/bus/usb/001/002

this sorted everything and both commands now work.
Give it a try and good luck :)

---

