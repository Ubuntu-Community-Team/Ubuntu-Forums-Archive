---
title: "Audacity hangs while recording.."
date: 2009-05-24
forum: Ubuntu Studio
---

### Post by chetvolpe on 2009-05-24
Running ubuntu 9.04 on a 1GHz AMD 32 bit processor and Audacity 1.3.7. Recording via USB from an Ion turntable and at random points in the recording process (anywhere from 3 to 20 minutes) CPU goes to 100 % and Audacity just stops recording. Monitoring the playback from the turntable and it continues to play. I am including the log file info at the time of the failure. I have attached a screen shot and results of lshw. While it works, it works well... Any help would be much appreciated - Chet

May 24 11:30:35 ubuntu kernel: [1008723.208416] usb 1-1.1: USB disconnect, address 63
May 24 11:30:35 ubuntu kernel: [1008723.505361] usb 1-1.1: new full speed USB device using ohci_hcd and address 64
May 24 11:30:35 ubuntu kernel: [1008723.626738] usb 1-1.1: configuration #1 chosen from 1 choice
May 24 11:30:35 ubuntu kernel: [1008723.822570] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:01.2/usb1/1-1/1-1.1/1-1.1:1.3/input/input63
May 24 11:30:35 ubuntu kernel: [1008723.844500] generic-usb 0003:08BB:2900.003A: input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:01.2-1.1/input3
May 24 11:30:37 ubuntu pulseaudio[3480]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May 24 11:30:44 ubuntu kernel: [1008732.205785] usb 1-1.1: USB disconnect, address 64
May 24 11:30:44 ubuntu kernel: [1008732.505741] usb 1-1.1: new full speed USB device using ohci_hcd and address 65
May 24 11:30:44 ubuntu kernel: [1008732.619008] usb 1-1.1: configuration #1 chosen from 1 choice
May 24 11:30:44 ubuntu kernel: [1008732.795017] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:01.2/usb1/1-1/1-1.1/1-1.1:1.3/input/input64
May 24 11:30:44 ubuntu kernel: [1008732.828427] generic-usb 0003:08BB:2900.003B: input,hidraw0: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:01.2-1.1/input3
May 24 11:30:46 ubuntu pulseaudio[3480]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

---

