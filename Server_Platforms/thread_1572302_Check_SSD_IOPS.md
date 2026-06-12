---
title: "Check SSD IOPS"
date: 2010-09-10
forum: Server Platforms
---

### Post by Confucius! on 2010-09-10
I am testing out a OCZ SSD that i got not to long ago. So far the benchmarks are off. Got to love SSD marketing :rolleyes:. I was wondering how to check the IOPS of the SSD drive. I was looking at bonnie++ or iozone but i am not sure what is best. Also if you could provide me with the full command so i can just copy and paste that would be great.[-o<

---

### Post by juliobahar on 2010-09-19
Almost same question here... How to test / check my newly installed SSD?

---

### Post by whoopn on 2010-12-16
No one answered so you can try the following, it will give you MB/s for a sequential write (which is what those marketing guys are touting).

In a console:

To write to your disk to find the write speeds
```


dd if=/dev/zero of=/path/to/your/drive/test.txt bs=1M count=4096


```
note: make sure the count value is double the size of your RAM or these tests are going to be a little generous towards the ssd's numbers

To test read speeds:

```


dd if=/path/to/your/drive/test/txt of=/dev/null bs=1M count=4096

```

So run the write test then run the read test on that same file.

Hope that gives you some idea

---

### Post by chmac on 2012-04-14
For anyone finding this in the future, sysbench is a useful tool for benchmarking drives. It's in the ubuntu repos.

---

### Post by d4m1r on 2012-04-14
An easier way to check your disk I/O speed is:

```
dd if=/dev/zero of=test bs=64k count=16k conv=fdatasync && rm -f test
```

^Works on Server + Desktop versions of Ubuntu. However, note it only really tests sequential write speed and there are 3-4 other factors that determine HDD speed so...

---

### Post by darkod on 2012-04-15
On this subject, is there any tool for random R/W, for both HDD and SSD?

I would really like to test random access, not sequential.

---

### Post by chmac on 2012-04-19
Yes, sysbench can test random or sequential reads, writes, or a mixture of both. It's used by the Percona folks to benchmark for mysql performance.
```
sudo apt-get install sysbench
```

Then it can be run something like:
```
sysbench --test=fileio --file-num=64 --file-total-size=$size --init-rng=on --file-extra-flags=direct prepare
sysbench --test=fileio --file-total-size=$size --file-test-mode=$mode --max-time=60 --max-requests=100000000 --num-threads=$threads --init-rng=on --file-num=64 --file-extra-flags=direct --file-fsync-freq=0 --file-block-size=16384 run
```

Note that you'll need to replace $size and $threads with appropriate values and $mode with one of seqwr seqrd rndrd rndwr rndrw. I copied and pasted the above from a script which recursively calls sysbench for file sizes 1G, 4G, 16G and for threads 1, 4, 8. You can find more info [here]("http://www.percona.com/docs/wiki/benchmark:io-alignment:4-disk_raid10").

---

### Post by darkod on 2012-04-19
Cool, thanks a lot. I'll look into it.

---

