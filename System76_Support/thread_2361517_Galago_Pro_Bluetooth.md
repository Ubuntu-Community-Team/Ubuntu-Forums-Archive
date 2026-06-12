---
title: "Galago Pro Bluetooth"
date: 2017-05-17
forum: System76 Support
---

### Post by egarff on 2017-05-17
Greetings,

I cannot get Bluetooth working on my new galago pro, running the preinstalled ubuntu 16.04.  

From dmesg:

[ 3884.457881] Bluetooth: hci0: Bootloader revision 0.0 build 26 week 38 2015
[ 3884.458939] Bluetooth: hci0: Device revision is 16
[ 3884.458939] Bluetooth: hci0: Secure boot is enabled
[ 3884.458940] Bluetooth: hci0: OTP lock is enabled
[ 3884.458940] Bluetooth: hci0: API lock is enabled
[ 3884.458940] Bluetooth: hci0: Debug lock is disabled
[ 3884.458941] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[ 3884.458954] bluetooth hci0: Direct firmware load for intel/ibt-12-16.sfi failed with error -2
[ 3884.458955] Bluetooth: hci0: Failed to load Intel firmware file (-2)

blueman, all options are greyed out.

From lspci

bluetooth             557056  14 btrtl,hci_uart,btintel,btqca,bnep,btbcm,btusb

Per the bluetooth guide, I've been stepping through the steps, and I get this error:

~$ pactl load-module module-bluetooth-discover
Failure: Module initialization failed

Your help is greatly appreciated.

---

### Post by egarff on 2017-05-17
Ok, I should have continued on in the document, but this is something to note for future Galago Pro shipments... upgrading the linux-firmware to the latest has resolved it.

---

### Post by Geoffrey_Arndt on 2017-05-19
In other words, the latest update from the System76 PPA . . . or are you referring to BIOS update by the OEM/OED?

---

