---
title: "virtual server crashing"
date: 2008-03-21
forum: Virtualisation
---

### Post by vortmax on 2008-03-21
I'm running feisty as a VM on a VMware ESX Server (3.5.0).  About a month ago, I came in to find that things weren't working right.  I took a look in the logs and found that there was a major disk error.  I managed to boot into the recovery console and fsck it back to life.

Last weekend we upgraded the VM server to the new version (3.5.0) and I come in today to find the same error.  Here is a snipit of the error log:

```

[447282.369878] mptbase: ioc0: IOCStatus(0x0002): Busy
[447282.369882] mptbase: ioc0: IOCStatus(0x0002): Busy
[447282.789320] mptbase: ioc0: IOCStatus(0x0002): Busy
[447282.789339] mptbase: ioc0: IOCStatus(0x0002): Busy
[447282.789343] mptbase: ioc0: IOCStatus(0x0002): Busy
[447282.789347] mptbase: ioc0: IOCStatus(0x0002): Busy
[447543.297804] sd 0:0:0:0: SCSI error: return code = 0x00020008
[447543.297840] end_request: I/O error, dev sda, sector 27574719
[447543.297946] Buffer I/O error on device sda1, logical block 3446832
[447543.298116] lost page write due to I/O error on sda1
[447543.298341] Aborting journal on device sda1.
[447543.300365] journal commit I/O error
[447543.300603] ext3_abort called.
[447543.300677] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[447543.300864] Remounting filesystem read-only
[447543.352857] journal commit I/O error
[447543.813492] device eth0 left promiscuous mode
[447543.813513] audit(1206087116.313:3): dev=eth0 prom=0 old_prom=256 auid=4294967295

```

I'm going to try and fsck it again to revive it, but I can't have this happening.  I moved this system from a POS pentium 4 machine I use for development for the stability and reliability of the VM environment, but it was a million times more stable on it's own machine.

---

### Post by fjgaude on 2008-03-21
Could it be that a disk is going bad? Or could it be RAM?

---

### Post by vortmax on 2008-03-21
It shouldn't be a HD.  The Vm server is running off a huge san, so the actual VM is being striped across several disks.  There are also 23 other VM's running , some of which demand much more memory, diskspace and disk activity and they don't have any issues.

---

### Post by mixed9 on 2008-05-07
We are experiencing similar issues out of nowhere - did you find a solution?

---

### Post by klchxbec on 2009-02-04
Check your kernel version. See this :

[http://kb.vmware.com/kb/1001778](http://kb.vmware.com/kb/1001778)

---

### Post by CNBarnes on 2011-01-06
Ug, this is the 2nd forum I've seen this link.  Yet when I click on it, it tells me I'm not "authorized to view it".   

I'm really beginning to hate VMWare...

---

