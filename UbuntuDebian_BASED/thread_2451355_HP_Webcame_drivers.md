---
title: "HP Webcame drivers"
date: 2020-10-02
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2020-10-02
Hi!
I'm running PopOS on a Laptop: HP Pavillion 17 -e004ed and it has a integrated webcame onboard, i believe from Intel, on windows it worked but on Mint en PopOS it doesnt work. It isn't even detected as far as i know (im a noob in linux btw)
I couldn't find a driver on Mint for it nor could i find one on the internet, do you know how to fixt this?

---

### Post by jeremy31 on 2020-10-02
Moved to Ubuntu/Debian based

---

### Post by CelticWarrior on 2020-10-02
Please try 'lsusb' and 'lspci'. In one of those there should be a reference to the webcam. Please post that line.

---

### Post by Disabled20241022 on 2020-10-03
I have kernel 5.8.12 installed.

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
0:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

```

I think that when i first tried linux a year ago that the cam worked. just saying.

---

### Post by Disabled20241022 on 2020-10-03
Also tried it using KVM and then the latest ubuntu but failed to recognise the camera
I just tried a windows iso on KVM without internet and the camera app in windows also says cannot find a device.

There is no option in my bios for a webcame. whats going on?

---

### Post by CelticWarrior on 2020-10-03
Defective hardware.
Please contact tech support.

---

### Post by Disabled20241022 on 2020-10-03
Tech support from? (HP?)

---

### Post by CelticWarrior on 2020-10-03
Or the nearest computer store.

The point is if it isn't recognized and was before, if not detected with another OS, the conclusion is obvious.

---

### Post by Disabled20241022 on 2020-10-03
i have to say that it was detected on the first install of linux next to windows. then i went back to windows and half a year later back to linux. so formated drive etc.. does that make a change? So its not that it just stopt working on the same software system.

---

### Post by CelticWarrior on 2020-10-03
Precisely because it happens in different OSes you should conclude hardware failure.

---

