---
title: "SFTP SSH File transfer slow"
date: 2010-04-24
forum: Server Platforms
---

### Post by Lokro on 2010-04-24
I'm trying to transfer some files using filezilla and the SFTP - SSH File Transfer Protocol and I'm getting around 9 MB/s. If I transfer in Samba I'm getting 90 MB/s. I am behind a 1000 Mbps Gigabit Switch and it is all showing to be connected correctly. What can I do to speed up this SFTP transfer? Kind of a pain to drag and drop with Samba right now.

---

### Post by v1ad on 2010-04-24
try winscp and use the option of scp instead of sftp. if you are doing windows to linux. if linux to linux use the command console.

---

### Post by Lokro on 2010-04-24
ok just downloaded and set up winscp and used scp and my transfer speeds are still slow. 8,120 KiB/s

---

### Post by konsole on 2010-04-24
> **Lokro said:**
> ok just downloaded and set up winscp and used scp and my transfer speeds are still slow. 8,120 KiB/s

this slow speed is the price you're paying for encryption. If you're on a home or trusted network just use ftp and ftpd. 500+ Mb/s depending on whatever you're transferring.

---

### Post by chokfulla on 2010-09-14
I have noticed the same problem.  Using WinSCP on Win7 64 I get about the same (~6KBps)transfer rates to/from my Ubuntu 9.10 Server, which is two feet away on a gigabit LAN.  When transferring from my Fedora 11 box at my house via the internet, I cap out my bandwidth limit (>30KBps.  I'm sure that I'm taking a performance hit for encryption, but it doesn't seem to affect my Fedora box.
Samba transfers from the same Ubuntu Server are in the neighborhood of 70 MBps.

---

### Post by BkkBonanza on 2010-09-14
I really don't see how the encryption could hit xfer so hard. I mean ecryptfs can do the encryption with only a very slight degradation. I don't have another answer for you but it seems unlikely that the ssh encryption routines would be that much worse. 

I did do a few tests on my LAN (GBit). Results using scp: 

```
default        - 20 MB/s (aes128-ctr)
-c blowfish    - 36 MB/s
-c 3des        - 12 MB/s
-c arcfour     - 50 MB/s
-c cast128-cbc - 22 MB/s
-c aes256-cbc  - 30 MB/s
```
It seems most of them are better than the default, and I noticed they start out fast and slow down as they progress (350 MB file). I suspect that is due to source file not being in cache - which means that target drive speed plays a big part in limiting speed (at least in my case as this server is using a flash drive which is limited to 30MB/s at very best). ie. I'm seeing mostly speed being limited by the target drive.

Using dd to copy the same file to /dev/null runs 325 MB/s (which means it's all in the cache).

I think blowfish was likely best for consistency overall.

---

### Post by joculi on 2010-12-04
I'm seeing the same problem.  My sftp whether from Filezilla or the command line is terribly slow.  The remote server is RedHat enterprise 3.  My local client is Ubuntu 10.04.  

My data rate briefly started out around 30 kb/s (which is already very bad) and then degrades to about 3-4 kb/s.  

Both server and client are essentially idle according to top.  Plenty of memory, cpu, etc available.  

The transfer is across the internet, not my LAN, but when I use a filezilla on windows client I get far better rates.  

Any idea what could be wrong or what I can do?

---

### Post by msandoy on 2011-01-21
I'm also having the same problem. I'm running Ubuntu server 10.04.1 and Ubuntu 10.04 desktop. I have gigabit network between the computers, and the speed is good for ordinary ftp. sftp is really slow, down to 100 megabit. I have been trying to find any sollution to this transfer limitation, but no luck. 
I'm trying to have as few server processes as possible on my server box, and was hoping to get by with only ssh.
Is there any way to increase the transfer rate in sftp?

Edit: I just tested with sshfs, and got 14.5 mb/sec, transfering a 700mb ISO file. Non of the computers are working hard during this process, and non of the hard drives are either. Everything is looking completely normal, except for the speed.

---

### Post by marek_online on 2011-04-12
Did anyone find a fix for this problem?

Facing precisely the same issue on a wireless LAN, both boxes running Maverick, scp and sshfs giving transfer speeds of about 100Kb/s at best, and stalling completely after an hour or so of that.

---

### Post by dafreez on 2011-09-14
Im having the same problem. I set up a sftp server to stream my music and sync my docs while on a three month research trip. Now Im gone and everything is working but speeds are ridiculously slow. Im getting about 35kB/s down (clientside) and at most 100kB/s up (again, clientside). The bottleneck should be my ISP rates which are ca 0.8 MB/s up and ca 12MB down (serverside).

Anyone found a fix for this? Otherwise I'll set up  a ftp server and mount all the data read-only.

---

### Post by roy.nico on 2011-09-22
Hej, i encounter the same problem. 
Between two PC (Lucid and Maverick) with gigabit NIC  : 
* sftp with filezilla : 15MB/s
* Samba : 30 MB/s
* NFS : 50-60 MB/s

The PCs are quite recent, and i do not expect the encription to slow down the process so much.

---

