---
title: "LSI 1068E based SAS/SATA controller"
date: 2008-09-29
forum: Server Platforms
---

### Post by tiburcillo on 2008-09-29
Hello!

I'm fairly new to linux and so far I've never had any problems when plugging in new hardware. For example, last year I plugged in a Promise IDE Controller and was suprised i didn't even had to install a driver to get it working. Now with a shortage on hard drives I've decided to buy an Intel SASMF8I card which has an LSI 1068E chip inside. My ubuntu (2.6.22-14-generic) doesn't seem to recognize the card, when i do lspci -v i get this output:
```
02:00.0 RAID bus controller: LSI Logic / Symbios Logic Unknown device 0059 (rev 08)
        Subsystem: Intel Corporation Unknown device 3002
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at ee00 [size=256]
        Memory at fd9fc000 (64-bit, non-prefetchable) [size=16K]
        Memory at fd9e0000 (64-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fd600000 [disabled] [size=2M]
        Capabilities: [50] Power Management version 2
        Capabilities: [68] Express Endpoint IRQ 0
        Capabilities: [98] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=1
```

Some searching on the net & this forum says that loading the megaraid_sas driver should get this working. My guess is that by doing "modprobe megaraid_sas" the driver is inserted in the kernel. Now my question is... how do i know this succeeded and how can I see (and mount) the 4 SATA drives that are attached to the controller?

Thanks,
t

---

### Post by fjgaude on 2008-09-29
Well, you should be able to find your driver module in /lib/modules/2.6.<kernel>.

Also after loading, and then rebooting, your drives should show up in Ubuntu's Nautilus file browser... you should be able to mount them as you wish.

I guess the drives are showing now in your BIOS?

---

### Post by alastair on 2008-09-29
Check the logs at boot i.e.

terminal : sudo dmesg 
terminal : less /var/log/syslog

and look for the probe for this card. It might be loaded and the card recognised.

If you have to modprobe a module, so a "tail -f /var/log/syslog" in a different terminal ansd see what happens.

Alastair

---

### Post by alastair on 2008-09-29
Check the logs at boot i.e.

terminal : sudo dmesg 
terminal : less /var/log/syslog

and look for the probe for this card. It might be loaded and the card recognised.

If you have to modprobe a module, so a "tail -f /var/log/syslog" in a different terminal ansd see what happens.

Alastair

---

### Post by tiburcillo on 2008-09-29
Indeed, in the bios I see all four drives (750, 750, 500 and 320 GB).

I'll try rebooting right away, however "tail -f /var/log/syslog" doesnt give a lot of feedback after modprobing...

Sep 29 21:11:53 centurion kernel: [  254.381817] megasas: 00.00.03.10-rc5 Thu May 17 10:09:32 PDT 2007
Sep 29 21:17:01 centurion /USR/SBIN/CRON[6431]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 29 21:28:00 centurion -- MARK --
Sep 29 21:34:08 centurion kernel: [  809.599875] Fusion MPT base driver 3.04.04
Sep 29 21:34:08 centurion kernel: [  809.599878] Copyright (c) 1999-2007 LSI Logic Corporation
Sep 29 21:34:08 centurion kernel: [  809.606452] Fusion MPT SAS Host driver 3.04.04

I've also found this interesting piece of info:
> Hi Folks, 

Any suggestions on this one? 

2.6.18-6-amd64 #1 SMP Sun Feb 10 17:50:19 UTC 2008 x86_64 GNU/Linux 
Running on a Supermicro *H8DM3-2 motherboard (with on-board *LSI SAS1068E Controller) 
lspci reports the controller as: 
02:00.0 SCSI storage controller: LSI Logic / Symbios Logic Unknown device 0059 (rev 04) 
LSI provides a source tar ball (good for them!) and although the driver source apparently compiled successfully, it would not load. 
/var/log/kern.log says: 
mptbase: no version for "struct_module" found: kernel tainted. 
Fusion MPT base driver 4.00.21.00 
Copyright (c) 1999-2007 LSI Corporation 
mptsas: Unknown symbol scsi_is_sas_phy_local 
mptsas: Unknown symbol scsi_is_sas_phy_local 
Fusion MPT SPI Host driver 4.00.21.00 
Fusion MPT misc device (ioctl) driver 4.00.21.00 
mptctl: Registered with Fusion MPT base driver 
mptctl: /dev/mptctl @ (major,minor=10,220) 
mptsas: Unknown symbol scsi_is_sas_phy_local 
mptctl: Deregistered /dev/mptctl @ (major,minor=10,220) 

Any suggestions most appreciated. 

(A side note: The mptsas driver supplied with the etch release loads fine, but, apparently doesn't support the controller: 
modinfo mptsas 
suggests it does not support the model 0059. It lists 0050, 0054, 0056, 0058, & 0062. 
I have limited experience with this kind of thing, so I don't know what the different "names" for the controller signifies--if anything.) 
Thanks! 

John

---

### Post by tiburcillo on 2008-09-29
I got a bit further!

By doing **update-pciids** the card is no more detected as unknown but:
02:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 8208ELP/8208ELP (rev 08)
        Subsystem: Intel Corporation Unknown device 3002
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at ee00 [size=256]
        Memory at fd9fc000 (64-bit, non-prefetchable) [size=16K]
        Memory at fd9e0000 (64-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fd600000 [disabled] [size=2M]
        Capabilities: [50] Power Management version 2
        Capabilities: [68] Express Endpoint IRQ 0
        Capabilities: [98] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=1

Now trying to enable the driver... :)

---

### Post by cariboo on 2008-09-29
If you look at the output of your /var/log/syslog it is indeed loading a driver for your device:

> Sep 29 21:34:08 centurion kernel: [ 809.599875] Fusion MPT base driver 3.04.04
Sep 29 21:34:08 centurion kernel: [ 809.599878] Copyright (c) 1999-2007 LSI Logic Corporation
Sep 29 21:34:08 centurion kernel: [ 809.606452] Fusion MPT SAS Host driver 3.04.04

So you should see something in the output of dmesg concerning the drives. You should see sometning in the output of:

```
sudo fdisk -l
```

Jim

---

### Post by tiburcillo on 2008-09-30
Unfortunately there is no output when the module is loaded. I found a semi-opensource driver but it only compiles against kernels 2.4.19 and before. I have a later version, so no luck i guess. :(

---

### Post by nutznboltz on 2010-07-02
The driver problems with LSI 1068E (A.K.A LSI SAS 3442E-R also LSI 3081E-R) is an ongoing issue that affects also affects Karmic and Lucid.

[https://bugs.launchpad.net/debian/+bug/474207](https://bugs.launchpad.net/debian/+bug/474207)

---

### Post by nutznboltz on 2010-07-02
Related thread:

[http://ubuntuforums.org/showthread.php?t=1315321](http://ubuntuforums.org/showthread.php?t=1315321)

---

### Post by cainwong on 2010-08-08
The 1st post on this topic seems a bit outdated. Anyway, check this out (may help):
[http://ubuntuforums.org/showpost.php?p=9690768&postcount=7](http://ubuntuforums.org/showpost.php?p=9690768&postcount=7)

---

