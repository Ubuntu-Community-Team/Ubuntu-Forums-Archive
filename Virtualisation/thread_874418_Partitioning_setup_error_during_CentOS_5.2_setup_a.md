---
title: "Partitioning setup error during CentOS 5.2 setup as guest"
date: 2008-07-29
forum: Virtualisation
---

### Post by Imap on 2008-07-29
Hello,

I am attempting a CentOS 5.2 guest install on Ubuntu hardy. I have
lvm based partitions. When I attempt 'custom partition' setup during
the domain creation. I get the following error:

===============================================================
Traceback (most recent call first):                                            
  File "/usr/lib/anaconda/partitions.py", line 804, in hasGptLabel
    disk = diskset.disks[device]
  File "/usr/lib/anaconda/partitions.py", line 878, in sanityCheckAllRequests
    elif self.hasGptLabel(diskset, dev):
  File "/usr/lib/anaconda/textw/partition_text.py", line 1489, in __call__
    (errors, warnings) = self.partitions.sanityCheckAllRequests(self.diskset)
  File "/usr/lib/anaconda/text.py", line 565, in run
    rc = win(self.screen, instance)
  File "/usr/bin/anaconda", line 982, in ?
    anaconda.intf.run(anaconda)
KeyError: 'xvda'
===============================================================

Any suggestions on what could be causing the above exception.

Thanks

---

### Post by KatBuntu on 2008-07-30
Anaconda requires at least 1Gb of RAM, check your Virtual Machine resources, and... anaconda is the installer of CentOS

---

### Post by Imap on 2008-07-30
Thanks for your reply.

I had the memory set to 512Mb initially, I now changed it to 1024Mb, 
but I still get the same exception. Any other suggestions?

Thanks

---

