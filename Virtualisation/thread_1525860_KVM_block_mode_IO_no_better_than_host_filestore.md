---
title: "KVM block mode I/O no better than host filestore?"
date: 2010-07-07
forum: Virtualisation
---

### Post by pootle42 on 2010-07-07
I'm a bit puzzled, I have an ubuntu VM (2.6.28-14-server #47-Ubuntu SMP Sat Jul 25 01:18:34 UTC 2009 i686 GNU/Linux) running on an ubuntu host (2.6.31-20-server #58-Ubuntu SMP Fri Mar 12 05:40:05 UTC 2010 x86_64 GNU/Linux).

I have a 150Gb disc in the VM (mainly photos), and the performance is a bit naff (it is a file based virtio disc). It sounded like a block mode disk should be significantly better, so I added one in and used hdparm to do a quick sanity check on the difference between the 2 volumes, but it seems to have made no real difference at all.  Is this because the system is limited by the discs I'm using?  I would have expected to see some difference.  Even the CPU  load on the host machine is not noticeably different when running tests on the 2 different disk types.  I/O performance in the VM is not significantly slower than on the host machine.  Using mdadm seems to be giving me a big performance loss though - but that is another story!

The setup is as follows:
host machine: 
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxex
t fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2000.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxex
t fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 2000.80
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```


[LIST]
[*]4Gb RAM
[*]4 off 320Gb 2.5" discs running under mdadm raid 10
[*]1 Physical Volume
[*]3 logical volumes:
[*]disc a with single partition mounted on host as ext4, contains files for all VMs
[*]disc b with single partition passed through as block device to VM being tested above
[*]disc c with other filestore in it.
[/LIST]

In the VM 1 data disc is mapped to a host file on disc a, and the other data disc is mapped to disk b in block mode.

here's the hdparm output: (vdb is the block mode device)
```
/dev/vdb1:
 Timing cached reads:   1976 MB in  2.00 seconds = 987.94 MB/sec
 Timing buffered disk reads:  108 MB in  3.07 seconds =  35.20 MB/sec
iain@newworld:~$ sudo hdparm -Tt /dev/vda1

/dev/vda1:
 Timing cached reads:   2006 MB in  2.00 seconds = 1002.77 MB/sec
 Timing buffered disk reads:  112 MB in  3.05 seconds =  36.69 MB/sec
iain@newworld:~$ sudo hdparm -Tt /dev/vdb1

/dev/vdb1:
 Timing cached reads:   2018 MB in  2.00 seconds = 1008.97 MB/sec
 Timing buffered disk reads:   94 MB in  3.03 seconds =  31.07 MB/sec
iain@newworld:~$ sudo hdparm -Tt /dev/vda1

/dev/vda1:
 Timing cached reads:   1688 MB in  2.00 seconds = 843.57 MB/sec
 Timing buffered disk reads:  122 MB in  3.05 seconds =  40.02 MB/sec

```

and here is the output of hdparm on the host machine:
```
/dev/gendata/vmdata:
 Timing cached reads:   1912 MB in  2.00 seconds = 956.40 MB/sec
 Timing buffered disk reads:  112 MB in  3.01 seconds =  37.19 MB/sec

```

---

### Post by sh1ny on 2010-07-07
Running software raid is cpu bound iirc. You can't squeeze more than there's already there :) Here's a hdparm on a kvm with file based virtio hdd with a host that has an LSI raid ( 4 disks in raid6 - so it's hell of a lot slower than raid10 ) :



```
/dev/vda:
 Timing cached reads:   14470 MB in  2.00 seconds = 7242.04 MB/sec
 Timing buffered disk reads:  292 MB in  3.01 seconds =  97.13 MB/sec
```

So i'd say you're doing great :)

---

### Post by TheFu on 2010-07-07
You didn't say the model of either the controller or the disk drives.  I've been using mdadm for years and never been CPU bound on a core 2 duo or better CPU.
Also, you aren't showing write speeds. Those would be interesting to me. 

Here are my host numbers:

> Timing cached reads:   17494 MB in  2.00 seconds = 8754.94 MB/sec
Timing buffered disk reads:  660 MB in  3.00 seconds = 219.72 MB/secInside a client - no virtio - just a "full disk image" file.
> Timing cached reads:    13768 MB in  1.98 seconds = 6962.07 MB/sec
Timing buffered disk reads:  1376 MB in  3.00 seconds = 458.54 MB/secDisk array is connected through a normal SATA MB controller. Software RAID5. Obviously, some VM disk caching is helping out with the buffered reads.  Oh - this is a virtualbox system now, not KVM. Sorry if that negates my quick testing.

---

### Post by pootle42 on 2010-07-09
*Sh1ny, I'd agree if it was raid5, but raid 0,1,10 aren't nearly so CPU intensive.

I did an upgrade to lucid (on the host) and disk manager promptly threw up it's hands in horror saying the array was misaligned, and lvm threw away all my data!  So I rebuilt it under lucid and restored the data and performance is now significantly better (70 - 80 Mb/s for read), but file based virtio disks are still coming back consistently 5% - 10% faster than block based virtio discs, so I'll just stick with filestore I think ;)

CPU utilisaton while test is running peaks at < 25% of 1 cpu.

The disc controller btw is just the one on my motherboard - SB700/SB800 is reported.

---

