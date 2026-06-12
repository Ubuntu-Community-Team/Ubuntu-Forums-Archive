---
title: "Fileserver w/ ntfs-3g, 99.9% CPU usage"
date: 2007-01-17
forum: Server Platforms
---

### Post by vkkim on 2007-01-17
I have been running a small headless file/web server using Edgy on a laptop (I don't have much physical space) with a 1.2 GHz Pentium M Dothan processor and 1.25 GB of RAM and a 1 TB external HDD (USB) mounted using the ntfs-3g driver (version .200610) for maybe a little over a month now.  It doesn't get much traffic (maybe 4-5 users max at any one time requesting files) and it is accessed via a 10 Mbit LAN connection.  I'm not sure if this is a recent problem or not, but I have only noticed it recently.  When a user is uploading files to the server via SFTP (I am running OpenSSH 4.3p2-5ubuntu1), ntfs-3g ties up the CPU with 99.9% usage and access is virtually impossible via Apache, SFTP, or Samba (I am running all three concurrently).  I am not sure if this is a SSH-only problem or if similar problems exist using another method, but this problem does not happen when writing to the ntfs-3g mounted disk within the local environment (i.e., when the source file is on any disk physically connected to the server).  Here is a sample output from top:

```
top - 04:31:35 up 3 days,  5:31,  2 users,  load average: 1.06, 1.08, 1.03
Tasks:  99 total,   3 running,  96 sleeping,   0 stopped,   0 zombie
Cpu(s): 99.3%us,  0.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1286616k total,  1262876k used,    23740k free,   346808k buffers
Swap:  1469908k total,      244k used,  1469664k free,   623552k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5060 root      25   0  9212 6856  600 R 99.7  0.5   1757:31 ntfs-3g

```

Is anyone else having a similar problem?  Is this caused by the ntfs-3g program?  If so, is there any other program I can use to mount ntfs drives reliably with rw capabilities?

---

### Post by szaka on 2007-01-17
> **vkkim said:**
> Is this caused by the ntfs-3g program?
It is caused by old ntfs-3g.  Newer releases are reported to be much better in general: [http://www.ntfs-3g.org/releases.html](http://www.ntfs-3g.org/releases.html)

---

### Post by vkkim on 2007-01-17
Okay, I tried compiling the latest version (.20070116) from the website today and everything seems to run much smoother, not exceeding 20% CPU load even with two simultaneous users doing rw operations.

---

