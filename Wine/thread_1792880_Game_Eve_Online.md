---
title: "Game: Eve Online"
date: 2011-06-28
forum: Wine
---

### Post by freeallforever on 2011-06-28
When I try to install allfonts it goes to tell me that the checksum did not match and after retrying it then says "sha1sum mismatch! Rename /home/anonymous/.cache/winetricks/droid/DroidSans-Bold.ttf and try again."

I am doing this because when trying to turn on the game eve online I have been able to install and accept user agreement and to patch and now I am at the login screen but there is no window to input text.

I am using the latest version of Ubuntu
I am using wine 1.3.15
I am using experimental videocard driver for nvidia because the proprietary one would not work at all.

Thank you

---

### Post by freeallforever on 2011-06-29
bump

---

### Post by freeallforever on 2011-07-02
bump

---

### Post by Gunman1982 on 2011-07-03
> **freeallforever said:**
> When I try to install allfonts it goes to tell me that the checksum did not match and after retrying it then says "sha1sum mismatch! Rename /home/anonymous/.cache/winetricks/droid/DroidSans-Bold.ttf and try again."

I am doing this because when trying to turn on the game eve online I have been able to install and accept user agreement and to patch and now I am at the login screen but there is no window to input text.

If you could accept the license agreement you should be trough with possible font problems.

> **freeallforever said:**
> 
I am using the latest version of Ubuntu
I am using wine 1.3.15
I am using experimental videocard driver for nvidia because the proprietary one would not work at all.
So you are using the nouveau driver? I don't know if it is sophisticated enough to provide the 3d capabilities you need for 3d in wine or rather eve trough wine. I don't know how far this nouveau/mesa/gallium/wine actually advanced until now.

What graphic card do you use? Open a console, issue the 'lspci' command and show the output.

---

### Post by freeallforever on 2011-07-04
> **Gunman1982 said:**
> If you could accept the license agreement you should be trough with possible font problems.


So you are using the nouveau driver? I don't know if it is sophisticated enough to provide the 3d capabilities you need for 3d in wine or rather eve trough wine. I don't know how far this nouveau/mesa/gallium/wine actually advanced until now.

What graphic card do you use? Open a console, issue the 'lspci' command and show the output.
I'm using the Experimental 3D support for NVIDIA cards which is free. The NVIDIA accelerated graphics driver which is proprietary would not function for me before, I reinstalled several times.


```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
09:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
09:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
09:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
09:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
```

---

### Post by freeallforever on 2011-07-06
bump

---

