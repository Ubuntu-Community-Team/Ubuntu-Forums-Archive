---
title: "DELL Vostro 3560 usb issue"
date: 2016-03-14
forum: Ubuntu/Debian BASED
---

### Post by wahwha on 2016-03-14
Hi, i have a dell Vostro 3560, running elementary OS 0.3.2 Freya (64-bit). The Laptop has 4 usb ports, all of them said to be as USB3., but if i check, the hardware is shown as 3 ports with USB2. and only one with USB3. all of the ports are blue in colour and none of them have the symbol for USB 3. 


> lsusb
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:648b Microdia Integrated Webcam
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 22b8:2e82 Motorola PCS 
Bus 003 Device 002: ID 275d:0ba6  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by sandyd on 2016-03-14
Moved to Other OS support as this is not a Ubuntu distribution.

---

### Post by wahwha on 2016-03-14
thanks

---

### Post by ajgreeny on 2016-03-14
This one listed is USB-3 I think.
{code]Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/code]
The other 3 are all USB-2 as far as I can make out, as you seem to have realised.
I think you just have to forget about the colour coding and go with the terminal output.

However, if you bought the laptop having been told by the seller that all were USB-3, I suspect you might have grounds for a complaint.

---

### Post by wahwha on 2016-03-14
ya..seems so apparently; its advertised as having all ports as USB3. Any idea as to tell which one is USB3 then?. as there no outer mark on it... copying large files is the only solution to check for speeds?

EDIT..Checked for speeds while copying file(5gb) onto a 1tb hard disk from all ports.. they all are similar..

---

