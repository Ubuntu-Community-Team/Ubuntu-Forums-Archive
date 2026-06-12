---
title: "Software RAID6 Performance?"
date: 2011-09-22
forum: Server Platforms
---

### Post by pentas on 2011-09-22
Currently, I'm running two file servers.  One has Ubuntu Server on it and the other has Debian Squeeze.

Ubuntu Server:
E6600, 8GB Memory
8x 500GB drives
RAID6
4k chunks
Algorithm 2
ext3

Debian:
E6600, 8GB Memory
9x 500GB drives
RAID6
512k chunks
Algorithm 2
ext4

The Ubuntu server was setup, maybe 18 months to 2 years ago while the Debian server was setup a few weeks ago.  Both run stable and haven't had any issues.  Both run SAMBA for communicating with Windows hosts and both mdstat's report clean arrays with all drives operational.

The Ubuntu server can routinely move data over the network at ~60-80MB/s without breaking a sweat.  Peak access speeds can go above that.

The issue is that the Debian server is much slower!  As I type this, I am moving a 18GB file from my machine (with an SSD) to the Debian server, and I cannot get it to go above 4.5MB/s, even for smaller files, this is an issue.  I can move a 100+ MB file to the Ubuntu server without the Windows "file transfer window" even popping up.

Here's what data I have at the moment:
- Bottleneck exists with SAMBA and with SFTP (over SSH), both report maximum of ~4.5MB/s
- hdparm reports 503.24MB/s for buffered disk reads (hdparm -t /dev/md0)
- bonnie is currently running to test array performance

Does anyone have any idea what might be going on?

---

### Post by pentas on 2011-09-22
Ah, it looks like it may be a failing RAID card.  Problem solved.

---

