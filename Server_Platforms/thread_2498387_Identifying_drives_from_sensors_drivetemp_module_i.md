---
title: "Identifying drives from sensors drivetemp module is a pain so i made this"
date: 2024-06-11
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2024-06-11
knowing what drive i am looking at is a pain:
```
[FONT=monospace][COLOR=#000000]$ sensors drivetemp-* [/COLOR]
drivetemp-scsi-11-0 
Adapter: SCSI adapter 
temp1:        +32.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +27.0°C, highest = +36.0°C) 

drivetemp-scsi-9-0 
Adapter: SCSI adapter 
temp1:        +31.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +26.0°C, highest = +35.0°C) 

drivetemp-scsi-4-0 
Adapter: SCSI adapter 
temp1:        +50.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +29.0°C, highest = +63.0°C) 

drivetemp-scsi-0-0 
Adapter: SCSI adapter 
temp1:        +50.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +28.0°C, highest = +66.0°C) 

drivetemp-scsi-12-0 
Adapter: SCSI adapter 
temp1:        +31.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +26.0°C, highest = +35.0°C) 

drivetemp-scsi-10-0 
Adapter: SCSI adapter 
temp1:        +32.0°C  (low  =  +0.0°C, high = +65.0°C) 
                       (crit low = -41.0°C, crit = +85.0°C) 
                       (lowest = +27.0°C, highest = +36.0°C) 

drivetemp-scsi-5-0 
Adapter: SCSI adapter 
temp1:        +50.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +29.0°C, highest = +63.0°C) 

drivetemp-scsi-1-0 
Adapter: SCSI adapter 
temp1:        +52.0°C  (low  =  +0.0°C, high = +100.0°C) 
                       (crit low =  +0.0°C, crit = +100.0°C) 
                       (lowest = +29.0°C, highest = +68.0°C)
[/FONT]
```
So i made a few versions of a script in PHP so i know the model, temp, serial, and a few was to identify the drive both as the hardware and software level, here is the output
```
[FONT=monospace][COLOR=#000000]$ ./ls_drives [/COLOR]
DEV: ata1 
        Temperature: +50.0°C (28.0°C to 66.0°C) 
        DEVNAME: /dev/sda 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_WWN: 0x55cd2e414f4a6b29 
        ID_SERIAL_SHORT: BTLA81061ECP128I 
        ID_PATH: pci-0000:15:00.1-ata-1.0 
DEV: ata2 
        Temperature: +52.0°C (29.0°C to 68.0°C) 
        DEVNAME: /dev/sdb 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_WWN: 0x55cd2e414f579528 
        ID_SERIAL_SHORT: BTLA81510DU3128I 
        ID_PATH: pci-0000:15:00.1-ata-2.0 
DEV: ata5 
        Temperature: +51.0°C (29.0°C to 63.0°C) 
        DEVNAME: /dev/sdc 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_WWN: 0x55cd2e414f4a0b50 
        ID_SERIAL_SHORT: BTLA810613SC128I 
        ID_PATH: pci-0000:15:00.1-ata-5.0 
DEV: ata6 
        Temperature: +51.0°C (29.0°C to 63.0°C) 
        DEVNAME: /dev/sdh 
        ID_MODEL: INTEL_SSDSCKKF12 
        ID_WWN: 0x55cd2e414f4afc55 
        ID_SERIAL_SHORT: BTLA810616PX128I 
        ID_PATH: pci-0000:15:00.1-ata-6.0 
DEV: usb1 
        DEVNAME: /dev/sdd 
        ID_MODEL: Compact_Flash 
        ID_SERIAL_SHORT: 20060413092100000 
        ID_PATH: pci-0000:15:00.0-usb-0:8:1.0-scsi-0:0:0:0 
DEV: usb1 
        DEVNAME: /dev/sde 
        ID_MODEL: SM_xD-Picture 
        ID_SERIAL_SHORT: 20060413092100000 
        ID_PATH: pci-0000:15:00.0-usb-0:8:1.0-scsi-0:0:0:1 
DEV: usb1 
        DEVNAME: /dev/sdf 
        ID_MODEL: SD_MMC 
        ID_SERIAL_SHORT: 20060413092100000 
        ID_PATH: pci-0000:15:00.0-usb-0:8:1.0-scsi-0:0:0:2 
DEV: usb1 
        DEVNAME: /dev/sdg 
        ID_MODEL: MS_MS-Pro 
        ID_SERIAL_SHORT: 20060413092100000 
        ID_PATH: pci-0000:15:00.0-usb-0:8:1.0-scsi-0:0:0:3 
DEV: ata10 
        Temperature: +31.0°C (26.0°C to 35.0°C) 
        DEVNAME: /dev/sdi 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_WWN: 0x50014ee263e2b396 
        ID_SERIAL_SHORT: WD-WCC7K7KKNSN9 
        ID_PATH: pci-0000:2e:00.0-ata-2.0 
DEV: ata11 
        Temperature: +32.0°C (27.0°C to 36.0°C) 
        DEVNAME: /dev/sdj 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_WWN: 0x50014ee263ce2c81 
        ID_SERIAL_SHORT: WD-WCC7K0RY7R37 
        ID_PATH: pci-0000:2e:00.0-ata-3.0 
DEV: ata12 
        Temperature: +32.0°C (27.0°C to 36.0°C) 
        DEVNAME: /dev/sdk 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_WWN: 0x50014ee263e27e85 
        ID_SERIAL_SHORT: WD-WCC7K4PE4C1U 
        ID_PATH: pci-0000:2e:00.0-ata-4.0 
DEV: ata13 
        Temperature: +31.0°C (26.0°C to 35.0°C) 
        DEVNAME: /dev/sdl 
        ID_MODEL: WDC_WD40EFRX-68N 
        ID_WWN: 0x50014ee265d71fad 
        ID_SERIAL_SHORT: WD-WCC7K0CSZY00 
        ID_PATH: pci-0000:2e:00.0-ata-5.0
[/FONT]
```

Figure someone here may find this useful

as long as the drive shows up in ```
[FONT=monospace][COLOR=#000000]udevadm info --query=all --name=/dev/sd{a..z}[/COLOR][/FONT]
``` it will print it, not sure what happens if you have over 26 drives (a-z) though

---

### Post by deadflowr on 2024-06-11
> not sure what happens if you have over 26 drives (a-z) though
The name scheme cycles up, so after sdz it moves on the sdaa.
And so on.
[https://superuser.com/a/406277](https://superuser.com/a/406277)

---

