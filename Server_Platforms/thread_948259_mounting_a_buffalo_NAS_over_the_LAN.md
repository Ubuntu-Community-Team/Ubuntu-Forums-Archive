---
title: "mounting a buffalo NAS over the LAN"
date: 2008-10-15
forum: Server Platforms
---

### Post by ceabaird on 2008-10-15
Hello,

I've been surfing aound this forum (and others) trying to get this to work. Let me outline the situation, then the steps I've been taking.

I have a Linux box running 8.04, set up as a LAMP. I have installed Drupal 5.8 and I'm using data base file manager (DBFM) with the intention of allowing people here in the office to access, over the LAN, files and images stored on the server. Since the server (a dell GX520) has rather limited storage capability, we've got ourselves a Buffalo TeraStation Pro (2 TB) set as RAID 5.

Now my issue is to mount the NAS, point the drupal dbfm towards the mounted NAS, and all will be well.

Following several recommendations on the ubuntu forum site and elsewhere, I started with:

> sudo mkdir /mnt/NAS
sudo chmod 777 /mnt/NAS

Then I went to mount the NAS. The file system on the NAS is XFS, so I adjusted the following mount command:

> sudo mount -t xfs //172.24.11.50 /mnt/NAS -o rw,username=xxxx,password=XXXXX

Doing that gave the following response:

> mount: special device //172.24.11.50 does not exist

So, I tried to ping the NAS, and got thru:

> ping 172.24.11.50
PING 172.24.11.50 (172.24.11.50) 56(84) bytes of data.
64 bytes from 172.24.11.50: icmp_seq=1 ttl=64 time=0.184 ms
64 bytes from 172.24.11.50: icmp_seq=2 ttl=64 time=0.136 ms
64 bytes from 172.24.11.50: icmp_seq=3 ttl=64 time=0.124 ms

Looking at the syslogs showed me this:

> SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
SGI XFS Quota Management subsystem

Where am I going wrong? Is it the XFS file system? If so, how do i change that on the NAS?

Any advice would be greatly appreciated, thanks.

---

### Post by ceabaird on 2008-10-21
Ok, an update.

I finally got the NAS to mount, but I cheated. I did it through webmin. I mounted the NAS as a cifs-type file system, mounted on

/usr/share/drupal/files

However, although webmin shows the NAS size correctly (929 GB), and I've been saving files on it via DBFM within the Drupal page, I'm not sure that the files are actually being written to it.  I suspect they are not, and they are going to the old location which I think should be gone:

/usr/share/drupal/files/xxx

For example, after mounting the new NAS, the old files that were accessible from the Drupal site should have disappeared, right? 

They're still there.

The web interface for the NAS is no help, since it only counts % of the 1TB of storage. 200 MB isn't going to make a dent in that. How can I verify that the NAS is indeed being written to?

---

