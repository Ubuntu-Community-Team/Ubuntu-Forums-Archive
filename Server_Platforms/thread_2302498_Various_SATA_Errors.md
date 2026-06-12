---
title: "Various SATA Errors"
date: 2015-11-10
forum: Server Platforms
---

### Post by d4rk0wl on 2015-11-10
Hello,
I am experiencing multiple SATA errors upon booting, and drive functions are very slow. Here is the errors I am experiencing.  
```
sysadmin@ubuntu:~$ dmesg | tail -n 50
[  131.260061] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  131.263053] ata4.00: BMDMA stat 0x26
[  131.266007] ata4.00: failed command: READ DMA
[  131.268270] ata4.00: cmd c8/00:68:f8:4c:8c/00:00:00:00:00/ec tag 0 dma 53248 in
     res 51/84:38:28:4d:8c/84:01:1c:00:00/ec Emask 0x30 (host bus error)
[  131.272322] ata4.00: status: { DRDY ERR }
[  131.274177] ata4.00: error: { ICRC ABRT }
[  131.275708] ata4: soft resetting link
[  131.452362] ata4.00: configured for UDMA/33
[  131.452383] ata4: EH complete
[  138.192093] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[  138.193691] ata4.00: BMDMA stat 0x26
[  138.195318] ata4.00: failed command: READ DMA
[  138.196928] ata4.00: cmd c8/00:20:58:72:6d/00:00:00:00:00/e4 tag 0 dma 16384 in
     res 51/84:00:77:72:6d/84:01:1c:00:00/e4 Emask 0x30 (host bus error)
```
  I have been doing a lot of reading on these errors and from what I  have been finding, the situation is bad. When I first started receiving  these errors I took the liberty of swapping out the drive to a newer one  and reinstalling the system. 3 drives later, and multiple attempts of  replacing the SATA cable (and using different HDD ports) I am seeing the  same thing. Could this potentially be an issue with power to the hard  drive? Or perhaps a defect on the motherboard? It seems that every previous solution for others that I have discovered in regards to these errors seems to have no effect on my situation.
I am currently running  the latest 32bit version of Ubuntu Server. I should also mention that this is a very old machine. It is an old Pentium 4 computer that has been lying around that I decided to bring back to life.

  Thanks in advance!
d4rk0wl

---

### Post by sandyd on 2015-11-10
Have you checked the voltage of the ports providing SATA power?

---

### Post by d4rk0wl on 2015-11-11
Hello and thanks for the fast reply,
Yes I have confirmed that I have both 3.3v, 5v and 12v at the SATA connection. I have also, on a whim, attempted to use a Molex -> SATA converter for the drive power on a tested good molex plug. It has no effect and I am still receiving the same error.

Thanks!

---

### Post by sandyd on 2015-11-11
From what I gather

a) It isn't a power problem
b) It isn't a drive problem
c) It isn't a sata cable problem

I would say at this time that it is either an issue with Ubuntu, or an issue with the mobo.

---

### Post by tgalati4 on 2015-11-12
Perhaps it is a current problem or a noise problem.  Look for bulging capacitors on the motherboard.  Perhaps clean it with compressed air.  Old hardware can be difficult to get reliability.  Try removing everything and boot to a minimum condition.  If you can boot from a LiveDVD or USB without using the hard disk, then you know that the motherboard is working OK.  If the Live Session does not work reliably, then you have more work to do.

What is the make and model of the computer?

---

