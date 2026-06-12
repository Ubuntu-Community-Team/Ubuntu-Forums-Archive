---
title: "Suspend / Resume for Serval"
date: 2011-09-25
forum: System76 Support
---

### Post by habys on 2011-09-25
Greetings! I realize you support Ubuntu, so I realize I've strayed a bit in terms of support.

First of all, thank you for this laptop, it's amazing. 
Here's some info to describe my situation, it also just might be helpful to someone:

**************************************
Hardware
[http://knowledge76.com/index.php/SerP7](http://knowledge76.com/index.php/SerP7)
**************************************
OS
64bit Debian stable "Squeeze"
lsb_release -r
Release:        6.0.2
**************************************
dmesg
[http://pastebin.com/raw.php?i=PCCXhx7Z](http://pastebin.com/raw.php?i=PCCXhx7Z)
**************************************
Non-free components:

firmware-iwlwifi - Binary firmware for Intel Wireless 3945, 4965 and 5000-series cards

nVidia - binary blob
sudo cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
GCC version:  gcc version 4.4.5 (Debian 4.4.5-8) 
**************************************
uname -a
Linux bs 2.6.32-5-amd64 #1 SMP Fri Sep 9 20:23:16 UTC 2011 x86_64 GNU/Linux
**************************************
hdparm -I /dev/sda
hdparm -I /dev/sdb
[http://pastebin.com/raw.php?i=zN1G2y2c](http://pastebin.com/raw.php?i=zN1G2y2c)
**************************************
cat /proc/cpuinfo
[http://pastebin.com/raw.php?i=q49nHjwA](http://pastebin.com/raw.php?i=q49nHjwA)
**************************************
cat /proc/meminfo
[http://pastebin.com/raw.php?i=jMf60J3h](http://pastebin.com/raw.php?i=jMf60J3h)
**************************************



Question: I know this is a stretch, but I've pulled apart system76-driver and would like to try and compile suspend/resume for Debian. Can any one offer some assistance?

Also, thanks Carl and Tom for the drivers! Is there any progress getting them accepted into the mainstream kernel?

---

### Post by isantop on 2011-09-26
Actually, the bit breaking your suspend and resume are the drivers for USB3. You'll want to make sure they get unloaded before suspending, and reloaded after resuming. I'm not sure how to do this in Debain, but in Ubuntu, it's done like this:

```
echo "SUSPEND_MODULES=\"xhci-hcd\"" | sudo tee -a /etc/pm/config.d/suspend_modules
```

---

### Post by habys on 2011-10-03
OK! Now I'm in business. [http://ubuntuforums.org/showthread.php?t=1444822]("Source") For posterity:

/etc/pm/sleep.d/20_custom-xhci_hcd
```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-xhci_hcd".
TMPLIST=/tmp/xhci-dev-list

case "${1}" in
  hibernate|suspend)
    echo -n '' > $TMPLIST
    for i in `ls /sys/bus/pci/drivers/xhci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
    # Unbind ehci_hcd for first device XXXX:XX:XX.X:
     echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
     echo "$i" >> $TMPLIST
  done
  ;;
    resume|thaw)
  for i in `cat $TMPLIST`; do
    # Bind ehci_hcd for first device XXXX:XX:XX.X:
    echo -n "$i" | tee /sys/bus/pci/drivers/xhci_hcd/bind
  done
  rm $TMPLIST
  ;;
esac

```
/etc/pm/config.d/usb3-suspend-workaround
```

#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

```

I set the executable bit for both. I don't have any USB3 devices to test, but it does hibernate now, at least sudo pm-suspend, does. I everything is perfect now, thanks!

---

