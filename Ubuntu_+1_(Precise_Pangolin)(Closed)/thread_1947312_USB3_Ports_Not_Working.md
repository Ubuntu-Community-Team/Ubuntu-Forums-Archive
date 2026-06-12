---
title: "USB3 Ports Not Working"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by suprman2020 on 2012-03-26
I have a Dell Vostro 3555. It uses the AMD A8-3500M. It has four usb ports. One of them is esata/usb and the remaining three are usb3.0.

I've been using Precise since the beta and the three usb3.0 ports do not work. Any ideas on how to fix it or what the problem could be?

Edit: Forgot to mention that they used to work in 11.10.

---

### Post by cariboo on 2012-03-26
Could you paste the output of:

```
dmesg | grep usb
```

in your next post?

---

### Post by suprman2020 on 2012-03-26
```
[    0.621460] usbcore: registered new interface driver usbfs
[    0.621460] usbcore: registered new interface driver hub
[    0.621460] usbcore: registered new device driver usb
[    2.280335] usbcore: registered new interface driver libusual
[    2.552109] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    2.960040] usb 3-2: new full-speed USB device number 2 using ohci_hcd
[    3.408122] usb 3-3: new full-speed USB device number 3 using ohci_hcd
[    3.684246] usb 8-2: new full-speed USB device number 2 using xhci_hcd
[   15.355473] usbcore: registered new interface driver btusb
[   15.412445] usbcore: registered new interface driver usbhid
[   15.412449] usbhid: USB HID core driver
[   15.454884] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input9
[   15.455048] usbcore: registered new interface driver uvcvideo
[   15.547608] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:10.1-2/input2
[   15.556632] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.2/0003:046D:C52B.0003/input/input11
[   15.556831] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:10.1-2:1
[  796.916334] Modules linked in: joydev pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) parport_pc ppdev vesafb rfcomm bnep bcma arc4 hid_logitech_dj dell_wmi sparse_keymap uvcvideo dell_laptop dcdbas videodev v4l2_compat_ioctl32 usbhid snd_hda_codec_idt hid snd_hda_codec_hdmi snd_seq_midi snd_rawmidi snd_seq_midi_event btusb bluetooth snd_seq psmouse snd_hda_intel serio_raw snd_hda_codec snd_hwdep snd_seq_device snd_pcm k10temp i2c_piix4 brcmsmac snd_timer fglrx(P) mac80211 snd brcmutil cfg80211 wmi crc8 cordic soundcore snd_page_alloc video mac_hid lp parport sdhci_pci sdhci pata_atiixp r8169
[ 1956.908266] usb 3-2: reset full-speed USB device number 2 using ohci_hcd
[ 1957.065257] usb 3-2: device firmware changed
[ 1957.065380] PM: resume of drv:btusb dev:3-2:1.1 complete after 499.203 msecs
[ 1957.065395] PM: resume of drv:btusb dev:3-2:1.0 complete after 499.423 msecs
[ 1957.065404] PM: resume of drv:usb dev:3-2:1.3 complete after 498.872 msecs
[ 1957.065435] PM: resume of drv:usb dev:3-2:1.2 complete after 499.086 msecs
[ 1957.256265] usb 3-3: reset full-speed USB device number 3 using ohci_hcd
[ 1957.421413] PM: resume of drv:usb dev:3-3:1.0 complete after 854.659 msecs
[ 1959.528827] usb 2-3: USB disconnect, device number 2
[ 1959.700128] usb 2-3: new high-speed USB device number 3 using ehci_hcd
[ 1959.990303] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input14
[ 1960.100231] usb 2-5: new high-speed USB device number 4 using ehci_hcd
[ 1960.256531] usb 8-2: USB disconnect, device number 2
[ 1960.308514] usbcore: registered new interface driver usb-storage
[ 1980.300971] usb 3-2: USB disconnect, device number 2
[ 1980.350536] usbcore: registered new interface driver uas
[ 1980.377051] scsi5 : usb-storage 2-5:1.0
[ 1980.377296] usbcore: registered new interface driver ums-realtek
[ 1980.688285] usb 3-2: new full-speed USB device number 4 using ohci_hcd
[ 1980.976206] usb 1-1: new high-speed USB device number 4 using ehci_hcd
[ 1981.111750] scsi6 : usb-storage 1-1:1.0
[ 1981.112220] usb 2-5: USB disconnect, device number 4
[ 2032.396206] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2032.652204] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2039.440325] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2039.752337] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2048.804322] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2049.076366] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2080.012126] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2080.300180] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2110.304134] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2110.588106] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2115.996310] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2116.256213] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2165.000187] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2165.256148] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2166.640127] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2166.928174] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2171.484138] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2171.752248] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2176.504132] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2176.760125] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2178.308304] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2178.568159] usb 1-1: reset high-speed USB device number 4 using ehci_hcd
[ 2213.896400] usb 1-1: USB disconnect, device number 4
[ 2214.304231] usb 3-1: new full-speed USB device number 5 using ohci_hcd
[ 2214.463098] usb 3-1: not running at top speed; connect to a high speed hub
[ 2214.477497] scsi7 : usb-storage 3-1:1.0
[ 2229.128227] usb 3-1: USB disconnect, device number 5
[ 2254.300293] usb 3-2: reset full-speed USB device number 4 using ohci_hcd
[ 2254.457485] usb 3-2: device firmware changed
[ 2254.457569] PM: resume of drv:usb dev:3-2:1.3 complete after 504.321 msecs
[ 2254.457592] PM: resume of drv:usb dev:3-2:1.2 complete after 504.372 msecs
[ 2254.457611] PM: resume of drv:btusb dev:3-2:1.1 complete after 504.411 msecs
[ 2254.457632] PM: resume of drv:btusb dev:3-2:1.0 complete after 504.493 msecs
[ 2254.648283] usb 3-3: reset full-speed USB device number 3 using ohci_hcd
[ 2254.813806] PM: resume of drv:usb dev:3-3:1.0 complete after 860.774 msecs
[ 2256.921305] usb 2-3: USB disconnect, device number 3
[ 2257.088188] usb 2-3: new high-speed USB device number 5 using ehci_hcd
[ 2257.374631] input: Laptop_Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input15
[ 2257.484119] usb 2-5: new high-speed USB device number 6 using ehci_hcd
[ 2257.661639] scsi8 : usb-storage 2-5:1.0
[ 2257.662004] usb 3-2: USB disconnect, device number 4
[ 2258.048207] usb 3-2: new full-speed USB device number 6 using ohci_hcd
[ 2258.226928] usb 2-5: USB disconnect, device number 6
[ 2546.244293] usb 3-1: new full-speed USB device number 7 using ohci_hcd
[ 2546.430692] logitech-djreceiver 0003:046D:C52B.0007: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input2
[ 2546.436714] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0007/input/input16
[ 2546.437307] logitech-djdevice 0003:046D:C52B.0008: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:12.0-1:1
[ 3147.755043] usb 3-1: USB disconnect, device number 7
[ 3153.084286] usb 1-1: new high-speed USB device number 6 using ehci_hcd
[ 3153.218295] scsi9 : usb-storage 1-1:1.0
[ 3753.200245] usb 1-1: USB disconnect, device number 6
[ 3769.720197] usb 3-1: new full-speed USB device number 8 using ohci_hcd
[ 3769.907150] logitech-djreceiver 0003:046D:C52B.000B: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input2
[ 3769.912712] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.000B/input/input17
[ 3769.913052] logitech-djdevice 0003:046D:C52B.000C: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:12.0-1:1
```

---

### Post by cariboo on 2012-03-26
I'd suggest you file a bug against linux, as it looks like the usb ports keep disconnectiong. Assuming you have a [launchpad account]("https://launchpad.net/"), open a terminal, or press Alt-F2 and type:

```
apport-bug linux
```

You'll be taken to a bug reporting page, where you can fill in the info about your problem.

---

### Post by suprman2020 on 2012-03-27
Thanks! Here's the bug report in case anybody else is having the same problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/966248)

---

