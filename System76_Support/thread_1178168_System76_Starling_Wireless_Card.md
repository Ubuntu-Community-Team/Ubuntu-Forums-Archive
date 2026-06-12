---
title: "System76 Starling Wireless Card"
date: 2009-06-04
forum: System76 Support
---

### Post by ubermenschx on 2009-06-04
Can the card go into promiscuous mode for Pen testing? here is the card for those who aren't familiar:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: QUANTA Computer Inc Device 1777
        Flags: bus master, fast devsel, latency 0, IRQ 2301
        I/O ports at 1000 [size=256]
        Memory at 51010000 (64-bit, prefetchable) [size=4K]
        Memory at 51000000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at 51020000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
        Capabilities: [cc] Vital Product Data <?>
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: r8169
        Kernel modules: r8169

---

### Post by thomasaaron on 2009-06-04
Not something we test, but...

[http://ubuntuforums.org/showthread.php?t=837863](http://ubuntuforums.org/showthread.php?t=837863)

...seems to indicate it is possible. They don't explain how they did it, though.

---

### Post by ubermenschx on 2009-06-04
I went to that post and it still wasn't helpful. Here is something I will try from this sight and post if it works:

[http://www.a110wiki.de/wiki/Wireless](http://www.a110wiki.de/wiki/Wireless)

---

### Post by ubermenschx on 2009-06-04
this is what I tried:

gonzo@gonzo-laptop:~$ sudo iwconfig wlan0 mode monitor

this is what I got:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

If any one has any ideas, I would appreiciate it and  so will the next guy.

---

### Post by thomasaaron on 2009-06-05
Same error message here...

[http://forums.remote-exploit.org/newbie-area/10699-bt3-iwconfig-device-resource-busy.html](http://forums.remote-exploit.org/newbie-area/10699-bt3-iwconfig-device-resource-busy.html)

...and a couple of workaround ideas. Probably the...
```


iwconfig wlan0 down
iwconfig wlan0 mode monitor
iwconfig wlan0 up
```

...idea is the best.

---

### Post by ubermenschx on 2009-06-05
I think I got it...loaded airmon-ng and aircrack-ng then:

sudo airmon-ng start wlan0

Let me know if it works for you.

---

### Post by ubermenschx on 2009-06-07
While I did get monitor mode to work sometimes after boot up the wireless card will refuse to work. This wireless card is awfully finicky.

---

### Post by dizzpozable on 2010-04-20
Here's a script that works for placing a starling with an rt8187 into monitor mode.

```

#!/bin/bash

# monmode.sh - by dual
# sets up monitor mode on system76 starling

echo
echo "monmode.sh - sets up monitor mode on system76 starling"
echo

# stop troublesome processes
echo ">>> stopping conflicting processes..."
stop --quiet avahi-daemon && \
stop --quiet network-manager && \
killall wpa_supplicant
echo

# start monitor mode
echo ">>> entering monitor mode..."
airmon-ng start wlan0

echo ">>> note, you will have to reboot to regain network access"
echo

```

---

### Post by xboxit on 2011-10-31
hi where is the wlan card located in a system 76 laptop the 17" model?

---

### Post by isantop on 2011-11-03
What is the model number of your computer? It would be listed on the bottom of the computer. 

In the future, it's generally better to start a new thread to ask a question, rather than continuing on an old one. You can create a new thread with the button labeled "New Thread" in the main forum view.

---

