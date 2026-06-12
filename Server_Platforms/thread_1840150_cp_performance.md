---
title: "cp performance"
date: 2011-09-07
forum: Server Platforms
---

### Post by sand7000 on 2011-09-07
When I copy a file foo to foo2 I get a transfer rate of X. If I then copy foo to foo3 and simultaneously copy foo2 to foo4 the transfer rates drop to about X/2 for both processes. I have not even come close to maxing out the IOPS from my SAN so I feel it must have something to do with how cp is written. I have tried dd with similar results. I can see in top that I have two cp processes running but is it really two threads or are the two processes sharing some kind of resource back and fourth that slows both down? Is there anything I can do to increase this?

---

### Post by rubylaser on 2011-09-07
Some data, and the actual commands you're trying to use might make this easier to look at. 

**CAUTION: unscientific tests ahead :)**
These tests are on a slow development server, so don't be dismayed by the slow times.

Make a testfile and use that as your starting point.
```
root@svr-cc-marketing:~# dd if=/dev/zero of=testfile bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 36.3284 s, 289 MB/s
```

**Single cp**
```
root@svr-cc-marketing:~# time cp testfile1 testfile2

**real	2m12.426s**
user	0m0.060s
sys	0m23.510s

```

**Double cp** (I'm copying (2) 10 GB files, so it should take twice as long).
```
root@svr-cc-marketing:~# time cp testfile1 testfile3

real	4m20.559s
user	0m0.060s
sys	0m23.980s

root@svr-cc-marketing:~# time cp testfile2 testfile4

real	4m19.906s
user	0m0.070s
sys	0m23.560s
```

That's just about spot on double with the previous cp, but I am moving twice as much data, so cp seems to scale well for me based on simultaneous copies.  The cp commands goes as fast as it's capable of going based on it's code, so as you add more threads, it splits that maximum speed among the threads. So in your case 2 Threads, each gets half of the maximum.

cp isn't the fastest way to transfer, so if you want more speed, you could use cat, dd, or other transfer mechanisms. 

 If you use the cat command, or dd those files instead, it should be faster than the cp command.

**Catting the files**
```

root@svr-cc-marketing:~# time `cat testfile1 > testfile3`

real	3m5.312s
user	0m0.060s
sys	0m23.550s

root@svr-cc-marketing:~# time `cat testfile2 > testfile4`

real	3m9.280s
user	0m0.070s
sys	0m23.200s
```
More than a minute faster than the cp command.

dd
```
root@svr-cc-marketing:~# time `dd if=testfile1 of=testfile3`
20480000+0 records in
20480000+0 records out
10485760000 bytes (10 GB) copied, 197.341 s, 53.1 MB/s

real	3m17.360s
user	0m5.530s
sys	1m34.560s

root@svr-cc-marketing:~# time `dd if=testfile2  of=testfile4`
20480000+0 records in
20480000+0 records out
10485760000 bytes (10 GB) copied, 202.494 s, 51.8 MB/s

real	3m22.496s
user	0m5.960s
sys	1m33.630s
```

---

### Post by sand7000 on 2011-09-07
Thank you for your thoughtful reply. These are exactly the same tests I have been toying with. Can you clarify one point as I think it is the heart of the issue. You say:
> The cp commands goes as fast as it's capable of going based on it's  code, so as you add more threads, it splits that maximum speed among the  threads.but if the SAN can handle more IO and the second cp thread can be handed to another of the many processor cores why is this so? Is there a resource that gets locked and only one cp process can access it? If so then I don't see the multiple threads as having a purpous.

I am using a Compellent SAN which I know doesn't work at its best with single threaded processes so if I could get a true multi-threaded process running (where one thread doesn't interfere with the other) I think I could see a huge boost.

---

