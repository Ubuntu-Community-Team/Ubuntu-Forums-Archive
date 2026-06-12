---
title: "wlp4s0 Wifi on Ubuntu server?"
date: 2021-12-15
forum: Server Platforms
---

### Post by kandresen2000 on 2021-12-15
I currently got Ubuntu Desktop up and working on my laptop with Wifi networking enabled. What I really intend to do is run a minimal Ubuntu Server 20.04 within a KVM container and assign all hardware networks to it. This is partly working - the WIFI shutdown on my main system, and is assigned correctly to the VM, however, the Ubuntu Server does not detect my Wifi card. I have already installed the packages wpasuppliant, wireless-tools and libiw30, but even though the wireless network card is detected during boot-up in dmesg, the card is not initiated as a network device, and NOT listed under /sys/class/net . The wireless network card is auto-detected under Ubuntu Desktop 20.04 with the following from dmesg: 
rtw_8821ce 0000:04:00.0: Firmware version 24.8.0, H2C version 12
rtw_8821ce 0000:04:00.0 wlp4s0: renamed from wlan0
rtw_8821ce 0000:04:00.0: start vif ..:..:..:..:..:.. on port 0

Under Software and Updates --> additional drivers on the desktop, an alternative driver: Realtek Semiconductor Co, RTL8821CE 802.11ac is listed inactive as "Do not use the device", so at least on the desktop its unneeded. 

Am I missing some particular software, or is the reason this is not working that the sever kernel might be missing some options present in the desktop kernel? 

What is the best way to get this wifi network working for me under Ubuntu Server 20.04?

---

### Post by MAFoElffen on 2021-12-17
Check the Kernel versions on both the installed Server Edition and on the Desktop Edition... There were some issues of this wifi driver kernel module on some kernel versions. On the Desktop edition, it ma be using the HWE series Kernels, which may be newer.

If so, you can install the HWE package to a Server Edition and benefit from the hardware support of the Hardware Enablement Stack, with it's series of Kernels...

EDIT:
If you run the UbuntuForum's 'system-info' scirpt in my sig-line on it... There's is a section of the report that now only tells you with kernel the system is running, but a section on the HWE kernel series, the Generic kernel series, if the system is certified for, safe to install and run HWE. I wrote the Forum's script for both Desktop and Server Editions. It will quickly give you those answers.

---

