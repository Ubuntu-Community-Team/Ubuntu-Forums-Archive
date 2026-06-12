---
title: "Unable to use Tape Library and/or SCSI card"
date: 2008-12-30
forum: Server Platforms
---

### Post by Seq on 2008-12-30
I acquired a [SpectraLogic 2k tape library]("http://www.spectralogic.com/index.cfm?fuseaction=products.displayContent&catID=78&p=9") (Not exactly as described -- it seems they keep the same look and model number, though change the hardware over time), and have purchased an adaptec 29160 ("Adaptec AIC-7892A U160/m (rev 02)" according to lspci) card and appropriate cable to connect. This is my first foray into SCSI and I have been having sigificant difficulty.

Unfortunately, as I am not familiar with SCSI, I am not sure how to narrow down the issue to driver, library, or card (Though the Library has previously worked when it was installed at work). 

Also unfortunately, I am not sure what to even report, so if there are any SCSI gurus around who could help me diagnose my problems (SCSI "Sense" codes seem to be useful, but I have no idea how to acquire them)

So far, I have set the card (via the card's BIOS) to disable Domain Validation (The machine would not get past the SCSI BIOS with this enabled).

I have also set "Wide SCSI Negotiation" to false for all SCSI IDs as the tape drive is not a wide device, but the aic79xxx driver was attempting to use it as such and throwing parity errors.

I have blacklisted the ch and osst drivers as they were throwing warnings about using depreciated APIs, and it seems everything just uses the sg drivers anyway. I have also created /dev/changer as a symlink to /dev/sg2, which is the tape changer (I did this to avoid having to specify -f /dev/sg2 on the mtx commands).

Below is the output of (what I think are) relavant commands:

**cat /proc/scsi/scsi** (The first two as they are my SATA disk and optical drive)
```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKS-2 Rev: 12.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVD-ROM GDR8163B Rev: 0L23
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi7 Channel: 00 Id: 02 Lun: 00
  Vendor: SPECTRA  Model: 215              Rev: 2202
  Type:   Medium Changer                   ANSI  SCSI revision: 02
Host: scsi7 Channel: 00 Id: 03 Lun: 00
  Vendor: SONY     Model: SDX-500C         Rev: 02b3
  Type:   Sequential-Access                ANSI  SCSI revision: 02
Host: scsi7 Channel: 00 Id: 04 Lun: 00
  Vendor: SONY     Model: SDX-500C         Rev: 02b3
  Type:   Sequential-Access                ANSI  SCSI revision: 02

```

**mtx inquiry** This seems to be all I can actually do with the changer.
```
Product Type: Medium Changer
Vendor ID: 'SPECTRA '
Product ID: '215             '
Revision: '2202'
Attached Changer API: No

```

**mtx status** (Note that this hangs for several minutes before outputting the illegal Element Type Code)
```
mtx: Request Sense: Long Report=yes
mtx: Request Sense: Valid Residual=yes
mtx: Request Sense: Error Code=70 (Current)
mtx: Request Sense: Sense Key=Unit Attention
mtx: Request Sense: FileMark=no
mtx: Request Sense: EOM=no
mtx: Request Sense: ILI=no
mtx: Request Sense: Residual = 00 00 00 00
mtx: Request Sense: Additional Sense Code = **29**
mtx: Request Sense: Additional Sense Qualifier = **00**
mtx: Request Sense: BPV=no
mtx: Request Sense: Error in CDB=no
mtx: Request Sense: SKSV=no
Mode sense (0x1A) for Page 0x1D failed
illegal Element Type Code 83 reported

```
(Note: I looked up the [Additional Sense Code/Qualifiers]("http://www.spectralogic.com/index.cfm?fuseaction=support.senseCodeResult&CatID=311&senseKey=&senseCode=29&senseQualifier=00&SUBMIT=Submit#self#"))

bottom part of **dmesg** (After the illegal Element Type Code gets printed)
```
[ 3624.450022] scsi 7:0:2:0: Attempting to queue an ABORT message
[ 3624.450029] CDB: 0xb8 0x12 0x0 0x0 0x0 0x40 0x0 0x0 0x16 0x1c 0x0 0x0
[ 3624.450056] scsi7: At time of recovery, card was not paused
[ 3624.450067] >>>>>>>>>>>>>>>>>> Dump Card State Begins <<<<<<<<<<<<<<<<<
[ 3624.450068] scsi7: Dumping Card State while idle, at SEQADDR 0x8
[ 3624.450070] Card was paused
[ 3624.450078] ACCUM = 0x4, SINDEX = 0x20, DINDEX = 0x23, ARG_2 = 0x0
[ 3624.450083] HCNT = 0x0 SCBPTR = 0x0
[ 3624.450086] SCSIPHASE[0x0] SCSISIGI[0x0] ERROR[0x0] 
[ 3624.450095] SCSIBUSL[0x0] LASTPHASE[0x1]:(P_BUSFREE) 
[ 3624.450102] SCSISEQ[0x12]:(ENAUTOATNP|ENRSELI) 
[ 3624.450106] SBLKCTL[0xa]:(SELWIDE|SELBUSB) SCSIRATE[0x0] 
[ 3624.450113] SEQCTL[0x10]:(FASTMODE) SEQ_FLAGS[0xc0]:(NO_CDB_SENT|NOT_IDENTIFIED) 
[ 3624.450121] SSTAT0[0x0] SSTAT1[0x8]:(BUSFREE) 
[ 3624.450128] SSTAT2[0x0] SSTAT3[0x0] SIMODE0[0x8]:(ENSWRAP) 
[ 3624.450137] SIMODE1[0xa4]:(ENSCSIPERR|ENSCSIRST|ENSELTIMO) 
[ 3624.450142] SXFRCTL0[0x80]:(DFON) DFCNTRL[0x0] 
[ 3624.450149] DFSTATUS[0x89]:(FIFOEMP|HDONE|PRELOAD_AVAIL) 
[ 3624.450152] STACK: 0x0 0x164 0x179 0x3
[ 3624.450167] SCB count = 4
[ 3624.450168] Kernel NEXTQSCB = 2
[ 3624.450171] Card NEXTQSCB = 2
[ 3624.450172] QINFIFO entries: 
[ 3624.450176] Waiting Queue entries: 
[ 3624.450179] Disconnected Queue entries: 0:3 
[ 3624.450187] QOUTFIFO entries: 
[ 3624.450188] Sequencer Free SCB List: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 
[ 3624.450282] Sequencer SCB Info: 
[ 3624.450285]   0 SCB_CONTROL[0x44]:(DISCONNECTED|DISCENB) 
[ 3624.450292] SCB_SCSIID[0x20] SCB_LUN[0x0] SCB_TAG[0x3] 
[ 3624.450300]   1 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450309] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450315]   2 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450324] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450329]   3 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450338] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450344]   4 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450353] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450358]   5 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450367] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450373]   6 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450382] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450387]   7 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450396] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450402]   8 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450411] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450416]   9 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450425] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450431]  10 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450440] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450445]  11 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450454] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450460]  12 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450469] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450475]  13 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450484] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450489]  14 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450498] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450504]  15 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450513] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450519]  16 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450527] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450533]  17 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450542] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450547]  18 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450556] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450562]  19 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450571] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450576]  20 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450585] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450591]  21 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450600] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450605]  22 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450614] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450620]  23 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450629] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450634]  24 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450643] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450649]  25 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450658] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450663]  26 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450672] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450678]  27 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450687] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450692]  28 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450701] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450707]  29 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450716] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450721]  30 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450730] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450736]  31 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[ 3624.450745] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[ 3624.450750] Pending list: 
[ 3624.450751]   3 SCB_CONTROL[0x40]:(DISCENB) SCB_SCSIID[0x20] 
[ 3624.450755] SCB_LUN[0x0] 
[ 3624.450756] Kernel Free SCB list: 1 0 
[ 3624.450758] Untagged Q(2): 3 
[ 3624.450760] 
[ 3624.450761] <<<<<<<<<<<<<<<<< Dump Card State Ends >>>>>>>>>>>>>>>>>>
[ 3624.450814] (scsi7:A:2:0): Device is disconnected, re-queuing SCB
[ 3624.450818] Recovery code sleeping
[ 3624.706435] Recovery SCB completes
[ 3624.706688] Recovery code awake
[ 3624.706693] aic7xxx_abort returns 0x2002
[ 3624.962473] scsi 7:0:2:0: Attempting to queue a TARGET RESET message
[ 3624.962478] CDB: 0xb8 0x12 0x0 0x0 0x0 0x40 0x0 0x0 0x16 0x1c 0x0 0x0
[ 3624.962484] scsi 7:0:2:0: Command not found
[ 3624.962486] aic7xxx_dev_reset returns 0x2002

```

I'm all ears. Does anybody know what else I should look for?

---

### Post by Vegan on 2008-12-30
What is attached to your SCSI adapter, also what is the SCSI ID that your tape is set to. Your adapter is rather old and should be detected OK but tape drive might not be working properly with that model.

This is one of the reasons for Serial Attached SCSI and Serial ATA where there are NO configurations to mess up.

Might be better to use the LAN and iSCSI where the SCSI card is not needed at all.

Look up iSCSI to get more background.

:guitar:

---

### Post by Seq on 2008-12-31
> **Vegan said:**
> What is attached to your SCSI adapter, also what is the SCSI ID that your tape is set to. Your adapter is rather old and should be detected OK but tape drive might not be working properly with that model.

What do you mean? The unit has two HD68 ports, one has a terminator, the other connects to the adaptec card (which has one VHD68 port)

There are four ID adapters. "Library" is 2, "Drive 1" is 3, and "Drive 2" is 4. There is also a "Config" that apparently is used to set some kind of emulation. I have left it at 0.

> **Vegan said:**
> This is one of the reasons for Serial Attached SCSI and Serial ATA where there are NO configurations to mess up.

Might be better to use the LAN and iSCSI where the SCSI card is not needed at all.

Look up iSCSI to get more background.

Those are all good technologies, but this unit is not iSCSI capable, just plain old SCSI. I'm sure there are devices about that will act as a gateway (Wikipedia says so!), but if it really is an issue with the adaptec card or aic7xxx driver, I'd rather just get a different card (now that I know I don't need a 160, I can get a cheaper one next time).

---

### Post by windependence on 2008-12-31
Indeed iSCSI isn't even relevant here. Do you have your SCSI chain terminated?

-Tim

---

### Post by Seq on 2008-12-31
> **windependence said:**
> Indeed iSCSI isn't even relevant here. Do you have your SCSI chain terminated?

Yes. The library unit itself has two HD68 ports. One connects to the Adaptec card, the other is terminated. 

Some documentation I've been reading has said the following:
> Termination can be active or passive on a single-ended SCSI bus, but must be the same at both ends.

What does this mean? There is only one end, where I've put the terminator..

Also, I found the [SpectraLogic 2k User Guide]("http://www.spectralogic.com/index.cfm?fuseaction=home.displayFile&DocID=49") online. Page 28 has a chart describing the emulation/config settings. As I indicated in the original post, I have it set to 0 (that's how it came).

---

### Post by Seq on 2008-12-31
> **Seq said:**
> What does this mean? There is only one end, where I've put the terminator..

I guess the SCSI card has a termination setting on it. Why would one disable this? Anyway, I changed it from "Automatic" to "Enabled", just to be sure...

---

### Post by windependence on 2008-12-31
I have never had to mess with that, just made sure it was terminated. You learn something new every day. :)

-Tim

---

### Post by Seq on 2009-01-10
So it turns out that it was an issue with aic7xxx. I acquired an LSI scsi card and it is actually returning useful information
```
# mtx status
  Storage Changer /dev/changer:2 Drives, 30 Slots ( 0 Import/Export )
Data Transfer Element 0:Empty
Data Transfer Element 1:Empty
      Storage Element 1:Empty
      Storage Element 2:Empty
      Storage Element 3:Empty
      Storage Element 4:Empty
      Storage Element 5:Empty
      Storage Element 6:Empty
      Storage Element 7:Empty
      Storage Element 8:Empty
      Storage Element 9:Empty
      Storage Element 10:Empty
      Storage Element 11:Empty
      Storage Element 12:Empty
      Storage Element 13:Empty
      Storage Element 14:Empty
      Storage Element 15:Empty
      Storage Element 16:Empty
      Storage Element 17:Empty
      Storage Element 18:Empty
      Storage Element 19:Empty
      Storage Element 20:Empty
      Storage Element 21:Empty
      Storage Element 22:Empty
      Storage Element 23:Empty
      Storage Element 24:Empty
      Storage Element 25:Empty
      Storage Element 26:Empty
      Storage Element 27:Empty
      Storage Element 28:Empty
      Storage Element 29:Empty
      Storage Element 30:Empty

```

---

