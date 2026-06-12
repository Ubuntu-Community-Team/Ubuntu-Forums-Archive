---
title: "modem huawei e398 doesn t works"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ff1-ff1 on 2012-04-01
I was forced by my family to check if LTE modem huawei e398 works in ubuntu 12.04 beta 2.  Unfortunatly it doesnt.
There is no any reaction after putting it into usb. But after lsusb i get right information (i mean about gsm modem huawei etc.-not usb memory). But dmesg |grep GSM and ls /dev/ttyUSB* give me nothing(first-without any answer,second-no such file or directory).
May I count that in final version of the system this modem will work? Or should i install windows xp?

---

### Post by philinux on 2012-04-01
> **ff1-ff1 said:**
> I was forced by my family to check if LTE modem huawei e398 works in ubuntu 12.04 beta 2.  Unfortunatly it doesnt.
There is no any reaction after putting it into usb. But after lsusb i get right information (i mean about gsm modem huawei etc.-not usb memory). But dmesg |grep GSM and ls /dev/ttyUSB* give me nothing(first-without any answer,second-no such file or directory).
May I count that in final version of the system this modem will work? Or should i install windows xp?

See this and post #9

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/889878](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/889878)

---

### Post by ff1-ff1 on 2012-04-01
i saw this posts earlier.They are usless for people like me (with my level of abilities in linux). I want to use network manager. Moreover people which will use this device  have problem with proper shutting down system so i wont complicate their life.
My question is open- will ubuntu 12.04 (final) properly work with this device or not? I have to install new system so if answer is No i will chose windows xp.

---

### Post by surja on 2012-04-16
Apparently Ubuntu 12.04 Beta seems not to detect or configure quite a few USB 3G modems. I think the drivers are simply missing. Bugs have been filed regrading this problem but i suppose this is not a major problem concerning the devs. Unfortunately for many people i know, a USB 3G modem is the only way of connecting to the net.

---

