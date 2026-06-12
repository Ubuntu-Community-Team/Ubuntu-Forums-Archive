---
title: "Slow IO over Samba/NFS"
date: 2011-09-05
forum: Server Platforms
---

### Post by Chireru on 2011-09-05
Running into a weird issue.  Some IO runs at 80+MB/sec, the rest (and most important pieces) run at ~30MB/sec.

Server is mainly used as a fileserver.  I have a gigabit network, with everything linked at gigabit.

Things that work at 80MB/sec or higher:
[LIST]
[*]cat a file into /dev/null on the server
[*]Bonnie
[/LIST]
```
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
ako           4018M           56561  10 32386  12           **88826**  16 110.1   3
Latency                        5549ms     228ms             43102us     430ms

1.96,1.96,ako,1,1315246753,4018M,,,,56561,10,32386,12,,,88826,16,110.1,3,,,,,,,,,,,,,,,,,,,5549ms,228ms,,43102us,430ms,,,,,,

```

Things that work at around 30MB/sec:
[LIST]
[*]Reading files using Samba
[*]Reading files using NFS
[/LIST]
=> Both of these tests were done to eliminate other variables: Either we were writing to an SSD disk, which has a write speed that is much faster than the server's read speed, or, eliminate the client's IO by running cat a file on a NFS-mounted from the server into /dev/null.  Clients include Win7 and Ubuntu Natty Desktop.

The network is not the problem... if we remove disk IO, and transfer from /dev/zero on one system to /dev/null on the other, without compression:
[LIST]
[*] CLIENT: # netcat -l 5555 > /dev/null
[*] SERVER: # cat /dev/zero | netcat 10.10.221.18 5555
[*] Monitor on client with iptraf or other tool... shows a steady 55MB/sec (slow for gigabit, but still 25MB/sec higher than what I'm getting)
[/LIST]
IOStat shows about 60% IO utilization on the disk during Samba or NFS transfer.

For purposes of this post, all transfers done with single large, uncached files off the same disk.  Source FS is xfs.

This issue has been going on for a long time, but I had slower disks previously, and didn't think anything of the 30MB/sec speeds.. but after upgrading the disks, everything still runs at the same speed, even though everything else says the disks are capable of much higher speeds.

Server is running Ubuntu Lucid LTS, fully patched, was installed (not upgraded) several months ago.

---

### Post by kevin11951 on 2011-09-05
Are you using RAID (esp. 4/5/6) by any chance?

---

### Post by Chireru on 2011-09-05
There's RAID1 for the OS disks but not for the data disks, it's just a normal SATA disk connected to the motherboard's SATA controller:
```
[    2.550041] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.575777] ata8.00: ATA-8: WDC WD2002FAEX-007BA0, 05.01D05, max UDMA/133
[    2.575780] ata8.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    2.591002] ata8.00: configured for UDMA/133
[    2.591067] scsi 7:0:0:0: Direct-Access     ATA      WDC WD2002FAEX-0 05.0 PQ: 0 ANSI: 5
[    2.591220] sd 7:0:0:0: Attached scsi generic sg7 type 0
[    2.591621] sd 7:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.591660] sd 7:0:0:0: [sdf] Write Protect is off
[    2.591663] sd 7:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    2.591684] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.591809]  sdf: sdf1
[    2.595398] sd 7:0:0:0: [sdf] Attached SCSI disk
[    2.771160]   alloc irq_desc for 16 on node 0
[    2.771164]   alloc kstat_irqs on node 0
[    2.771175] ohci1394 0000:00:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

```

---

### Post by ian dobson on 2011-09-06
Hi,

Have you tried playing with the socket options (in smb.conf)? 30Mb/Sec for samba read isn't that bad. What are the write speeds like?

For me the following options gave the best performance
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 rlimit_max=16384 IPTOS_LOWDELAY SO_KEEPALIVE

Regards
Ian Dobson

---

### Post by Chireru on 2011-09-06
I did some toying with the Socket, and other performance options at one point, so mine aren't default:

My SMB Socket options:
```
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT
use sendfile = Yes
write cache size = 262144
large readwrite = yes
read raw = yes
write raw = yes

```

Using mine:
Read: ~30-33MB/sec
Write: ~30-33MB/sec

Using your socket options + my other performance options listed:
Read: ~30-33MB/sec
Write: ~30-33MB/sec

Using your socket option only (disabling the rest):
Read: ~20-23MB/sec
Write: ~30-33MB/sec


Here's the fun part though:  Regardless of what the socket settings are, reading a non-recently-read file will perform about the same, but reading a file that has been read recently (and is in memory cache) will read at 60-70MB/sec.

The problem isn't that 30MB/sec is bad... it's just I could get that if I had spent less and bought a 5400rpm disk, like I was running on before :(

---

### Post by ian dobson on 2011-09-06
Hi,

oH OK the problem is reading non-cached files. All you can do is try playing with the readahead options for the drive.

Have a look at the blockdev --setra command

Regards
Ian Dobson

---

### Post by Chireru on 2011-09-06
Well, that's the thing, I'm not sure it's read-ahead that's the problem.  The disk appears to read-ahead fine when I'm using it locally, but over the network it doesn't...

I toyed around with that command, setting the read-ahead value of the disk to a variety of values.  Default is 256 sectors, I tried 512, 1024, and even 10240, 64, and 0.  All performed about the same, 30-33MB/sec via Samba.

---

### Post by Chireru on 2011-09-07
The more I look at this, the more convinced I am that this is an issue with the network configuration on the server.

I set up FTP on the server, and found that the performance is the same, about 30-33MB/sec (shocking).

However, when reading a file locally, I can stress it to 100% utilization, around 80+MB/sec.

I tried playing around with the kernel TCP buffer settings, but nothing seemed to increase the performance, so I set everything back.

Transferring over IPv4 vs IPv6 makes no difference.  Any ideas?

---

### Post by ian dobson on 2011-09-07
Hi,

If you think it's a network problem, then have a look at Iperf.

Are you using a RTL81xx network card? I can remember having performace problem with a linux box using a rtl card. In the end I replaced it with an intel card and increased the network throughput by about 30%.

Regards
Ian Dobson

---

### Post by Chireru on 2011-09-07
The NIC is a Marvell Yukon 88E8001.  One of the clients has a RealTek, the other has an Intel.

```
[  4] local 10.10.221.2 port 5001 connected with 10.10.221.8 port 43309
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec    540 MBytes    452 Mbits/sec
[  5] local 10.10.221.2 port 5001 connected with 10.10.221.8 port 43319
[  5]  0.0-10.0 sec    519 MBytes    434 Mbits/sec
[  4] local 10.10.221.2 port 5001 connected with 10.10.221.8 port 43322
[  4]  0.0-10.0 sec    534 MBytes    447 Mbits/sec
```

Lowest was 434Mbit/s, which gives us the ~55MB/s that I saw earlier when I did my manual network testing.

Did a bit more testing.  I figured that since IO works fine, and Network works fine independently of each other, that it's the combination of the two that is the problem.

When I attempt to stress both at the same time (cat a large file locally > /dev/null, and funnel /dev/zero through netcat to another system), IOStat says the diskIO maintained 46MB/sec, but according to iptraf, the network was only going 20MB/sec.  CPU was at 100% used while dealing with these tasks simultaneously.  

However, when I use Samba to read a file:
* CPU looks OK, is 50-60% idle... far from 100% busy.

* Memory looks OK, not swapping, lots of buffers, lots of cache, some free memory, which never runs out.

* Disk IO looks OK, it`s at 70% IO Utilization, and at less than 1% IOWait CPU, so lots of room here.  (Capable of 88MB/sec at 100% IO utilization).

* Network IO looks OK, 30MB/sec using about 20-25% CPU for interrupts.  Lots of room here too.  (Capable of 55MB/sec (including protocol overhead).  At that point it would use about 25-30% CPU for interrupts).

* Samba uses about 15% CPU.

That`s all the normal bottlenecks.  Since netcat uses TCP, those capability numbers should be accurate unless Samba and NFS and FTP are all doing something wacky to the TCP stack.

I`m out of ideas... this makes no sense to me.  Has to be something related to IO+Network together.

---

### Post by ian dobson on 2011-09-08
Hi,

OK can you try using nc to transfer a real file over the network.

If your using 25-30%cpu for interrupts in the network test, that'll reduce the free CPU to handle the disk (also interrupts) and I think only one ISR (Interrupt service routine) can be active at any time.

Is it possible to try a different network card on the server? I've always had good experiances with intel cards.

Regards
Ian Dobson

---

### Post by Herm87 on 2011-09-08
Dear Chireru

I am experiencing similar problems, but far worse. I have been Ubuntu on my Intel D945GSEJT for two years. It's main purpose is routing and NAS. Needing the CF-card somewhere else, I recently installed a SSD for the system, small files and working data while an ordinary harddisk holds the large files and backups. The problem: Writing to the SSD is possible with decent speed at first filling the buffer up to 128MB (at 45MBps through SMB from Windows, an Ubuntu client performs similar), but then the speed drops down to only 3MBps. This is totally inacceptable. smbd uses 30% CPU, I don't believe this is the bottleneck. Writing to the SSD locally works with 120MBps. Reading unbuffered data from the SSD through the network is possible at 9MBps. Reading unbuffered data locally is possible at 133MBps. Filesystem on the SSD is ext4 aligned to 1MB blocks, noop is used as elevator. Now for the weird part: The standard harddrive performs perfectly fine (45MBps read or write). Both drives are connected to the same controller (mode is set to AHCI). I am also totally out of ideas.

Regards
Hermann

---

### Post by ian dobson on 2011-09-08
Hi,

Have a look here [http://wiki.amahi.org/index.php/Make_Samba_Go_Faster](http://wiki.amahi.org/index.php/Make_Samba_Go_Faster) , the async options look very interesting, also the write behind option if speed is more important that safe.

Regards
Ian Dobson

---

### Post by Chireru on 2011-09-08
If I cat a file over Netcat (to /dev/null on the other side), it still goes slow.  Averaging 32.5MB/sec.

CPU was: 
1.0% user
29.0% system
28.4% idle
14.5% iowait
6.6% hardware interrupts
20.1% software interrupts

netcat used about 26% CPU, and cat used about 11% CPU
IO Utilization was between 65-70%.

I'll toy around with the samba options, but I'm not convinced that's the problem, since it's affecting even a simple netcat transfer.

I don't have an Intel card, but I do have a Netgear GA311 that I can swap in there.  I'll give that a test and see if it performs any better.

Hermann gave me an idea... I've only been testing using one disk.  I tried performing the same netcat on my other disks.  The other data disk I have performed the same, 30MB/sec, but my RAID1 (of two 10,000 RPM disks) went at 46MB/sec (40-60% IO utilization per disk). -- This is better than 30MB/sec, but in many ways, the exact same -- not taxing the network, CPU, or IO.

---

### Post by Herm87 on 2011-09-09
@ian's link "Make Samba Go Faster":
Async IO is a good idea. Unfortunately, those settings have no positive effect. I suspect it's a problem with the manner in which samba (or ftp) write files. It must be different from what dd does. Maybe smbd starts to write in 128kB blocks or something.

---

### Post by Chireru on 2011-09-10
I haven't had a chance to test any suggestions yet, but one interesting thing that I can report on is that I have an old IDE disk set up for iSCSI testing.  

I mounted it on a client and cat a file > /dev/null, and it achieved 46MB/sec transfer, with 100% IO utilization on the client and a  IO utilization bouncing between 50-100% on the server.

Interesting.  I will have to do more testing...  I have a feeling this may be hardware or driver related.
* Mount the iSCSI disk locally on the server, share through Samba and see what speeds I get.
* Connect the disk I've been testing to each of the other two SATA controllers in the server.
* Swap the server's NIC
* Try the samba settings

---

### Post by Herm87 on 2011-09-12
Mystery solved for my part. It's actually the SSD that is slow. It turns out it's either faulty or a ripoff product. Testing the SSD locally, I was dd'ing /dev/zero to the SSD and the Firmware uses a compression algorithm (Huffman, I assume) to reduce the amount of data that is actually written. Writing urandom leads to the same bad performance as experienced over network. This still doesn't explain why writing zeroes over network is also slow, but I definitely need a better SSD.

---

### Post by Chireru on 2011-09-12
> **Herm87 said:**
> Writing urandom leads to the same bad performance
/dev/urandom has bad performance to begin with...  It relies on entropy within the system, which does not come quickly.

/dev/zero > /dev/null goes at 1.4GB/s
/dev/urandom > /dev/null goes at 5.2MB/s
```
$ time dd if=/dev/zero of=/dev/null bs=1024 count=100000000
100000000+0 records in
100000000+0 records out
102400000000 bytes (102 GB) copied, 72.6448 s, 1.4 GB/s

real    1m12.650s
user    0m12.410s
sys     0m58.860s
$ time dd if=/dev/urandom of=/dev/null bs=1024 count=1000000
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 197.459 s, 5.2 MB/s

real    3m17.464s
user    0m0.180s
sys     3m12.240s
```

---

### Post by Herm87 on 2011-09-13
Good point. I used Atto Disk Benchmark for Windows, but I'd like to reproduce the test on Linux. I'll look for a faster non-all-the-same data generator.

---

### Post by Chireru on 2011-09-14
Not much luck...  all of the tests came out the same, or worse:

*** Mount the iSCSI disk locally on the server, share through Samba and see what speeds I get.**
Slow speeds.  Even slower than normal... 22MB/s
*** Connect the disk I've been testing to each of the other two SATA controllers in the server.**
Same speeds, regardless of controller.
*** Swap the server's NIC**
Same speeds, 30MB/s
*** Try the samba settings**
Same speeds, 30MB/s

---

### Post by kid1000002000 on 2012-06-21
Some of us are having it perform perfectly fast from a windows client, but slow from a linux client to a linux NAS.

[https://bugzilla.samba.org/process_bug.cgi](https://bugzilla.samba.org/process_bug.cgi)
[http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)

---

