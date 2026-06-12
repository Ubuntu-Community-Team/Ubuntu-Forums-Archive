---
title: "Really slow Raid!"
date: 2011-01-05
forum: Server Platforms
---

### Post by Gervais_5H3T on 2011-01-05
Hey people
 
 I have recently migrated my file server over to  a HP Microserver. The  server has two 1TB disks, in a software RAID-1 array, using MDADM. When I  migrated simply moved the mirrored disks over, from the old server  Ubuntu 9.10 (server) to the new one 10.04.1 (server).

 I Have recently noticed that write speed to the RAID array is *VERY*  slow.  In the order of 1-2MB/s order of magnitude (more info below). Now  obviously this is not optimal performance to say the least. I have  checked a few things, CPU utilisation is not abnormal (<5%) nor is  memory / swap. When I took a disk out and rebuilt the array, with only  one disk (tried both) performance was as to be expected (write speed  >~70MB/s)  The read speed seems to be unaffected however!


   Creating a file on the single (non-raid) disk, is fine:
```
root@BigBertha:/# dd if=/dev/zero of=ddfile.big bs=1MB count=1k 
1024+0 records in  
1024+0 records out  
1024000000 bytes (1.0 GB) copied, 14.9 s, 68.7 MB/s  
 
```   However, copying the 1GB file to the array (mounted on /storage/big/) takes ~25mins, (~ 0.6MB/s) which is not normal
```
root@BigBertha:/# time cp ddfile.big /storage/big/  
 real    25m51.021s  
 user    0m0.128s  
 sys    0m10.957s  
 
```Creating the file on the array (from the kernel /dev/zero, no other storage involved), is again very slow:
```
root@BigBertha:/storage/big# dd if=/dev/zero of=ddfile.big bs=1MB count=1k 
1024+0 records in 
1024+0 records out 
1024000000 bytes (1.0 GB) copied, 71.4943 s, 14.3 MB/s 
```Reading from the array however, everything runs fine!:
```
root@BigBertha:/storage/big# dd if=ddfile.big of=/dev/null 
2000000+0 records in 
2000000+0 records out 
1024000000 bytes (1.0 GB) copied, 12.4544 s, 82.2 MB/s
```As is copying from the array to the single disk
```
root@BigBertha:/storage/big# time cp ddfile.big ~ 
real    0m13.547s 
user    0m0.040s 
sys    0m4.156s 
```Also here is  the output of 'cat /proc/mdstat'
```
root@BigBertha:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[0] sdb1[1] 
      976759936 blocks [2/2] [UU] 
      
unused devices: <none>
```As mentioned above when I remove a  disk, and then mount a single drive from the array performance is  normal, with either disk, whilst I understand that write speeds to  RAID-1 mirrors might not be blazing, I am certain that something is  amiss here! 

I'm tempted to think that there is something funny going on with the  storage subsystem, as copying from the single disk to the array is  slower than creating a file from /dev/zero to the array using DD..

Either way I can't try the array in another computer right now, so I  though I was ask to see if people have seen anything like this!

At the moment I'm not sure if it is something strange to do with having  simply chucked the mirrored array into the new server, perhaps a  different version of MDADM? I'm wondering if it's worth backing up and  starting from scratch! Anyhow this has really got me scratching my head,  and its a bit of a pain! Any help here would be awesome, e-cookies at  the ready! Cheers

---

### Post by Gervais_5H3T on 2011-01-05
Hmm I think this post might be better off in the Hardware area?

Nobody seen a problem like this with a server?

---

### Post by psusi on 2011-01-05
So you have a total of 3 disks, and you copied the file from the stand alone disk to the raid array?  Was it in the process of resyncing at the time?  Are these IDE disks or sata?  If IDE, are they are on the same ribbon?

---

### Post by Gervais_5H3T on 2011-01-06
> **psusi said:**
> So you have a total of 3 disks, and you copied the file from the stand alone disk to the raid array?  Was it in the process of resyncing at the time?  Are these IDE disks or sata?  If IDE, are they are on the same ribbon?

yes there arethree disks, all SATA. on with the OS (boot/root) and the other two in a RAID1 array (mounted on /storage/big/ as above)
whenever anything needs to write too the array it is very slow! The disks are not synchronizing at the time.

---

