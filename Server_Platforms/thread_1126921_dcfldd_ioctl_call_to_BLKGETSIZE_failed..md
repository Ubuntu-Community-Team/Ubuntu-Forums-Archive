---
title: "dcfldd: ioctl call to BLKGETSIZE failed."
date: 2009-04-15
forum: Server Platforms
---

### Post by NFN_NLN on 2009-04-15
Environment
-----------

OS: Ubuntu 8.04.1 (hardy)
kernel: 2.6.24-19-generic #1 SMP i686
Platform: VMWare with virtual disks
dcfldd 1.3.4

Problem
-------

dcfldd is unable to get the total block size of sde.  If I set sizeprobe=if it estimates fine.  The transfer works but it is unable to output proper progress bar if it can't get the total device size.

This is reproducible.

Output
------

# dcfldd of=/dev/sde if=/dev/sdc sizeprobe=of
dcfldd: ioctl call to BLKGETSIZE failed.
[-2147483648% of 0Mb] 3072 blocks (96Mb) written. 00:00:-04 remaining.

Notes
-----

[http://dcfldd.sourcearchive.com/documentation/1.3.4/sizeprobe_8c-source.html](http://dcfldd.sourcearchive.com/documentation/1.3.4/sizeprobe_8c-source.html)

00062 /* I stole this from Jesse Kornblum's md5deep */
00063 static off_t get_dev_size(int fd, long blksize) 
00064 {
00065     off_t num_sectors = 0;
00066   
00067     if (ioctl(fd, BLKGETSIZE, &num_sectors))
00068         log_info("%s: ioctl call to BLKGETSIZE failed.\n", program_name);
00069     else 
00070         return (num_sectors * 512);
00071 }

Caveat
------

1.
sdb,c,d were available at boot time.  sde was added during runtime from VMWare and pushed into ubuntu using rescan-scsi-bus.sh from the scsitools package.

2.
sdb,c,d are all < 200Mb while sde is ~8Gb

- NFN_NLN

---

