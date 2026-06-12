---
title: "Help with Empire Earth 2"
date: 2009-01-02
forum: Wine
---

### Post by 67GTA on 2009-01-02
I had this game running under 8.04 with wine. I can't get it going under 8.10. The game installs, but when I try to start it, it gives an error:

```
Please insert the original disc instead of a backup. See www.securom.com/copy for more details.
```

I've looked at the website, but it only talks about enabling DMA in Windows. This is the original retail CD's. They work fine in Windows too. Any ideas?

---

### Post by 67GTA on 2009-01-02
I reloaded the CD and got a new message:

```
Unable to authenticate original disc within time limit.
```My CD/DVD drive seems to be using MDMA2, which I know nothing about. I assume that is similar to DMA?

```
shawnr@fastback:~$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=TSSTcorp CDDVDW TS-L632N                , FwRev=0503    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 AdvancedPM=no
 Drive conforms to: unknown: 

 * signifies the current active mode
```

---

