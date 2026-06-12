---
title: "Darter wifi on suspend problem - SOLVED!"
date: 2007-05-26
forum: System76 Support
---

### Post by jgordon510 on 2007-05-26
I had a problem on my darter that when I came back from suspend the wifi wouldn't come back on. Most of the time I could get it back by flipping the switch on and off, but sometimes that wouldn't even work and I'd have to restart the network manager. I hunted around in the api scripts and found this script:

/etc/acpi/resume.d/60-asus-wireless-led.sh

the script reads:
```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
    setLEDAsusWireless 1
else
    setLEDAsusWireless 0
fi
```


On a whim, I tried switching the 1 and 0 values. Bingo! It works perfectly. Here's how the script reads now:
```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
if isAnyWirelessPoweredOn ; then
    setLEDAsusWireless 0
else
    setLEDAsusWireless 1
fi
```

---

### Post by MarkID on 2007-06-01
Can you post a step-by-step procedure for finding and editing the file?  TIA

---

### Post by thomasaaron on 2007-06-01
From a terminal, type:
> sudo gedit /etc/acpi/resume.d/60-asus-wireless-led.sh

In the resulting text editor, change the '0' to a '1' and change the '1' to a '0'.
Click 'save' on the text editor.

Reboot your computer.

---

