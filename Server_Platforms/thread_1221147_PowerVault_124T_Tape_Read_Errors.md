---
title: "PowerVault 124T Tape Read Errors"
date: 2009-07-23
forum: Server Platforms
---

### Post by Bromius76 on 2009-07-23
I have a PowerVault 124T with Quantum Ultrium 4 drive connected to a LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS controller.

It appears I am getting errors when I try to read data back from the drive.

/var/log/messages contains:
```
Jul 23 10:12:03 arden kernel: [1148963.817238] mptscsih: ioc0: attempting task abort! (sc=ffff8802fc5ce000)
Jul 23 10:12:03 arden kernel: [1148963.817243] st 5:0:0:0: [sg6] CDB: Read(6): 08 01 00 00 01 00
Jul 23 10:12:04 arden kernel: [1148964.313569] mptbase: ioc0: LogInfo(0x31140000): Originator={PL}, Code={IO Executed}, SubCode(0x0000)
Jul 23 10:12:04 arden kernel: [1148964.329823] mptscsih: ioc0: task abort: SUCCESS (sc=ffff8802fc5ce000)
```

I'm trying to use Yosemite Server Backup, it's logs contain:
```
07/23/2009 10:12:04 AM Sgd: I/O Control Failed to /dev/sg6 5-0-0-0 (Error 4024: IO failure)
07/23/2009 10:12:04 AM Sgd: Cmd: 08h Scsi Status: 00h Host status: 08h, Masked status: 00h, Driver status: 00h
07/23/2009 10:12:04 AM Scs: Recovered with retry cdb: 08 count: 1
07/23/2009 10:32:12 AM Sgd: I/O Control Failed to /dev/sg6 5-0-0-0 (Error 4024: IO failure)
07/23/2009 10:32:12 AM Sgd: Cmd: 08h Scsi Status: 00h Host status: 08h, Masked status: 00h, Driver status: 00h
07/23/2009 10:32:12 AM Scs: Recovered with retry cdb: 08 count: 1
07/23/2009 10:32:43 AM Lf7: Failed to read a valid header at ltf position 270453 got 01000000
```

I'm somewhat at a loss as to what to try next.  Any feedback or suggestions would be appreciated.

Thanks!

---

### Post by apel_2804 on 2009-07-23
If I'm not mistaken, it is an atutoloader, does this error only appear with a specific tape or did jou get error with all tapes?

---

### Post by Vegan on 2009-07-23
I abandoned tape so long ago. Lets see, position error usually means a tape is missing or needs to be mounted.

If the tapes are written with the same hardware as you are reading. Then there is some problem with the transport control logic. If you put the tapes back into the machine, they need to be in the same order as they were when recorded.

I use commodity RAID boxes for storage and point backups to it. Bigger than a tape rack, and safer with RAID6. Tape is worse than last year in my shop.

---

### Post by Bromius76 on 2009-07-24
It is an auto-loader, but it's not when talking to the changer that we have issues.  It's when we're reading data from the tape.  Any tape, we've tried different ones.  And we're trying to read back with the same drive that we wrote the data with.

We looked at online and RAID based backups, online was too expensive.  And RAID backups didn't give us enough snapshots in history and/or offsite backups.  So for us, it's not a good fit.  And at this point that decision has been made.  So debating the pros/cons of the backup scheme won't help me at this point. :(  I just need to get this drive working.

---

### Post by lithorus on 2009-07-30
We have begun to get the same kind of errors, with NovaNET (Yosemite re-branded). Now the whole thing is marked as offline.

Did you get any further with this?

Edit:
A long story short. I replaced the cable and things seems to work alot better.(atleast for now)

---

