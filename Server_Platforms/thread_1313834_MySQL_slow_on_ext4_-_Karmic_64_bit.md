---
title: "MySQL slow on ext4 - Karmic 64 bit?"
date: 2009-11-04
forum: Server Platforms
---

### Post by alexlzl on 2009-11-04
Installed 9.10 Karmic 64 bit and updated to latest packages. I used ext4 for / partition, and kept ext3 for /home partition. Installed MySQL 5.1.37 through apt. 

Struggled couple hours finding that MySQL performance was horrible when datadir is poiting to default /var/lib/mysql (ext4). Simple script which INSERT 20K rows took more than an hour (io wait was around 20%, CPU 15%). Don't see any error logs or issues, the thing is just slow.

Finally moved the datadir to /home ext3 partition, everything flies (script finished in just couple second).

Does anybody else has similar experience? The ext4 root partition otherwise works pretty well, I did "dd" testing and the io throughput is quite normal.

---

### Post by Millage on 2009-11-04
I rebuilt a LAMP server I was testing on from 9.04 to 9.10.  I can confirm that inserting the dump file took a lot longer than it did under ext3.  Could this be a performance issue?  I believe so.

---

### Post by toonn on 2009-11-16
I also installed 9.10 Karmic 64 bit (ext4) and experience the same slowness in mysql.  I don't have a ext3 partition to test the workaround.

---

### Post by toonn on 2009-11-18
I disabled the write barrier mode on the ext4 partition and that fixed it

/dev/sda3 on / type ext4 (rw,errors=remount-ro,barrier=0)

---

### Post by Udai Gupta on 2009-11-20
Do you guys have SSD, I have SSD  storage and I experienced the same problem. But. some people whom I asked never had this issue (they didn't had SSD).

---

### Post by drewjw81 on 2009-11-30
Confirmed.  A 128mb data import took almost 9 hours before I addeded barrier=0 to /etc/fstab After restart the same import to 5 minutes.

---

### Post by justincwatt on 2010-03-05
I had script that was running through 130+ create table statements, and it was taking nearly 10 seconds to complete on a fresh 9.10 install of Ubuntu. It used to take 0.8 seconds on my old machine, running an older version of Ubuntu (with ext3 fs). I discovered that the individual create table statements were taking 0.05 second to complete, whereas on my old system they took 0.00-0.01 seconds. Obviously that makes a big difference. 

All that to say, adding barrier=0 to my /etc/fstab for my new ext4 hard drive brought things back in line with my old system.

---

### Post by Bruut on 2010-04-28
I got the same issues with the same config (64 bits Karmic server, on Ext4). So I tried adding barrier=0 to my fstab and did a restart but it didn't help. It still does a 100 simple UPDATE queries to take almost 4 seconds.

This is in my fstab:

```

UUID=edc1335e-bfe2-4e5a-869c-1fa02a502b4f /               ext4    errors=remount-ro,barrier=0 0       1

```

I got a software raid setup, maybe that makes difference?

---

### Post by Bruut on 2010-05-04
(a humble kick)

Can at least anyone confirm that my fstab is correct?

Does the fstab apply for raid setups?

---

### Post by skinlayers on 2010-05-31
I'm running into the same issue on Lucid. I've installed 10.04 server on a software RAID0, and mysql runs painfully slow by default. The nobarrier switch, along with noatime and nodiratime seems to help, but I'm not sure the issue is completely resolved...

---

### Post by maimai_kt on 2010-09-07
Hi,

I am a beginner of MySQL, I hope that my experience can help you. I faced a performance issue in record inserting, fortunately it have been solved. My OS is Ubuntu 9.04 Server, and is using EXT4.

My Problem:
Insert 20 records per second :confused:

Solution:guitar::
Edit my.cnf file as below:
# Uncomment the following if you are using InnoDB tables (*****uncomment the following*****)
innodb_data_home_dir = /usr/local/mysql/data/ (*****your data home folder*****)
innodb_data_file_path = ibdata1:2000M;ibdata2:10M:autoextend
innodb_log_group_home_dir = /usr/local/mysql/data/(*****your data home folder*****)
innodb_log_arch_dir = /usr/local/mysql/data/(*****your data home folder*****)
# You can set .._buffer_pool_size up to 50 - 80 %
# of RAM but beware of setting memory usage too high
innodb_buffer_pool_size = 384M
innodb_additional_mem_pool_size = 20M
# Set .._log_file_size to 25 % of buffer pool size
innodb_log_file_size = 100M
innodb_log_buffer_size = 8M
innodb_flush_log_at_trx_commit = 1
innodb_lock_wait_timeout = 50

Finally restart MySQL, it's work;). It can inserts 4k to 5k records per second now....

):P):P
Jeff

---

