---
title: "Question with hardware RAID"
date: 2007-03-07
forum: Server Platforms
---

### Post by pofcorn on 2007-03-07
Hi,

I hope this is the right forum for this.

I have an IBM xSeries 366 with 2 ServeRAID cards.

A Serveraid 8i is installed in its dedicated slot. 2 70 gig SAS drives configured in Raid 1.

A Serveraid 6m installed in a PCIX slot, connected to a EXP400 (external hard drives enclosure). 2 300 gig drives installed in the EXP400 configured in Raid 1.

I configured the cards and arrays using the Serveraid bootable CD. I set the 2 cards in write-back mode.

The 2 cards install and work fine under Ubuntu 6.06.

However, Ubuntu keeps setting them in write-through mode. This is not optimal because both cards have a battery-backed cache, so there is no risk of data loss.

**I would like to know if there is a way to force the aacraid driver to use write-back mode.**

Here is the relevant output from dmesg
```

  160.915444 SCSI subsystem initialized
  160.916690 Adaptec aacraid driver (1.1-4 Feb  1 2007 17:03:23)
  160.916753 GSI 16 sharing vector 0xA9 and IRQ 16
  160.916759 ACPI: PCI Interrupt 0000:01:02.0A -> GSI 25 (level, low) -> IRQ 169
  160.931279 AAC0: kernel 5.2-011835 
  160.931283 AAC0: monitor 5.2-011835
  160.931285 AAC0: bios 5.2-011835
  160.931288 AAC0: serial 163933
  160.931290 AAC0: 64bit support enabled.
  160.931292 AAC0: 64 Bit DAC enabled
  160.931616 scsi0 : ServeRAID
  160.931820   Vendor: IBM       Model: Systeme           Rev: V1.0
  160.931833   Type:   Direct-Access                      ANSI SCSI revision: 02
  160.957862 Driver 'sd' needs updating - please use bus_type methods
  160.957947 SCSI device sda: 143155200 512-byte hdwr sectors (73295 MB)
  160.957960 sda: Write Protect is off
  160.957963 sda: Mode Sense: 03 00 00 00
  160.957985 sda: got wrong page
  160.958408 sda: assuming drive cache: write through
  160.959081 SCSI device sda: 143155200 512-byte hdwr sectors (73295 MB)
  160.959098 sda: Write Protect is off
  160.959100 sda: Mode Sense: 03 00 00 00
  160.959127 sda: got wrong page
  160.959539 sda: assuming drive cache: write through
  160.960106  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
  160.989401 sd 0:0:0:0: Attached scsi removable disk sda
  161.297934 GSI 17 sharing vector 0xB1 and IRQ 17
  161.297942 ACPI: PCI Interrupt 0000:05:08.0A -> GSI 19 (level, low) -> IRQ 177
  161.337077 scsi1 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 6M>
  161.337285   Vendor: IBM       Model: SERVERAID         Rev: 1.00
  161.337300   Type:   Direct-Access                      ANSI SCSI revision: 02
  161.337494 SCSI device sdb: 585936896 512-byte hdwr sectors (300000 MB)
  161.338008 sdb: got wrong page
  161.338428 sdb: assuming drive cache: write through
  161.339204 SCSI device sdb: 585936896 512-byte hdwr sectors (300000 MB)
  161.339715 sdb: got wrong page
  161.340127 sdb: assuming drive cache: write through
  161.340700  sdb: sdb1
  161.357123 sd 1:0:0:0: Attached scsi disk sdb
  161.358673   Vendor: IBM       Model: SERVERAID         Rev: 1.00
  161.358687   Type:   Processor                          ANSI SCSI revision: 02
  161.362684   Vendor: IBM-ESXS  Model: MAW3300NC     FN  Rev: C206
  161.362705   Type:   Direct-Access                      ANSI SCSI revision: 04
  161.363538 SCSI device sdc: 585937500 512-byte hdwr sectors (300000 MB)
  161.365022 SCSI device sdc: drive cache: write through
  161.366086 SCSI device sdc: 585937500 512-byte hdwr sectors (300000 MB)
  161.367554 SCSI device sdc: drive cache: write through
  161.367559  sdc: sdc1
  161.383362 sd 1:1:0:0: Attached scsi disk sdc
  161.386814   Vendor: IBM-ESXS  Model: MAW3300NC     FN  Rev: C206
  161.386828   Type:   Direct-Access                      ANSI SCSI revision: 04
  161.388275 SCSI device sdd: 585937500 512-byte hdwr sectors (300000 MB)
  161.389599 SCSI device sdd: drive cache: write through
  161.390323 SCSI device sdd: 585937500 512-byte hdwr sectors (300000 MB)
  161.391650 SCSI device sdd: drive cache: write through
  161.391657  sdd: sdd1
  161.392986 sd 1:1:1:0: Attached scsi disk sdd
  161.429957   Vendor: IBM       Model: EXP400   S320     Rev: D110
  161.429973   Type:   Processor                          ANSI SCSI revision: 03
```


What's weird is that the system is able to detect the physical drives under the enclosure (sdc and sdd) but I don't think it's a problem, I don't mount them or anything.

Thanks.

---

### Post by pofcorn on 2007-03-15
Bump for great justice.

---

### Post by keldrum on 2007-07-10
I am in  the process of researching an install on a xSeries 360 to run as a VMWare server system. I've already got the system running W2K3 Ent. Server but would prefer to move to Ubuntu.

 I haven't got much to offer as far as your specific issue is concerned except for the following link which has been quite helpful for me so far:

IBM Info Centre for Linux on xSeries
[http://publib.boulder.ibm.com/infocenter/lnxinfo/v1r0/index.jsp?topic=/com.ibm.help.doc/concepts/lcon_xSeries_360.htm](http://publib.boulder.ibm.com/infocenter/lnxinfo/v1r0/index.jsp?topic=/com.ibm.help.doc/concepts/lcon_xSeries_360.htm)

Although the article is dealing with a SuSE install (one of the distros supported by IBM) I think the documentation is good. The potential problems with other distros are likely very similar & have been helpful to me.

I would like to know if you'd be interested in discussing your experience with the install. Let me know if you'd be interested.

---

