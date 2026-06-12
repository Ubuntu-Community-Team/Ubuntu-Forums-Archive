---
title: "USB in WINE"
date: 2009-05-02
forum: Wine
---

### Post by Vangelis666 on 2009-05-02
Ok, I have googled and googled and can't find any definitive answers on using USB under WINE (well not that is applicable to my situation). Here are the details:

1. WINE version 1.0.1
2. Ubuntu version 9.04
3. Device being connected: Garmin Edge 305 - GPS-enabled computer for cyclists.
4. Output from lsusb:
> Bus 002 Device 005: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 003 Device 003: ID 0c45:613b Microdia Win2 PC Camera
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub5. Output from lsusb -v -s 004:003
> Bus 004 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x091e Garmin International
  idProduct          0x0003 GPSmap (various models)
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)6. About the only thing I have found when I googled is that I can create a symbolic link for /dev/ttyUSB0 but this doesn't exist. Here's my /dev directory listing:
> adsp                ptmx        snd      tty46           usbdev3.3_ep81
audio               pts         sndstat  tty47           usbdev3.3_ep82
block               radio0      sr0      tty48           usbdev3.3_ep83
bus                 ram0        stderr   tty49           usbdev4.1_ep00
cdrom               ram1        stdin    tty5            usbdev4.1_ep81
cdrw                ram10       stdout   tty50           usbdev4.3_ep00
char                ram11       tty      tty51           usbdev4.3_ep02
console             ram12       tty0     tty52           usbdev4.3_ep81
core                ram13       tty1     tty53           usbdev4.3_ep83
cpu_dma_latency     ram14       tty10    tty54           usbdev5.1_ep00
disk                ram15       tty11    tty55           usbdev5.1_ep81
dsp                 ram2        tty12    tty56           usbdev6.1_ep00
dvd                 ram3        tty13    tty57           usbdev6.1_ep81
dvdrw               ram4        tty14    tty58           usbdev7.1_ep00
ecryptfs            ram5        tty15    tty59           usbdev7.1_ep81
fd                  ram6        tty16    tty6            usbmon0
full                ram7        tty17    tty60           usbmon1
fuse                ram8        tty18    tty61           usbmon2
hpet                ram9        tty19    tty62           usbmon3
initctl             random      tty2     tty63           usbmon4
input               rtc         tty20    tty7            usbmon5
kmem                rtc0        tty21    tty8            usbmon6
kmsg                scd0        tty22    tty9            usbmon7
log                 sda         tty23    ttyS0           v4l
loop0               sda1        tty24    ttyS1           vbi0
loop1               sda2        tty25    ttyS2           vcs
loop2               sda5        tty26    ttyS3           vcs1
loop3               sda6        tty27    urandom         vcs2
loop4               sdb         tty28    usbdev1.1_ep00  vcs3
loop5               sdc         tty29    usbdev1.1_ep81  vcs4
loop6               sdd         tty3     usbdev2.1_ep00  vcs5
loop7               sde         tty30    usbdev2.1_ep81  vcs6
lp0                 sdf         tty31    usbdev2.2_ep00  vcs7
mapper              sdf1        tty32    usbdev2.2_ep02  vcs8
mem                 sdg         tty33    usbdev2.2_ep81  vcsa
mixer               sdg1        tty34    usbdev2.3_ep00  vcsa1
net                 sequencer   tty35    usbdev2.3_ep02  vcsa2
network_latency     sequencer2  tty36    usbdev2.3_ep81  vcsa3
network_throughput  sg0         tty37    usbdev2.5_ep00  vcsa4
null                sg1         tty38    usbdev2.5_ep02  vcsa5
nvidia0             sg2         tty39    usbdev2.5_ep81  vcsa6
nvidiactl           sg3         tty4     usbdev3.1_ep00  vcsa7
oldmem              sg4         tty40    usbdev3.1_ep81  vcsa8
parport0            sg5         tty41    usbdev3.2_ep00  video0
pktcdvd             sg6         tty42    usbdev3.2_ep03  video1
port                sg7         tty43    usbdev3.2_ep81  watchdog
ppp                 shm         tty44    usbdev3.2_ep82  xconsole
psaux               snapshot    tty45    usbdev3.3_ep00  zero
So... That's all the information I can think of specifying. If anyone knows whether what I am doing is possible or not, I would appreciate their comments. If you require any more information, please let me know.

Kind Regards,

Vangelis

---

### Post by asdfoo on 2009-05-02
> **Vangelis666 said:**
> Ok, I have googled and googled and can't find any definitive answers on using USB under Wine (well not that is applicable to my situation). Here are the details:

1. Wine version 1.0.1
2. Ubuntu version 9.04
3. Device being connected: Garmin Edge 305 - GPS-enabled computer for cyclists.
4. Output from lsusb:
5. Output from lsusb -v -s 004:003
6. About the only thing I have found when I googled is that I can create a symbolic link for /dev/ttyUSB0 but this doesn't exist. Here's my /dev directory listing:
So... That's all the information I can think of specifying. If anyone knows whether what I am doing is possible or not, I would appreciate their comments. If you require any more information, please let me know.

Kind Regards,

Vangelis

[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

If /dev/ttyUSB0 doesn't exist then perhaps then you will need to solve this problem before coming to Wine.

Check the output of dmesg to look for your device... maybe you need to install a linux driver?

---

