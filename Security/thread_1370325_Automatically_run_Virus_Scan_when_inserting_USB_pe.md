---
title: "Automatically run Virus Scan when inserting USB pen drive"
date: 2010-01-02
forum: Security
---

### Post by krackersk on 2010-01-02
Hi All,

I use my ubuntu laptop at work and connect a lot of usb pen drives to my computer. Everyone else I work with use windows and I want to make sure that the usb pen drives don't contain any windows viruses so I don't spread them. 

The best way for this to be done would be to have the USB pen drives automatically scanned with they are inserted in my ubuntu machine. Any ideas on how to do this?

---

### Post by BkkBonanza on 2010-01-02
You can do this with a udev rule. I have done similar but for changing mount mode to read only. Should be the same idea but with a different run script.

Here is my rules, you put them in a file in /etc/udev.d/rules/

KERNEL=="sd[b-z][0-9]", ACTION=="add", RUN+="/usr/local/bin/remounter /dev/%k"
KERNEL=="mmc*", ACTION=="add", RUN+="/usr/local/bin/remounter /dev/%k"

For me this runs a script I made called remounter. What these rules say is "when a new kernel device named sdb0 - sdz9 or starting with mmc is added to the system then run this program... with the device name. For more info google "udev rules", there is some how-to pages around.

---

### Post by MikeFishcake on 2010-10-29
Just resurrecting this one to say thanks - looks like exactly what we need.

---

### Post by superbike on 2012-03-20
me too!
ah beautiful forums!

---

