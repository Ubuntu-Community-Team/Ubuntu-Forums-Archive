---
title: "Problems with h/d? can anyone tell me what these errors mean?"
date: 2009-04-06
forum: Server Platforms
---

### Post by gobbledigook on 2009-04-06
Hi!

I'm running 8.10 headless file server, and recently i've been having trouble connecting to my samba share. 

I have 2 drives set up to be shared, but only one has trouble connecting to it. From the windoze end it just pops up with error: network path not found. But if you try again a few times sometimes it works but others i need to restart the server.

the drive which i am having trouble with is a 320gb-ntfs which i've only had about 6 months!!  i'm not sure what is wrong, but i have extracted some segments from my log files at roughly the times of the errors... they don't look good, but i was hoping you guys could enlighten me a little more, hopefully i can save the drive!!

/var/log/samba/log.smbd:
```
[2009/04/04 19:19:38,  0] lib/util_sock.c:get_peer_addr_internal(1596)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2009/04/04 19:19:38,  0] smbd/process.c:srv_send_smb(74)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)
[2009/04/04 19:19:38,  1] smbd/service.c:make_connection_snum(1194)
  gobbledigook (192.168.1.101) connect to service Sharedfiles initially as user user (uid=1001, gid=1001) (pid 31003)
[2009/04/04 19:22:48,  0] smbd/service.c:make_connection_snum(1156)
  '/media/swap' does not exist or permission denied when connecting to [Swap] Error was Transport endpoint is not connected

```

/var/log/kern.log
```
Apr  4 19:22:19 server kernel: [769344.650154] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:19 server kernel: [769344.650754] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:19 server kernel: [769344.651426] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:19 server kernel: [769344.652005] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:19 server kernel: [769344.681267] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:1e:90:f5:2d:f9:00:21:97:90:a1:36:08:00 SRC=192.168.1.101 DST=192.168.1.120 L$
Apr  4 19:22:20 server kernel: [769345.096018] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:1e:90:f5:2d:f9:00:21:97:90:a1:36:08:00 SRC=192.168.1.101 DST=192.168.1.120 L$
```

/var/log/syslog
```
Apr  4 19:22:24 server kernel: [769349.384560] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:1e:90:f5:2d:f9:00:21:97:90:a1:36:08:00 SRC=192.168.1.101 DST=192.168.1.120 L$
Apr  4 19:22:24 server kernel: [769349.650159] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: Error reading $Mft record(s): Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_mft_record_read failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: Error reading $Mft record(s): Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_mft_record_read failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: Error reading $Mft record(s): Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_mft_record_read failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_attr_pread: ntfs_pread failed: Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: Error reading $Mft record(s): Input/output error
Apr  4 19:22:24 server ntfs-3g[3788]: ntfs_mft_record_read failed: Input/output error
Apr  4 19:22:24 server kernel: [769349.650758] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:24 server kernel: [769349.651596] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:24 server kernel: [769349.652047] Buffer I/O error on device sdb1, logical block 5
Apr  4 19:22:25 server kernel: [769349.960097] BANDWIDTH_IN:IN=eth0 OUT= MAC=00:1e:90:f5:2d:f9:00:21:97:90:a1:36:08:00 SRC=192.168.1.101 DST=192.168.1.120 L$
Apr  4 19:22:25 server kernel: [769349.960536] BANDWIDTH_OUT:IN= OUT=eth0 SRC=192.168.1.120 DST=192.168.1.101 LEN=108 TOS=0x10 PREC=0x00 TTL=64 ID=60415 DF $
```

any ideas, much appreciated!

Thanx!

Dan,

---

### Post by HermanAB on 2009-04-06
The SMB protocol is sensitive to network errors, so I would replace the ethernet card(s) and the PSUs if the trouble persists.  Network cards are really cheap - for the cost of a $10 card you can save yourself many hours of happy debugging.

---

### Post by druhboruch on 2009-04-06
To me it looks like a hard disk failure.
Backup your data asap.

---

### Post by cdenley on 2009-04-06
> **druhboruch said:**
> To me it looks like a hard disk failure.
Backup your data asap.

I agree. It definitely appears to be a hardware problem, and the hard drive is the most likely cause.

---

