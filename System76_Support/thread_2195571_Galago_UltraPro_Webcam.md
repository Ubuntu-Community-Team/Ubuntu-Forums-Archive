---
title: "Galago UltraPro Webcam"
date: 2013-12-25
forum: System76 Support
---

### Post by ash5 on 2013-12-25
Can someone who has the Galago UltraPro please give me the output of lsusb. I just bought a machine from Pro-star but its the same Clevo w740su. This is the output of mine:

> # lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


There's no webcam being detected. Trying to run lsusb with verbose flag core dumps. I'm pretty sure there is a H/W issue as this has happened with 13.04 and 13.10. Would like to collect some more evidence before I RMA this thing.

---

### Post by cool110 on 2013-12-25
You need to press Fn+F10 to enable the webcam before it can be detected.

---

### Post by ash5 on 2013-12-26
Well don't I feel like an idiot. Thanks for your help. Not sure how to mark as [solved]

---

