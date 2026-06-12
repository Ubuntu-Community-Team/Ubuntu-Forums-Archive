---
title: "[SOLVED] Why is cat /dev/urandom &amp;amp;amp;gt; /dev/sda faster then dd?"
date: 2008-12-14
forum: Security
---

### Post by ItsJweed on 2008-12-14
I'm in the process of erasing all of the data on my hard drive after which I am going to be reinstalling Ubuntu on a LVM encrypted volume. In the process, I'm overwriting the entire hard drive with pseudo-random data several times to ensure that nothing is recoverable from before. 

I noticed that using

```
cat /dev/urandom > /dev/sda
```

is much faster then 

```
dd if=/dev/urandom of=/dev/sda
```

I even wrote a small script to test this on a 1 GB partition, the output of which is shown below.

```
Starting cat erase at Sun Dec 14 15:15:07 NST 2008
cat: write error: No space left on device
Finished at Sun Dec 14 15:18:34 NST 2008

Starting dd erase at Sun Dec 14 15:18:34 NST 2008
dd: writing to `/dev/sda1': No space left on device
2104453+0 records in
2104452+0 records out
1077479424 bytes (1.1 GB) copied, 538.686 s, 2.0 MB/s
Finished at Sun Dec 14 15:27:33 NST 2008

```

It's easy to see that using cat is ~ 3x faster. What is the deal with that? I though the bottleneck here was /dev/urandom. Does using cat to do this introduce other bits that aren't random?

---

### Post by lswb on 2008-12-14
dd has some options to use different record or block sizes when copying. Most likely cat uses a default size much larger than dd. If you check the man page for dd and specify a very large block size, (something in the megabytes range) it will probably equal or surpass cat in speed.

---

### Post by ItsJweed on 2008-12-14
> **lswb said:**
> dd has some options to use different record or block sizes when copying. Most likely cat uses a default size much larger than dd. If you check the man page for dd and specify a very large block size, (something in the megabytes range) it will probably equal or surpass cat in speed.

Thanks. I've googled some and don't fully understand what block size means in this context. Does using a larger block size have any effect on the ultimate "randomness" of the disk?

---

### Post by lswb on 2008-12-14
It won't affect the results, the degree of randomness will be dependant on urandom. dd uses a default block size of 512 bytes. What this means in your example is that it gets 512 bytes of data from urandom, writes them to disk, then repeats. With a larger block size fewer disk seeks and accesses will be necessary to write the same amount of data.

---

### Post by ItsJweed on 2008-12-14
> **lswb said:**
> It won't affect the results, the degree of randomness will be dependant on urandom. dd uses a default block size of 512 bytes. What this means in your example is that it gets 512 bytes of data from urandom, writes them to disk, then repeats. With a larger block size fewer disk seeks and accesses will be necessary to write the same amount of data.

Excellent. Thank you.

Actually; on a side note, do you know of any way I could use both my cores to speed up the generation of random numbers? Right now it is only using one. It seems like that would double the speed of generating the numbers.

Would it be detrimental to my HD to have two instances of DD running, each with ~100MB block sizes and have one set to only write to the first half of my HD and the other one on the second half?

---

### Post by caljohnsmith on 2008-12-14
How about doing something like:
```
sudo dd if=/dev/urandom of=/dev/sda bs=10M conv=notrunc
```
I'm guessing that would go quite a bit faster than your original command. Also, you might want to try:
```
sudo apt-get install dcfldd
sudo dcfldd if=/dev/urandom of=/dev/sda statusinterval=10 bs=10M conv=notrunc
```
I would use "dcfldd" which is basically dd with more features, and one of the best features is it tells you its progress, based on how you set the "statusinterval" above. Using a statusinterval of 10 above means that dcfldd will report to you when it completes every 10MB X 10 = 100 MB. How about giving that a shot and let me know how it goes. :)

---

### Post by ItsJweed on 2008-12-14
> I would use "dcfldd" which is basically dd with more features, and one of the best features is it tells you its progress, based on how you set the "statusinterval" above. Using a statusinterval of 10 above means that dcfldd will report to you when it completes every 10MB X 10 = 100 MB. How about giving that a shot and let me know how it goes. :)

That is great! I was very frustrated by DD's lack of any type of progress notification. It is certainly going much faster, albeit wiping an entire hard drive is still a slow process. Thanks a bunch.

---

### Post by lswb on 2008-12-14
> **ItsJweed said:**
> Excellent. Thank you.

Actually; on a side note, do you know of any way I could use both my cores to speed up the generation of random numbers? Right now it is only using one. It seems like that would double the speed of generating the numbers.

Would it be detrimental to my HD to have two instances of DD running, each with ~100MB block sizes and have one set to only write to the first half of my HD and the other one on the second half?

I don't know how to do that but I'm pretty sure that the bottleneck will be the disk writes and that a single processor can easily generate random numbers much faster than they can be written to disk.

Trying to write to 2 different parts of the same disk IMHO will cause a lot of disk head movement that isn't necessary with a single sequential write. 

Now if you were writing to 2 or more different physical disks simultaneously, it might be work pursuing, but even in that case, the same data could be used for all the disks. I would think that the processor would really not be all that busy while the disk writing is going on. You could check it with top while the copy is in progress.

---

### Post by ItsJweed on 2008-12-14
> **lswb said:**
> I don't know how to do that but I'm pretty sure that the bottleneck will be the disk writes and that a single processor can easily generate random numbers much faster than they can be written to disk.

Right now I'm using dcfldd like caljohnsmith recommended and the HD access indicator light on my computer flashes briefly every few seconds yet the processor load stays at a steady 50%. (Fully utilizing one core.) In addition, when writing zeros to the drive I get write speeds of ~18 Mb per second whereas it goes much slower when writing random data. That leaves me to believe that the bottleneck lies within /dev/urandom unless there is something else at play here that I am neglecting.

---

### Post by Vantrax on 2008-12-17
> **ItsJweed said:**
> Right now I'm using dcfldd like caljohnsmith recommended and the HD access indicator light on my computer flashes briefly every few seconds yet the processor load stays at a steady 50%. (Fully utilizing one core.) In addition, when writing zeros to the drive I get write speeds of ~18 Mb per second whereas it goes much slower when writing random data. That leaves me to believe that the bottleneck lies within /dev/urandom unless there is something else at play here that I am neglecting.

Could be due to the complexity of the random number generator and how many times it is being run for each block. Usually in doing this the delay is in the randomization of data not the writing.

---

