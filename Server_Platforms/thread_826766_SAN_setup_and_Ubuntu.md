---
title: "SAN setup and Ubuntu"
date: 2008-06-12
forum: Server Platforms
---

### Post by schizo777 on 2008-06-12
I'm struggling to come right with our SAN setup and Ubuntu servers. 
Hopefully someone will be able to help me.

This is a description of our system at the moment.
Currently we have two fileservers connecting to the SAN, FS1 and FS2 the 
only reason we set up two servers is redundancy.
These servers are running ubuntu 8.04 which detects the Qlogic HBA's and the 
SAN.
I have partitioned a few RAID sets and have set up LUNS on these sets.
We then done a format on the LUNS with linux ext3 filesystem and mounted the 
LUNS on both the FS1 and FS2. So they both have access to the partitions
We then wrote data to the SAN. via FS1, in this case /Jupiter partition. I 
had to restart the FS1 server to test that FS2 would continue to write to 
the same partition. It does but if you have a look at the text below we are 
receiving errors doing a listing on a few of the directories, This is 
possibly the stuff that FS2 had written? After FS1 restarted it was 
complaining about the /Jupiter partition being bad, and I have to manually 
do a file system check.
Could this be a problem with the SAN? or the way in which I have configured 
the two servers?
If so what is the best way to do this?




/Jupiter/981/981771:
total 384K
drwxr-xr-x   2 root root 4.0K 2008-06-11 15:59 .
drwxr-xr-x 234 root root  12K 2008-06-11 20:35 ..
-rw-r--r--   1 root root  15K 2008-06-05 15:16 
05-981771-0548330041-0605H-151547.tif.TIFF
-rw-r--r--   1 root root  24K 2008-06-09 14:02 
10-981771-0218075800-0609G-140115.tif.TIFF
-rw-r--r--   1 root root  31K 2008-06-11 15:39 
11-981771-0548330041-0611A-153831.tif.TIFF
-?????????   ? ?    ?       ?                ? 
16-981771-0548330045-0603I-154040.tif.TIFF
-rw-r--r--   1 root root  18K 2008-06-04 17:35 
32-981771-0114759265-0604H-173454.tif.TIFF
-rw-r--r--   1 root root 199K 2008-06-04 17:26 
32-981771-0533532621-0604J-172141.tif.TIFF
-rw-r--r--   1 root root  36K 2008-06-05 09:20 
34-981771-0538329753-0605F-091941.tif.TIFF
-rw-r--r--   1 root root  18K 2008-06-05 16:12 
39-981771-0114759265-0605A-161128.tif.TIFF
-rw-r--r--   1 root root  15K 2008-06-05 15:29 
39-981771-0532981116-0605F-152909.tif.TIFF
-?????????   ? ?    ?       ?                ? 
46-981771-0532060224-0603E-152451.tif.TIFF
-?????????   ? ?    ?       ?                ? 
55-981771-0532981116-0603H-111010.tif.TIFF
ls: cannot access 
/Jupiter/981/981772/05-981772-0218631149-0603C-091330.tif.TIFF: No such file 
or directory
ls: cannot access 
/Jupiter/981/981772/54-981772-0218631149-0603A-135850.tif.TIFF: No such file 
or directory
ls: cannot access 
/Jupiter/981/981772/13-981772-0218631149-0603C-091110.tif.TIFF: No such file 
or directory

---

### Post by gtdaqua on 2008-06-12
how are you mounting the filesystems? post the output of:

```

cat /etc/fstab

```

---

### Post by schizo777 on 2008-06-13
This is only the root & /Jupiter partition

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=45e322fa-a4ce-43b4-9ecb-27212f3dced7 /               ext3    relatime,errors=remount-ro 0       1

# /dev/sdf
UUID=abda4f49-e6b1-4ada-8370-2d1fbb3ba4aa /Jupiter        ext3    relatime        0       2

---

### Post by schizo777 on 2008-06-13
I am currently thinking of changing this to a cluser filesystem like OCFS2...

---

### Post by promodus on 2008-06-16
> **schizo777 said:**
> I'm struggling to come right with our SAN setup and Ubuntu servers. 
Hopefully someone will be able to help me.

This is a description of our system at the moment.
Currently we have two fileservers connecting to the SAN, FS1 and FS2 the 
only reason we set up two servers is redundancy.
These servers are running ubuntu 8.04 which detects the Qlogic HBA's and the 
SAN.
I have partitioned a few RAID sets and have set up LUNS on these sets.
We then done a format on the LUNS with linux ext3 filesystem and mounted the 
LUNS on both the FS1 and FS2. So they both have access to the partitions
We then wrote data to the SAN. via FS1, in this case /Jupiter partition. I 
had to restart the FS1 server to test that FS2 would continue to write to 
the same partition. It does but if you have a look at the text below we are 
receiving errors doing a listing on a few of the directories, This is 
possibly the stuff that FS2 had written? After FS1 restarted it was 
complaining about the /Jupiter partition being bad, and I have to manually 
do a file system check.
Could this be a problem with the SAN? or the way in which I have configured 
the two servers?
If so what is the best way to do this?




/Jupiter/981/981771:
total 384K
drwxr-xr-x   2 root root 4.0K 2008-06-11 15:59 .
drwxr-xr-x 234 root root  12K 2008-06-11 20:35 ..
-rw-r--r--   1 root root  15K 2008-06-05 15:16 
05-981771-0548330041-0605H-151547.tif.TIFF
-rw-r--r--   1 root root  24K 2008-06-09 14:02 
10-981771-0218075800-0609G-140115.tif.TIFF
-rw-r--r--   1 root root  31K 2008-06-11 15:39 
11-981771-0548330041-0611A-153831.tif.TIFF
-?????????   ? ?    ?       ?                ? 
16-981771-0548330045-0603I-154040.tif.TIFF
-rw-r--r--   1 root root  18K 2008-06-04 17:35 
32-981771-0114759265-0604H-173454.tif.TIFF
-rw-r--r--   1 root root 199K 2008-06-04 17:26 
32-981771-0533532621-0604J-172141.tif.TIFF
-rw-r--r--   1 root root  36K 2008-06-05 09:20 
34-981771-0538329753-0605F-091941.tif.TIFF
-rw-r--r--   1 root root  18K 2008-06-05 16:12 
39-981771-0114759265-0605A-161128.tif.TIFF
-rw-r--r--   1 root root  15K 2008-06-05 15:29 
39-981771-0532981116-0605F-152909.tif.TIFF
-?????????   ? ?    ?       ?                ? 
46-981771-0532060224-0603E-152451.tif.TIFF
-?????????   ? ?    ?       ?                ? 
55-981771-0532981116-0603H-111010.tif.TIFF
ls: cannot access 
/Jupiter/981/981772/05-981772-0218631149-0603C-091330.tif.TIFF: No such file 
or directory
ls: cannot access 
/Jupiter/981/981772/54-981772-0218631149-0603A-135850.tif.TIFF: No such file 
or directory
ls: cannot access 
/Jupiter/981/981772/13-981772-0218631149-0603C-091110.tif.TIFF: No such file 
or directory

Are you connecting both file servers to the same LUN at the same time?

---

### Post by schizo777 on 2008-06-17
Yes, at least thats what I would like it to do.

---

### Post by promodus on 2008-06-17
Having two initiators connect to the same target is akin to having a SATA hard drive, and making the cable connect to two computers...

Corruption will happen.

What are your needs?

Redundancy (Reliability)?
Load Balancing (Performance)? 
both... ?

I am not sure how large your network is, but I'm going to assume this isn't enterprise. My suggestion, if they're both file servers (NAS) just use RSync.

---

### Post by schizo777 on 2008-06-18
The only real reason we have 2 file servers to connect to the SAN is for redundancy, possibly later we would need load balancing depending on growth. 
We have a decent sized network, but this solution is for a specific project. 
Currently what I have done is just mount one FS machine to the SAN and then the other server will be a "Hot Spare" if FS1 goes down. 
For future thou I would like to find out how to make a cluster file system. From what I can see Red Hat GFS looks like the way to go.

---

