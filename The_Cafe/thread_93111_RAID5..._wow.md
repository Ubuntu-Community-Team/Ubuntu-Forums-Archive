---
title: "RAID5... wow"
date: 2005-11-21
forum: The Cafe
---

### Post by poptones on 2005-11-21
I've had a raid5 for my main data storage for a while now (and it's already paid off as I had a disc fail and replaced it under warranty... boy, it's nice to not lose data!)

Now that I have my system pretty well reconfigured I decided to experiment with a raid5 "userland." When I build a system I put all user level partitions on /usr - /usr/home, /usr/var, /usr/tmp etc. 

Anyway, I decided to see how that compares with a RAID5 version of the same space, so I set up equal sized partitions across the other two discs (that weren't being used for /usr), created a degraded raid5, copied the data over from my active /usr partition and rebooted. Once I was sure it was working ok I just added the old /usr partition into the missing spot on the raid5 and in a few minutes I had a fully functional raid5 for my userland.

I then compared the performance of the (completely software) raid5 to the performance of a single, unencrypted, partition (in this case, root).

```

        Command line used: iozone /oddworld/test
        Output is in Kbytes/sec
        Time Resolution = 0.000003 seconds.
        Processor cache size set to 1024 Kbytes.
        Processor cache line size set to 32 bytes.
        File stride size set to 17 * record size.
                                                            random  random    bkwd  record  stride
              KB  reclen   write rewrite    read    reread    read   write    read rewrite    read   fwrite frewrite   fread  freread
             512       4    6505    6889   516696   530518  535562    6748  473675    6798  464599     6621     6939  490372   506984

        Command line used: iozone /test
        Output is in Kbytes/sec
        Time Resolution = 0.000003 seconds.
        Processor cache size set to 1024 Kbytes.
        Processor cache line size set to 32 bytes.
        File stride size set to 17 * record size.
                                                            random  random    bkwd  record  stride
              KB  reclen   write rewrite    read    reread    read   write    read rewrite    read   fwrite frewrite   fread  freread
             512       4    6354    6926   516643   526740  623560    6446  463772    6703  465858     6616     6928  483455   512979

```

Note the performance is roughly equal in spite of "oddworld" being an encrypted software based RAID5.

---

### Post by Ride Jib on 2005-11-21
That's pretty cool. Could you post up links to the information you used to accomplish this? Or if you did it off your own brain-power, could you share some of that knowledge with us?

Thanks

---

### Post by poptones on 2005-11-21
I suppose I could. I only posted that because there is a widespread misconception that "software raids" are somehow not as good as "hardare raids" (even though they are pretty much the same thing until you get to vey high end controllers) and that encryption slows things down in unacceptable fashion. 

In this case, write performance is significantly faster on a vanilla partition, but read performance is pretty much equal and the benefits (security, reliability) are significant.

---

