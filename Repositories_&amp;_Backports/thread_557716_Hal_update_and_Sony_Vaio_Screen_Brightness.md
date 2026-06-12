---
title: "Hal update and Sony Vaio Screen Brightness"
date: 2007-09-23
forum: Repositories &amp; Backports
---

### Post by howlsmoving on 2007-09-23
The version of the HAL packages in the backports repository breaks the brightness controls for my Sony VAIO VGN-CR131E.  This means the brightness applet in gnome as well as the spicctrl program stopped working.  I even tried re-running the command that made it work before for older packages (see below for it), but to no avail..

Here is the command I used to get brightness working with the old packages, but didn't work with the new package.  "sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done" (without the quotes)

Can someone tell me why this doesn't work?

---

### Post by llib1234 on 2007-09-27
Solution to Fix LCD brightness control

Edit the two files:

/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux

and

/usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux

Change the first line of each file from

[B]#!/bin/sh

to

#!/bin/bash[/B]

(You need Root privileges)

---

### Post by howlsmoving on 2007-09-29
Thanks for responding.

The script I had basically did that.  I checked the scripts and they were correct.  I have to resort to echoing numbers into /proc/acpi/sony/brightness.

The good or bad news is, I upgraded from a working fiesty install, to gutsy beta and I'm having the same problem in gutsy that I had with the backported hal installation, so I will have to post a bug report and hope that it will get fixed.

---

