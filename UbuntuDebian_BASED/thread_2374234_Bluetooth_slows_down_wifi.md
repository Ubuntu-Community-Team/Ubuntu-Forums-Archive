---
title: "Bluetooth slows down wifi"
date: 2017-10-13
forum: Ubuntu/Debian BASED
---

### Post by webdevel-fr on 2017-10-13
Hi everybody,
Everything are in the title. When I connect my a2dp bt headphones, my wifi connection fall to 100kb.s. 
I need your inspiration to help me find.

---

### Post by webdevel-fr on 2017-10-13
lspci -vvv :

[https://pastebin.com/i3yWy5wh](https://pastebin.com/i3yWy5wh)

dmidecode :

[https://pastebin.com/LjMnKAZq](https://pastebin.com/LjMnKAZq)

---

### Post by webdevel-fr on 2017-10-13
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth

```
Linux Nalyssa 4.13.0-kali1-amd64 #1 SMP Debian 4.13.4-1kali1 (2017-10-03) x86_64 GNU/Linux
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Lite-On Communications Inc QCA9377 802.11ac Wireless Network Adapter [11ad:08a6]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:108f]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   17.017061] Bluetooth: Core ver 2.22
[   17.017070] Bluetooth: HCI device and connection manager initialized
[   17.017072] Bluetooth: HCI socket layer initialized
[   17.017074] Bluetooth: L2CAP socket layer initialized
[   17.017079] Bluetooth: SCO socket layer initialized
[   21.593756] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.593759] Bluetooth: BNEP filters: protocol multicast
[   21.593764] Bluetooth: BNEP socket layer initialized
[   24.983401] Bluetooth: RFCOMM TTY layer initialized
[   24.983415] Bluetooth: RFCOMM socket layer initialized
[   24.983426] Bluetooth: RFCOMM ver 1.11
[    0.322163] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.567120] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x4d5f02)
[   16.009536] i915 0000:00:02.0: firmware: direct-loading firmware i915/kbl_dmc_ver1_01.bin
[   16.009866] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[   16.065363] [Firmware Bug]: ACPI(PXSX) defines _DOD but not _DOS
[   16.309717] ath10k_pci 0000:03:00.0: firmware: failed to load ath10k/pre-cal-pci-0000:03:00.0.bin (-2)
[   16.309753] ath10k_pci 0000:03:00.0: firmware: failed to load ath10k/cal-pci-0000:03:00.0.bin (-2)
[   16.310139] ath10k_pci 0000:03:00.0: firmware: failed to load ath10k/QCA9377/hw1.0/firmware-6.bin (-2)
[   16.314697] ath10k_pci 0000:03:00.0: firmware: direct-loading firmware ath10k/QCA9377/hw1.0/firmware-5.bin
[   16.315914] ath10k_pci 0000:03:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7
[   16.392273] ath10k_pci 0000:03:00.0: firmware: direct-loading firmware ath10k/QCA9377/hw1.0/board-2.bin
[   22.209443] r8169 0000:04:00.1: firmware: direct-loading firmware rtl_nic/rtl8411-2.fw
[ 7332.389622] rtsx_pci 0000:04:00.0: VPD access failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update
bluetooth             540672  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
rfkill                 24576  7 bluetooth,acer_wmi,cfg80211
crc16                  16384  2 bluetooth,ext4
```

---

### Post by webdevel-fr on 2017-10-13
Separated, wifi and bluetooth works perfectly. But together, my headphones works well but not my wifi network speed. I wonder if it is common hardware for both. And I didn't test if it is only for a2dp protocol.

---

### Post by jeremy31 on 2017-10-14
Moved to Ubuntu/Debian based as you are using Kali
You may want to file a bug report against package Linux as I don't see the normal firmware upload for this chipset.  Your bluetooth hasn't been added to correct section in the btusb.c yet as it currently has
```
	/* QCA ROME chipset */
	{ USB_DEVICE(0x0cf3, 0xe007), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0cf3, 0xe009), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0cf3, 0xe300), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0cf3, 0xe301), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0cf3, 0xe360), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0489, 0xe092), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x0489, 0xe0a2), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x04ca, 0x3011), .driver_info = BTUSB_QCA_ROME },
	{ USB_DEVICE(0x04ca, 0x3016), .driver_info = BTUSB_QCA_ROME },
```
I am surprised it works at all without the firmware

---

### Post by webdevel-fr on 2017-10-14
First of all, thanks for the answer.
Then, I'm  not quite sure to understand. You are talking about btusb.c and, for me, it is sources. Could you tell me what firmware for what chipset please.

---

