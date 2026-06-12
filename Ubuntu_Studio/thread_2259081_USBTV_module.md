---
title: "USBTV module"
date: 2015-01-01
forum: Ubuntu Studio
---

### Post by Dr.Death on 2015-01-01
Hello, i have this USB SRD "Gadmei USB TVBox UTV382 (id 0x1f71:0x3301)" 
[http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_%28id_0x1f71:0x3301%29](http://linuxtv.org/wiki/index.php/Gadmei_USB_TVBox_UTV382_%28id_0x1f71:0x3301%29)

from the link it said to download the module modify it and install it, and it should work fine.

but the new kernels 3.16 include usbtv as kernel module by default, but only for the module:
> 	{ USB_DEVICE(0x1b71, 0x3002) }
not for:
> 	{ USB_DEVICE(0x1f71, 0x3301) }

not sure how to do it correctly, so i download v4l-DVB as in the link:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

and modified the USBTV module that came with it, and install v4l

but nothing change !!

#dmesg:
```
[29850.711041] usb 2-4: new high-speed USB device number 6 using ehci-pci
[29850.830828] usb 2-4: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[29850.834326] usb 2-4: New USB device found, idVendor=1f71, idProduct=3301
[29850.834331] usb 2-4: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[29850.834334] usb 2-4: Product: USB TV Box
[29850.834337] usb 2-4: Manufacturer: Gadmei
[29850.834339] usb 2-4: SerialNumber: 330000000009

```

```

#sudo modprobe usbtv

#lsmod | grep usbtv
usbtv                  18299  0 
videobuf2_vmalloc      13440  2 usbtv,uvcvideo
videobuf2_core         48033  2 usbtv,uvcvideo
v4l2_common            14161  2 usbtv,videobuf2_core
videodev              130734  4 usbtv,uvcvideo,v4l2_common,videobuf2_core
snd_pcm                91884  5 usbtv,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd                    63701  25 snd_hda_codec_realtek,usbtv,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device

#lsusb
Bus 002 Device 006: ID 1f71:3301 

```


not sure whats wrong, please advise

Thanks

---

