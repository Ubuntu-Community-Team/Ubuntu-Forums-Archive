---
title: "HP Smart Array 410p"
date: 2010-03-29
forum: Server Platforms
---

### Post by RRJ on 2010-03-29
Hi,

Got a HP server with HP Smart Array raid controller.
Got 2 HDDs running in raid 0+1 with LVM on, but it seems something is wrong, because the copy speed is very slow.

could you give me some advice to solve that problem?
Here are some data:

/dev/mapper/root-system:
 Timing cached reads:   7196 MB in  2.00 seconds = 3599.98 MB/sec
 Timing buffered disk reads:   80 MB in  3.08 seconds =  26.02 MB/sec

on the same machine the HDD that is not in raid (but it is connected to the raid controller):

/dev/cciss/c0d0p1:
 Timing cached reads:   6866 MB in  2.00 seconds = 3434.76 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.16 MB/sec

Even linux software raid perfoms faster. Any ideas?
the cciss module is loaded.

---

### Post by RRJ on 2010-03-29
and more info
Checking for controllers..
DEBUG: Discarding old event 5/0/0
DEBUG: Discarding old event 5/0/0
DEBUG: Discarding old event 5/2/0
Done
Monitoring list
 [ 0] Controller type 'CCISS Controller' at /dev/cciss/c0d0
Pid is 30987

hdparm -tT /dev/cciss/c0d0

/dev/cciss/c0d0:
 Timing cached reads:   6420 MB in  2.00 seconds = 3211.18 MB/sec
 Timing buffered disk reads:  316 MB in  3.01 seconds = 105.15 MB/sec

/dev/cciss/c0d1:
 Timing cached reads:   6424 MB in  2.00 seconds = 3213.37 MB/sec
 Timing buffered disk reads:   64 MB in  3.15 seconds =  20.32 MB/sec

# hdparm -tT /dev/cciss/c0d1p1

/dev/cciss/c0d1p1:
 Timing cached reads:   6606 MB in  2.00 seconds = 3304.31 MB/sec
 Timing buffered disk reads:   24 MB in  3.04 seconds =   7.90 MB/sec

---

### Post by RRJ on 2010-03-29
i think i understood where the problem is. the 1+0 raid mode requires min on 4 hdds, but it was selected by default and this one is not really tested on linux. so i'll wait until ubuntu 10.04 comes out and reinstall the system. if there is some smart one guy or more expirienced with linux raids person - feel free to give an advice plz.

---

### Post by fang0654 on 2010-03-29
Are you running a hardware RAID?  Or is it a fakeraid?  If I remember correctly, the  Smart Arrays are full hardware RAIDs, which means that to the OS doesn't have much control over the speed.  All of the RAID is handled by the controller card.  I haven't used HPs in a while though, so I am not 100%.  Did you fully initialize the RAID before installing stuff on it?  It may still be building out.

---

### Post by RRJ on 2010-05-19
Temperature Warning Disabled or Not Supported
SMART Health Status: OK

Current Drive Temperature:     <not available>
Read defect list: asked for grown list but didn't get it

Error Counter logging not supported
Device does not support Self Test logging


any ideas?

---

