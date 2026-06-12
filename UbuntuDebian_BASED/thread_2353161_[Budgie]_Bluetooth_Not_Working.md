---
title: "[Budgie] Bluetooth Not Working"
date: 2017-02-19
forum: Ubuntu/Debian BASED
---

### Post by wafitzpatrick on 2017-02-19
Hi All,

I've looked around the forums and the web and tried many troubleshooting tips  but can't get an answer. Was recently running Ubuntu 16.04 up until last week and did a hard disk upgrade and decided to try out a completely new install of Budgie (16.10).

With Ubuntu 16.04 bluetooth was working (though it is was temperamental - there was some issue with wireless network interfering, but I found a fix for that by changing some modprobe options for rtl8723ae).

So now in Budgie 16.10 - bluetooth doesn't start - the icon shows it enabled and the Budgie default manager says its on (but the UI switch shows off). Attempts to switch the UI switch just hang and fail.

The only way I can get the bluetooth to 'turn on' is to use modprobe -r and reload - this gets the the Bluetooth to be recognised, but it then doesn't find any devices.

This is an MSI CX61 - the bluetooth device is integrated.

Any suggestions or help greatly appreciated!

lsusb:

```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:3394 IMC Networks Bluetooth
Bus 001 Device 008: ID 056a:033b Wacom Co., Ltd 
Bus 001 Device 009: ID 0557:2213 ATEN International Co., Ltd CS682 2-Port USB 2.0 DVI KVM Switch
Bus 001 Device 007: ID 0557:8021 ATEN International Co., Ltd CS1764A [CubiQ DVI KVMP Switch]
Bus 001 Device 006: ID 099a:0721 Zippy Technology Corp. 
Bus 001 Device 005: ID 1e7d:2c2e ROCCAT 
Bus 001 Device 003: ID 2109:2811 VIA Labs, Inc. Hub
Bus 001 Device 011: ID 5986:014c Acer, Inc 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 05c6:6765 Qualcomm, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dpkg -s bluez:

```

Package: bluez
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 4127
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 5.41-0ubuntu3
Replaces: bluez-alsa, bluez-audio (<= 3.36-3), bluez-input, bluez-network, bluez-serial, bluez-utils (<= 3.36-3), udev (<< 170-1)
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.9.14), libglib2.0-0 (>= 2.31.8), libreadline7 (>= 6.0), libudev1 (>= 196), init-system-helpers (>= 1.18~), kmod, udev (>= 170-1), lsb-base, dbus
Breaks: udev (<< 170-1)
Conflicts: bluez-alsa, bluez-audio (<= 3.36-3), bluez-utils (<= 3.36-3)
Conffiles:
 /etc/bluetooth/input.conf 9f85017f861ac34d983fa76fa715f9c3
 /etc/bluetooth/main.conf 445fdaa9def1ffaa873df2447ba22004
 /etc/bluetooth/network.conf 0c7497c405b963382ff71789d0730abd
 /etc/bluetooth/proximity.conf b75823a140e00905d41465c380bf89fe
 /etc/dbus-1/system.d/bluetooth.conf 2fd2de572a1221533e707d058e64e33a
 /etc/init.d/bluetooth 33ed7811d65a775cf10f04c2e6ee3cbf
 /etc/init/bluetooth.conf c7e11afe4581c8829a79a5ac8aa558b5
Description: Bluetooth tools and daemons
 This package contains tools and system daemons for using Bluetooth devices.
 .
 BlueZ is the official Linux Bluetooth protocol stack. It is an Open Source
 project distributed under GNU General Public License (GPL).
Homepage: http://www.bluez.org
Original-Maintainer: Debian Bluetooth Maintainers <pkg-bluetooth-maintainers@lists.alioth.debian.org>

```

sudo service bluetooth status:

```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-02-19 18:26:34 GMT; 48min ago
     Docs: man:bluetoothd(8)
 Main PID: 1227 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1227 /usr/lib/bluetooth/bluetoothd


Feb 19 18:26:35 FitzMSI bluetoothd[1227]: Starting SDP server
Feb 19 18:26:35 FitzMSI bluetoothd[1227]: Bluetooth management interface 1.13 initialized
Feb 19 18:26:35 FitzMSI bluetoothd[1227]: Failed to obtain handles for "Service Changed" characteristic
Feb 19 18:26:36 FitzMSI bluetoothd[1227]: Sap driver initialization failed.
Feb 19 18:26:36 FitzMSI bluetoothd[1227]: sap-server: Operation not permitted (1)
Feb 19 18:27:02 FitzMSI bluetoothd[1227]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/A2DPSour
Feb 19 18:27:02 FitzMSI bluetoothd[1227]: Endpoint registered: sender=:1.39 path=/MediaEndpoint/A2DPSink
Feb 19 18:27:25 FitzMSI bluetoothd[1227]: Failed to set mode: Failed (0x03)
Feb 19 18:28:20 FitzMSI bluetoothd[1227]: Failed to set mode: Failed (0x03)
Feb 19 18:55:55 FitzMSI bluetoothd[1227]: Failed to set mode: Failed (0x03)

```

bluetoothctl / show:

```

Controller 80:A5:89:68:B3:0F
    Name: FitzMSI
    Alias: FitzMSI
    Class: 0x000000
    Powered: no
    Discoverable: no
    Pairable: yes
    UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
    UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
    UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
    UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0529
    Discovering: no

[bluetooth]# discoverable on
Changing discoverable on succeeded
[CHG] Controller 80:A5:89:68:B3:0F Discoverable: yes
[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.NotReady


```

hciconfig:

```
$ sudo hciconfig hci0 up
Can't init device hci0: Connection timed out (110)
$ sudo hciconfig hci0 reset
Can't init device hci0: Connection timed out (110)

```

dmesg | egrep -i 'blue|firm'

```

[    0.142726] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.199757] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    2.040309] usb 1-1.3: Product: RT Bluetooth Radio
[    2.061635] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[    8.984867] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   12.362286] Bluetooth: Core ver 2.21
[   12.362296] Bluetooth: HCI device and connection manager initialized
[   12.362298] Bluetooth: HCI socket layer initialized
[   12.362299] Bluetooth: L2CAP socket layer initialized
[   12.362303] Bluetooth: SCO socket layer initialized
[   12.883973] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=1200
[   12.883974] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723a_fw.bin
[   24.114559] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.114560] Bluetooth: BNEP filters: protocol multicast
[   24.114562] Bluetooth: BNEP socket layer initialized
[   51.529817] Bluetooth: RFCOMM TTY layer initialized
[   51.529821] Bluetooth: RFCOMM socket layer initialized
[   51.529909] Bluetooth: RFCOMM ver 1.11
[   66.032758] Bluetooth: hci0 urb ffffa1f9d98d5d80 failed to resubmit (113)
[  121.072641] Bluetooth: hci0 urb ffffa1f9d99bd3c0 failed to resubmit (113)
[ 1775.936450] Bluetooth: hci0 urb ffffa1f9d9eb4240 failed to resubmit (113)
[ 1775.936821] Bluetooth: hci0 urb ffffa1f9d9eb4f00 failed to resubmit (113)
[ 1872.965728] Bluetooth: hci0 urb ffffa1f9d23f03c0 failed to resubmit (113)
[ 1872.966107] Bluetooth: hci0 urb ffffa1f9d23f0a80 failed to resubmit (113)
[ 1899.087077] Bluetooth: hci0 urb ffffa1f8d8320180 failed to resubmit (113)
[ 1899.087578] Bluetooth: hci0 urb ffffa1f8d8320f00 failed to resubmit (113)
[ 2131.027874] Bluetooth: hci0 urb ffffa1f8fd6b6540 failed to resubmit (113)
[ 2131.028291] Bluetooth: hci0 urb ffffa1f8fd6b6f00 failed to resubmit (113)
[ 3161.129753] Bluetooth: hci0 urb ffffa1f9dbf1d3c0 failed to resubmit (113)
[ 3161.130097] Bluetooth: hci0 urb ffffa1f9dbf1de40 failed to resubmit (113)
[ 3177.094688] Bluetooth: hci0 urb ffffa1f9dbf1d780 failed to resubmit (113)
[ 3177.095023] Bluetooth: hci0 urb ffffa1f9dbf1d240 failed to resubmit (113)

```

---

### Post by jhecohe on 2017-05-03
Do you  fixed the problem?, i have the same problem with ubuntu budgie 17.04

---

### Post by wafitzpatrick on 2017-05-06
I didn't manage to solve it, I gave up and went for full Ubuntu install over the top - but although it seemed to successfully find and connect to my device, it still didn't work.

I haven't upgraded to 17.04 yet but all I can tell you is it seems to be Ubuntu-wide and not specific to that distro. I quite like Budgie so I'll probably reinstall it.

I can only assume that Bluetooth is broken for my MSI laptop (after working perfectly from 15.04+) - I haven't had time to search for troubleshooting the issue unfortunately so I'm just hoping it will fix when I upgrade.

---

### Post by danmayadan on 2018-04-24
Same problem! Any ideias?

---

### Post by wafitzpatrick on 2018-04-25
Hi,

Never managed to solve the problem. instead, I upgraded my wifi card - it's fairly straightforward and cheap.

[Intel Wireless-AC 3160]("https://www.amazon.co.uk/gp/product/B00MYROS5U") - I can confirm that this card works beautifully with Ubuntu 17.10 on an MSI CX61.

---

