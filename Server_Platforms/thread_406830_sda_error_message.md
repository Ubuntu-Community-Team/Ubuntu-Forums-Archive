---
title: "sda error message"
date: 2007-04-11
forum: Server Platforms
---

### Post by malave on 2007-04-11
I have been trying to find out the source of this error message that I received on boot.  It does not prevent the system from booting but I am concerned it may cause some other problems I am not aware of yet.

sda: asking for cache data failed
sda: assuming ddrive cache: write through
sda: asking for cache data failed
sda: assuming ddrive cache: write through

Server Specifications:

Dell PowerEdge 2950
PERC 5/i RAID Controller
(4) 73GB 15K SAS Drives in RAID 5 Configuration
Running Ubuntu 6.10 Edgy

I can see the hard drive fine and the system boots normally.

the output of lsmod | grep megaraid
     megaraid_sas     28204     3
     scsi_mod         144392      5     sr_mod,sg,usb_storage,sd_mod,megaraid_sas

The drivers for the megaraid seem to load ok on boot.  Is this message something to be worried about?  How do I fix this issue if it is one?

Any help would be appreciated.  Thank You!

---

### Post by inphektion on 2007-04-11
I had those same messages on my 1950 server with the perc5/i.  Seemed to be common and not anything to have any real concern about.  However just today I updated my perc5/i firmware as there is an "urgent" update on Dells site: SAS RAID: Dell PERC 5/i Integrated, Firmware, Multi Language, Multi System, v.5.1.1-0040, A05.

You can load it via floppy and even if there isn't a floppy in your system an external usb floppy is what I used.  The floppy image for you is here: [http://ftp.us.dell.com/SAS-RAID/BR149666.exe](http://ftp.us.dell.com/SAS-RAID/BR149666.exe)

While you are at it there is also an urgent update for the BIOS for that server: BIOS: Dell Server BIOS, English, PowerEdge 2950, 1.3.7
you can get the floppy image for it here: [http://ftp.us.dell.com/bios/PE2950-010307CBIOS.exe](http://ftp.us.dell.com/bios/PE2950-010307CBIOS.exe)

Anyway after doing both of those I don't get that error message anymore so I think lsi finally updated something in the firmware to get the call for write caching responding correctly so it doesn't assume the wrong mode.  I think in worst case it would have slightly affected write performace to the disk.

---

### Post by malave on 2007-04-11
Thanks for the reply.  It didn't seem to be affecting the performance of the system so I have been ignoring it as much as I could.  I will try that firmware update and let you know if I have the same success.

---

### Post by malave on 2007-04-11
Updated the firmware as we discussed and the error went away.

Thanks again.

---

