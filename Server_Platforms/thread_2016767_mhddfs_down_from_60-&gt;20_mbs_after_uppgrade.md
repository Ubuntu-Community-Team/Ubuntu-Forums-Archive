---
title: "mhddfs down from 60-&gt;20 mb/s after uppgrade"
date: 2012-07-04
forum: Server Platforms
---

### Post by simon82 on 2012-07-04
I used ubuntu server 10.04 LTS and did an fresh install of ubuntu server 12.04 LTS a while ago, now when i write large files to the mhddfs pool i only get speeds at around 20mb/s. When using ubuntu 10.04 it was around 50-60 mb/s. 

How can this come? is it something in the kernel or? i find it verry anoying. mhddfs+snapraid that was so simple and meet all my criteras is not doing that anymore.

anybody has any knowledge of this problem?

oh forgot to mention, its over samba. if i write to another share (outside the pool) i get the correct speed.

---

### Post by rubylaser on 2012-07-04
Is it slow over NFS as well? Also, how fast is a write on the local machine to the share?

```
dd if=/dev/zero of=/mhddfs/path/testfile.out bs=1M count=10000
```

---

### Post by simon82 on 2012-07-04
To mhddfs pool
10485760000 bytes (10 GB) copied, 358.965 s, 29.2 MB/s

To regular disk
10485760000 bytes (10 GB) copied, 87.8204 s, 119 MB/s

Edit: now tried with an NFS Client to mhddfs pool

10485760000 bytes (10 GB) copied, 277,048 s, 37,8 MB/s

NFS to regular disk

10485760000 bytes (10 GB) copied, 111,169 s, 94,3 MB/s

---

### Post by rubylaser on 2012-07-04
So that rules out Samba as the culprit, because it's slow even on the local machine.  I'll have to try this out tomorrow and see if I see a similar drop in performance between 10.04 -> 12.04.  I've never been able to get much over 40 MB/s with mhddfs before even with good hardware and a 6 disks, so 60 MB/s is rather impressive.

---

### Post by simon82 on 2012-07-05
> **rubylaser said:**
> So that rules out Samba as the culprit, because it's slow even on the local machine.  I'll have to try this out tomorrow and see if I see a similar drop in performance between 10.04 -> 12.04.  I've never been able to get much over 40 MB/s with mhddfs before even with good hardware and a 6 disks, so 60 MB/s is rather impressive.


Found one problem atleast, seems like my CPU autocloking feature aint working no more. 


dd if=/dev/zero of=/storage/pool/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 118.676 s, _**88.4 MB/s**_

now is only problem to get AMD Cool & Quite feature to work as it should in Ubuntu 12.04 then im golden

---

### Post by rubylaser on 2012-07-05
That's great! Now, it's even faster than before :)  [This page]("http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html") covers enabling Cool & Quiet on most of the AMD Socket sets.

---

### Post by simon82 on 2012-07-05
> **rubylaser said:**
> That's great! Now, it's even faster than before :)  [This page]("http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html") covers enabling Cool & Quiet on most of the AMD Socket sets.

Already found the page with googles help but thx anyways. Its nice to have solved the problem =)

---

### Post by zac_haryy on 2012-09-18
> **simon82 said:**
> Found one problem atleast, seems like my CPU autocloking feature aint working no more. 


dd if=/dev/zero of=/storage/pool/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 118.676 s, _**88.4 MB/s**_

now is only problem to get AMD Cool & Quite feature to work as it should in Ubuntu 12.04 then im golden

I to am having write issue with mhddfs here are my speeds:

to mhddfs mount point
```
dd if=/dev/zero of=/mnt/mhddfs/testfile.out bs=1M count=3000
3000+0 records in
3000+0 records out
3145728000 bytes (3.1 GB) copied, 190.202 s, 16.5 MB/s

```

old sata 160gb spare hdd
```
dd if=/dev/zero of=/mnt/t1/testfile.out bs=1M count=3000
dd: writing `/mnt/t1/testfile.out': No space left on device
2236+0 records in
2235+0 records out
2344464384 bytes (2.3 GB) copied, 39.7634 s, 59.0 MB/s

```

SSD with OS
```
 dd if=/dev/zero of=/home/haryy/testfile.out bs=1M count=3000
3000+0 records in
3000+0 records out
3145728000 bytes (3.1 GB) copied, 3.69659 s, 851 MB/s

```


How exaclty did you get the fasters speeds? I am looking for an alternative due to this speed issue. Mhddfs seems to do what I want compared to AUFS though. I was going to go with AUFS but when right a file to the mounted share it wouldnt span accross the pool, it would look at the first hdd size and thats all it would let me write too. So thought I'd try Mhddfs but did read about major performance loss and now experiencing the same issue. Is there anything I can do to fix this?

-haryy

---

