---
title: "Unexpected RAID resync"
date: 2011-02-02
forum: Server Platforms
---

### Post by BobMUK on 2011-02-02
I've been running MD RAID on an 8.10 box for years and it's served me well.

I'm setting up a new box on 10.10 as a replacement.  I've created a similar RAID5 array on this box and have noticed that every now and then, for no reason, my array goes into resync.

/var/log/messages shows:
```

Feb  1 21:23:25 monolith kernel: [    3.150601] md/raid:md0: not clean -- starting background reconstruction
Feb  1 21:23:25 monolith kernel: [    3.150675] md/raid:md0: device sda5 operational as raid disk 0
Feb  1 21:23:25 monolith kernel: [    3.150741] md/raid:md0: device sdb5 operational as raid disk 1
Feb  1 21:23:25 monolith kernel: [    3.150806] md/raid:md0: device sdd5 operational as raid disk 3
Feb  1 21:23:25 monolith kernel: [    3.150872] md/raid:md0: device sdc5 operational as raid disk 2
Feb  1 21:23:25 monolith kernel: [    3.151204] md/raid:md0: allocated 4222kB
Feb  1 21:23:25 monolith kernel: [    3.151315] md/raid:md0: raid level 5 active with 4 out of 4 devices, algorithm 2
Feb  1 21:23:25 monolith kernel: [    3.151458] md0: detected capacity change from 0 to 4489887940608
Feb  1 21:23:25 monolith kernel: [    3.151839] md: resync of RAID array md0
Feb  1 21:23:25 monolith kernel: [    3.151903] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Feb  1 21:23:25 monolith kernel: [    3.151968] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Feb  1 21:23:25 monolith kernel: [    3.152061] md: using 128k window, over a total of 1461552064 blocks.
```

...and that's it.  No mention of why.

Anyone seeing anything similar, or any ideas on how to debug this further?

---

