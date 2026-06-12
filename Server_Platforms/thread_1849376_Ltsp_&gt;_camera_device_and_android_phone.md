---
title: "Ltsp &gt; camera device and android phone"
date: 2011-09-24
forum: Server Platforms
---

### Post by jackbert on 2011-09-24
Hello
(Sorry for mistakes, I'm not English)

Ubuntu 11.04 64b with ltsp

The thin client works fine with majority of usb stick, scanner  and printer
But not with Canon EOS 350d an android samsung galaxy s

in the console there is only this for dmesg when I pluged the device:
for android phone
```
[ 3681.920370] usb 1-5.1: new high speed USB device using ehci_hcd and address 9
[ 3682.013946] scsi3 : usb-storage 1-5.1:2.0
[ 3683.014277] scsi 3:0:0:0: Direct-Access     SAMSUNG  GT-I9000         0000 PQ: 0 ANSI: 2
[ 3683.014772] scsi 3:0:0:1: Direct-Access     SAMSUNG  GT-I9000 Card    0000 PQ: 0 ANSI: 2
[ 3683.017891] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3683.018125] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 3683.019576] sd 3:0:0:1: Attached scsi generic sg2 type 0
[ 3683.021903] sd 3:0:0:1: [sdc] Attached SCSI removable disk
```
and canon camera
```
[ 3644.876436] usb 1-5.2: new high speed USB device using ehci_hcd and address 8
```

I tested this link [https://wiki.ubuntu.com/DebugLocalDev]("https://wiki.ubuntu.com/DebugLocalDev") but nothing to help me

I tried to put this in the lts;conf but nothing :
```
        LOCALDEV=True
        SCANNER=true
        SCREEN_07=ldm
        SCREEN_02=shell
        MODULE_01 = vfat
        MODULE_02 = sg
        MODULE_03 = sd_mod
        MODULE_04 = usb-uhci
        MODULE_05 = usb-storage SCREEN_02=shell
```

If you any idea or links to propose

Thanks

---

### Post by jackbert on 2012-05-23
Hello, I'm back

so I test again on 12.04 and same things: lot of usb keys works on ltsp thin client but not for android_phone and canon 350D

to use android and canon I need to use a external usb media reader (it's works but it's not very practical)

An Other things:
- When I boot the thinclient before login, with android or canon plug, i can see the mount in nautilus
- I can mount directly the device in the terminal thinclient shell but I can't see it in graphiq session

Is there someone who have test it?
Thanks

---

