---
title: "Recommended partition setup"
date: 2011-05-31
forum: Server Platforms
---

### Post by ryanrobinson on 2011-05-31
Hi guys,

I am currently setting up my HP Microserver for personal use. The server will act as a local LAMP server and a NAS. I will be using Ubuntu Server 10.04.2

The server will be using two 500GB hard drives in the fakeRAID configured drive bay (I will be using SoftwareRAID instead) and a 250GB drive separate from the drive bay.

I just need some opinions regarding the partition setup as I've forgot whether Apache stores its files in the /var or /usr directory. Anyway, here is my proposed setup:

Hard drive - SDA (250GB)

/boot - Ex2 - 200MB
/     - Ex4 - 247.8GB
swap  - swap - 2GB

Software RAID1 setup (2x 500GB)

/var  - XFS - 300GB (this will contain website files)
/home - XFS - 200GB (this will have misc files)

Will this be a feasible setup? Also, if my RAID was to fail could I still boot the OS if GRUB was installed on the 250GB drive?

Thanks.

---

### Post by lhypx on 2011-07-02
as same as ryanrobinson, i have question about partitions size for my server.
i have 320GB HD and 2GB RAM, on server i want to running Squid and Samba, how effective partitions and sizes should be made?

for pre-test, i just use auto partitioning method at installation.

---

