---
title: "RAID 5 slow after upgrade from 12.04 to 14.04"
date: 2014-09-19
forum: Server Platforms
---

### Post by ron.leibfreid on 2014-09-19
I have a RAID 5 software array that for several years has been delivering 100-110MB/s writes over Gig-E running 12.04.  

After upgrading to 14.04, I am only seeing about 19-22MB/s.  The array checks out clean with no underlying issues.


I have performed the necessary write_cache_size optimizations along with other RAID optimizations I had previously in 12.04.


For some reason, I am seeing very low write_cache_active figures during sustained writes.  I am also not seeing the expected bump in memory utilization during long writes that the larger cache should bring about.  The networked host that is pasting files to the RAID's samba share is the same as it was previously and has not changed.


Any suggestions for other things I might look into in 14.04 that might be causing this behavior?  Is it likely that the low write cache usage is the problem?

---

### Post by ron.leibfreid on 2014-09-19
I noticed that the driver in 14.04 was older than what I was using in 12.04 for my e1000e.  I had been using 2.5.4 and the 14.04 build uses 2.3.2-k "out of the box".

I updated to the latest which is 3.1.0.2-NAPI, but no improvement...

---

### Post by ron.leibfreid on 2014-09-19
Well, I fixed it.  Back to ~115MB/sec.

Had to add a bunch of performance tweaks to the smb.conf file.  Odd, I don't remember having to do that previously.  Anyway, adjusted the buffers to 131072 (receive should only matter but did both).  Added raw read and raw write as well.

---

### Post by Michael_McKenney on 2014-09-22
Can you share more of what you did.  I have two Ubuntu boxes on Gbps that need performance tweaks.  I would appreciate any advice.

---

### Post by Votlon on 2014-09-24
Yeah please share what you did with us!

---

