---
title: "Getting my USB sound card working"
date: 2013-04-16
forum: Ubuntu Studio
---

### Post by d94asu on 2013-04-16
Hi,

I am trying to get Ubuntu studio to recognize my sound card, but I are not experienced enough to get it working on my own. I have a Focusrite Scarlett 2i4. When connecting it to the computer I can see the following line when running lsusb:

Bus 002 Device 012: ID 1235:800a Novation EMS

which has to do with my sound card.

The output from following commands does not mention the card
  aplay -l
  cat /proc/asound/cards
  cat /proc/asound/devices

There are some information on alsa web page:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Focusrite](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Focusrite)
I also read some information on ubuntu.com, but I can not grasp it.

Any ideas are welcome

  /Andreas

---

### Post by jejeman on 2013-04-16
If the audio card is listed in lsusb output then it is recognized.
If the audio card is not listed in aplay -l output then it is not supported.

Which version of Ubuntu studio are you using?
With card pluged in Give
```
lsmod | grep snd
```
```
dmesg | grep -i usb
```

---

### Post by d94asu on 2013-04-17
It is obvious I do not know what I'm doing. I did try to follow the instruction on [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio) trying to build some kernel modules, and when I got to alsa-utils I got some compiler problems. Then I thought that since I'm running Ubuntu Studio maybe it was better prepared for me. So then I tried out the sound card, and I got in touch with the forum. Today I rebooted the computer, and now I have contact with the sound card :)

Now I only see that sound card. 

andreas@andreas:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: USB [Scarlett 2i4 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andreas@andreas:~/Desktop$

which is definitely a step up. But I think I'd like use the build in sound card at some point.

I run this version: Ubuntu 12.04.2 LTS
andreas@andreas:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: USB [Scarlett 2i4 USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andreas@andreas:~/Desktop$ lsmod | grep snd
snd_usb_audio         117370  2 
snd_pcm_oss            45432  0 
snd_mixer_oss          22310  1 snd_pcm_oss
snd_pcm                96414  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         18484  1 snd_pcm
snd_hwdep              17659  1 snd_usb_audio
snd_usbmidi_lib        24952  1 snd_usb_audio
snd_rawmidi            30569  1 snd_usbmidi_lib
snd_seq_oss            38238  0 
snd_seq_midi_event     14899  1 snd_seq_oss
snd_seq                61553  4 snd_seq_oss,snd_seq_midi_event
snd_timer              29532  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_rawmidi,snd_seq_oss,snd_seq
snd                    72432  15 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
andreas@andreas:~/Desktop$ dmesg | grep -i usb
[    1.407289] usbcore: registered new interface driver usbfs
[    1.407297] usbcore: registered new interface driver hub
[    1.407315] usbcore: registered new device driver usb
[    2.035151] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.035225] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.048725] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.048921] hub 1-0:1.0: USB hub found
[    2.049047] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.062706] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.062878] hub 2-0:1.0: USB hub found
[    2.062930] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.062942] uhci_hcd: USB Universal Host Controller Interface driver
[    2.063039] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 3
[    2.074226] hub 3-0:1.0: USB hub found
[    2.074315] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    2.074416] hub 4-0:1.0: USB hub found
[    2.092751] usbcore: registered new interface driver libusual
[    2.350569] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.465300] hub 1-1:1.0: USB hub found
[    2.568171] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.683422] hub 2-1:1.0: USB hub found
[    2.758372] usb 1-1.1: new full-speed USB device number 3 using ehci_hcd
[    2.822031] usb 1-1.1: device descriptor read/64, error -32
[    3.084211] usb 1-1.2: new high-speed USB device number 4 using ehci_hcd
[    3.375628] usb 1-1.4: new high-speed USB device number 5 using ehci_hcd
[    3.527331] usb 2-1.2: new low-speed USB device number 3 using ehci_hcd
[   15.292474] Initializing rts5139 USB card reader driver...
[   15.292924] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   15.294094] usbcore: registered new interface driver btusb
[   15.294773] uvcvideo: Found UVC 1.00 device ASUS USB2.0 WebCam (058f:a014)
[   15.296066] scsi6 : SCSI emulation for RTS5139 USB card reader
[   15.296228] usbcore: registered new interface driver rts5139
[   15.296231] Realtek rts5139 USB card reader support registered.
[   15.297622] input: ASUS USB2.0 WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[   15.297880] usbcore: registered new interface driver uvcvideo
[   15.297888] USB Video Class driver (1.1.1)
[   15.324521] input: Lite-On Technology Corp. USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input6
[   15.324773] generic-usb 0003:04CA:0030.0001: input,hidraw0: USB HID v1.10 Mouse [Lite-On Technology Corp. USB Mouse] on usb-0000:00:1d.0-1.2/input0
[   15.324785] usbcore: registered new interface driver usbhid
[   15.324787] usbhid: USB HID core driver
[  282.758046] usb 2-1.1: new high-speed USB device number 4 using ehci_hcd
[  283.950587] usbcore: registered new interface driver snd-usb-audio
[ 1200.861609] usb 2-1.2: USB disconnect, device number 3
[ 1201.072467] usb 2-1.2: new low-speed USB device number 5 using ehci_hcd
[ 1201.176606] input: Lite-On Technology Corp. USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input10
[ 1201.177051] generic-usb 0003:04CA:0030.0002: input,hidraw0: USB HID v1.10 Mouse [Lite-On Technology Corp. USB Mouse] on usb-0000:00:1d.0-1.2/input0

---

