---
title: "Ubuntu Studio 14.04 WiFi is not stable."
date: 2014-09-18
forum: Ubuntu Studio
---

### Post by Hanjaya on 2014-09-18
Hi,

I have a dual core Dell laptop which ran Ubuntu Desktop 32bit 14.04LTS before. When I installed that, it was connected automatically with my WiFi, I put my WiFi password and boom...the connection was very stable. Then for some reason my laptop crashed and now I freshly installed Ubuntu Studio 32bit 14.04 into the laptop, after the installation the WiFi connection is very unstable. It always connects for about 5-10 minutes after rebooting the computer and it drops. I use IOGEAR GWU625 WiFi adapter. I am not sure what has happened....please help.

Thanks.

hc.

---

### Post by jejeman on 2014-09-18
If you really don't need "studio", go back to "desktop".

---

### Post by Hanjaya on 2014-09-18
Yes I need Studio indeed.

hc.

---

### Post by Hanjaya on 2014-09-19
Here is my iwconfig message.

wlan0   unassociated   Nickname:"rtl_wifi"
            Mode:Managed   Access Point: Not-Associated   Sensitivity:0/0
            Retry: off   RTS thr: off   Fragment thr: off
            Encryption key: off
            Power Management: off
            Link Quality:0   Signal level:0   Noise level:0
            Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0
            Tx excessive retries:0   Invalid misc:0    Missed beacon:0

Lo         no wireless extensions.



Please help. Thx.

hc.

---

### Post by Hanjaya on 2014-09-19
Here is the lsusb message.

Bus 001 Device 002: ID 0bda:812 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter


Here is the lshw message.

*-network
description: Wireless interface
physical id: 2
bus info: usb@1:5
logical name: wlan0
serial: 00:21:79:c5:c0:79
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated


hc.

---

### Post by Hanjaya on 2014-09-19
Please help me. Thx.

hc.

---

