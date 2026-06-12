---
title: "Virtualized Ubuntu server can write to tape at 128kb but not read from it"
date: 2011-08-14
forum: Server Platforms
---

### Post by cheehan33 on 2011-08-14
I'm using Ubuntu 11.04.
There are two servers, PhysicalA and VirtualB.
I've installed both with Ubuntu 11.04, 32bit.
VirtualB is running on top of VMware Vsphere ESX4.1.

At boot-up, the server is able to detect the SDLT Tape Library, 1 Medium Changer and 2 Tape Drives.

To read and write to the tape drive, i have 1 tape loaded into the drive first, and I run the following command:
cd /usr; find . -print | cpio -ocv | dd of=/dev/st0 bs=128k
<after writing completes>
cd /tmp/restore; dd if=/dev/nst0 of=myfile bs=128k

On PhysicalA, 
1) Check tape drive status with "mt"
root@ubuntu32b:~# mt -f /dev/nst0 status
SCSI 2 tape drive:
File number=-1, block number=-1, partition=0.
Tape block size 0 bytes. Density code 0x48 (no translation).
Soft error count since last status=0
General status bits on (1010000):
 ONLINE IM_REP_EN

2) Backup to tape
root@ubuntu32b:~# dd if=OpenDialect050.tar.gz of=/dev/st0 bs=128k
192+1 records in
192+1 records out
25210505 bytes (25 MB) copied, 16.6715 s, 1.5 MB/s

3) Restore from tape
root@ubuntu32b:~# dd if=/dev/nst0 of=myfile bs=128k
192+1 records in
192+1 records out
25210505 bytes (25 MB) copied, 10.5015 s, 2.4 MB/s

4) Syslog
n/a

On VirtualB, 
1) Check tape drive status with "mt"
root@ubuntu32:~# mt -f /dev/st0 status
SCSI 2 tape drive:
File number=0, block number=0, partition=0.
Tape block size 0 bytes. Density code 0x48 (no translation).
Soft error count since last status=0
General status bits on (41010000):
 BOT ONLINE IM_REP_EN

2) Backup to tape
root@ubuntu32:~# dd if=OpenDialect050.tar.gz of=/dev/st0 bs=128k
192+1 records in
192+1 records out
25210505 bytes (25 MB) copied, 20.5164 s, 1.2 MB/s

3) Restore from tape
root@ubuntu32:~# dd if=/dev/nst0 of=myfile2 bs=128k
dd: reading `/dev/nst0': Input/output error
192+0 records in
192+0 records out
25165824 bytes (25 MB) copied, 10.3942 s, 2.4 MB/s

4) Syslog
Jul 31 11:34:29 ubuntu-svr kernel: [  456.622375] st0: Sense Key : Medium Error [current]
Jul 31 11:34:29 ubuntu-svr kernel: [  456.622394] Info fld=0x400
Jul 31 11:34:29 ubuntu-svr kernel: [  456.622400] st0: <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff


I would've gone for VMware support at this point, until I tried an earlier version of Ubuntu Desktop, 9.0x, and as a virtual machine, I was able to read and write correctly using 128k blocksize.

Therefore, i'm posting this here, hoping to figure out this issue. I'm planning to use the latest version of Ubuntu to backup and restore from tapes. And most of my tapes have been written using 128k blocksizes.

Any help is appreciated. If you require anymore information than what I've supplied, pls advise. 

Thank you.

---

