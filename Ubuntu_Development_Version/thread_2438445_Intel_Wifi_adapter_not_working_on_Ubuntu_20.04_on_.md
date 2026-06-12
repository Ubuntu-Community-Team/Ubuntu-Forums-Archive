---
title: "Intel Wifi adapter not working on Ubuntu 20.04 on Fujitsu E Series Lifebook"
date: 2020-03-12
forum: Ubuntu Development Version
---

### Post by thecoder3281f on 2020-03-12
I had just did a backup using Timeshift. On my next boot, I realised that the wifi adapter doesn't work. 
  Here are the logs: 
  ```
Mar 11 15:31:25 jarrett-LIFEBOOK-E734 kernel: iwlwifi 0000:02:00.0: no suitable firmware found!
Mar 11 15:31:25 jarrett-LIFEBOOK-E734 kernel: iwlwifi 0000:02:00.0: iwlwifi-7260-17 is required
Mar 11 15:31:25 jarrett-LIFEBOOK-E734 kernel: iwlwifi 0000:02:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
Mar 11 15:31:25 jarrett-LIFEBOOK-E734 kernel: Bluetooth: hci0: failed to open Intel firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq (-2)
Mar 11 15:31:25 jarrett-LIFEBOOK-E734 kernel: Bluetooth: hci0: failed to open default fw file: intel/ibt-hw-37.7.bseq
Mar 11 15:31:28 jarrett-LIFEBOOK-E734 systemd[1]: Failed to start VirtualBox Linux kernel module.
Mar 11 15:46:48 jarrett-LIFEBOOK-E734 gdm-password][2515]: gkr-pam: unable to locate daemon control file
```
  What should I do?
  Output of lspci:
  ```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)
```

---

### Post by jeremy31 on 2020-03-12
Try ```
sudo apt install --reinstall linux-firmware
```
reboot

Moved to Ubuntu Dev Version

---

