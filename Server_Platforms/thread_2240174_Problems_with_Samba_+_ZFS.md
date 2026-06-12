---
title: "Problems with Samba + ZFS"
date: 2014-08-18
forum: Server Platforms
---

### Post by Lukas_Hfliger on 2014-08-18
Hello,

I know that there were previous questions regarding this problem but I did not find an answer anywhere.
My problem is that transferring data from my Ubuntu server to Windows is painfully slow with 3-4 MB/s.

Here are some stats:
- Intel Core i3-3220T CPU@ 2.80GHz, 4 cores
- 7 x 4TB HDD (2 x RaidZ1 pools and 1 hot spare)
- 1 x 60GB  SSD only for the system
- 16GB RAM
- Ubuntu 14.04

Now I did perform some performance measurement:
iperf:
1 parallel stream: 112 MBytes/s
5 parallel streams: 112 MBytes/s
10 parallel streams: 111 MBytes/s

dd if=/dev/zero of=/data/Test/testfile.out bs=1M count=10000
(10GB) copied, 44.2057 s, 237MB/s

dd if=/data/Test/testfile.out of=/dev/null bs=1M
(10GB) copied, 13.8011 s, 760 MB/s

Any hints where I might improve the performance?
If you need more information just ask ;)
Thanks for your help and time 

Lukas

---

### Post by TheFu on 2014-08-18
I thought ZFS includes its own CIFS server. Isn't samba redundant? At least on Solaris it is.
[http://docs.oracle.com/cd/E19120-01/open.solaris/820-2429/createstaticsmbsharezfstask/index.html](http://docs.oracle.com/cd/E19120-01/open.solaris/820-2429/createstaticsmbsharezfstask/index.html)

I routinely transfer without ZFS on my systems (EXT4) and see 75MBps writes. Don't do many reads, but hose are limited by the Windows system storage speed in my case - laptop HDD.

Like you, I'd look for where the slowdown might be. Looks like you've removed networking, and storage where /data/Test/testfile.out sits.  Is there any non-ZFS storage on the system to rule that out?

Does ZFS have built-in performance statistics?  If I were desperate, I'd attached to the process with strace or [https://stackoverflow.com/questions/2059311/whats-an-alternative-for-dtrace-on-linux](https://stackoverflow.com/questions/2059311/whats-an-alternative-for-dtrace-on-linux)  to see where all the time was being wasted. Not fun.

---

### Post by Lukas_Hfliger on 2014-08-18
Well thank you for your reply. I set the samba sharing on via zfs but the speed is equivalent.
Little more information on my setup:
/data is the mount point of zfs
all other storage is on a SSD which is not used in any sharing (only system is stored)

I will try the strace approach ;)

---

### Post by Lukas_Hfliger on 2014-08-18
I tried using a samba share on the SSD but the transfer rate is similar. Note that the SSD is formatted as ext4 so I don't think zfs is the problem but samba is.
My local HDD is also not the problem (>100MB/s read and write)
Here is my current samba conf:
```
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 1
        syslog only = yes
        log file = /var/log/samba/log.%m
        max log size = 50
        max connections = 10
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT
        use sendfile = No
        min receivefile size = 131072
        security = user
        aio read size = 16384
        aio write size = 16384
        aio write behind = true
        wins support = Yes
[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[media]
        path = /data
        valid users = samba
        read only = No
        create mask = 0777


[zfs]
        path = /data
        valid users = samba
        read only = No


```

EDIT:
tried FTP but is similarly slow? Any ideas?

---

### Post by TheFu on 2014-08-18
Did the workload recently change?
Was this the speed always?
Anything in the logs?

I'm working on a similar issue - a system that used to xfer at 65+Mbps is now around 15Mbps ... but the workload on the system and disks has increased.  I need to test again after shutting down a few VMs, to see which is causing the impact.

---

### Post by Lukas_Hfliger on 2014-08-19
Workload on the server is minimal since  it is only used for data storage and the transfer speed is consistently low.
In the logs was nothing I could find

---

### Post by lukeiamyourfather on 2014-08-21
Are you using the ZFS on Linux implementation or the FUSE implementation? Try disabling sync writes on the file system for starters unless you absolutely need it. An example command is below. I'm able to get 400+ MB/s transfers over 10GbE to Ubuntu Server 14.04 LTS with ZFS on Linux from a client with Windows 7 so I assure you both ZFS on Linux and Samba are capable of more than you're getting right now. Can you post more information about your ZFS configuration?

```
sudo zfs set sync=disabled tank/whatever
```

Unrelated to your current issue, you should not use ZFS without ECC memory. Since the specifications show the Core i3 processor I'm guessing it doesn't have ECC memory. You're asking for trouble.

---

### Post by Lukas_Hfliger on 2014-08-23
Thanks for your reply. 
I tried this but with no significant performance gain.

I am well aware of the non-ECC ram issue but the decision for CPU was made before the decision for ECC and I cannot upgrade the hardware yet. Currently I "just risk it"

My Zfs configuration:
```
  pool: data state: ONLINE
  scan: scrub repaired 0 in 9h44m with 0 errors on Wed Jan 29 18:23:46 2014
config:


        NAME                                 STATE     READ WRITE CKSUM
        data                                 ONLINE       0     0     0
          raidz1-0                           ONLINE       0     0     0
            ata-ST4000DM000-1F2168_W300CXP9  ONLINE       0     0     0
            ata-ST4000DM000-1F2168_Z3011PD8  ONLINE       0     0     0
            ata-ST4000DM000-1F2168_W300AVT5  ONLINE       0     0     0
          raidz1-1                           ONLINE       0     0     0
            ata-ST4000DM000-1F2168_W300BT0L  ONLINE       0     0     0
            ata-ST4000DM000-1F2168_W3009R9A  ONLINE       0     0     0
            ata-ST4000DM000-1F2168_Z300ZXKW  ONLINE       0     0     0
        spares
          ata-ST4000DM000-1F2168_Z3011N0G    AVAIL


errors: No known data errors

```
Can I post you anymore information?

---

### Post by lukeiamyourfather on 2014-08-26
What does the network look like between the machines, maybe a wireless connection in there? Please post the output of "sudo zfs get all data/whatever" where whatever is any file system you might have created if applicable. It will list parameters of the file system. Also that processor does support ECC memory according to Intel (your motherboard might be another story though).

[http://ark.intel.com/products/65694/Intel-Core-i3-3220T-Processor-3M-Cache-2_80-GHz](http://ark.intel.com/products/65694/Intel-Core-i3-3220T-Processor-3M-Cache-2_80-GHz)

---

