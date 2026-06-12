---
title: "Cant mount or partition or format hard drives"
date: 2010-04-08
forum: Server Platforms
---

### Post by NXArmada on 2010-04-08
I have a server with 3 hard drives

1 400GB
2 1TB

The 400GB has the OS and SWAP while the 1TB are going to be used as storage....

Now for the problem, when I have both the 1TB drives in I can not format or mount either 1TB drives.  Says Device is in use or "The device file '/dev/sdc1' does not exist"

Now if I take one of the 1TB drives out I can format, partition, and mount it no problem...it only seems to be a problem when both drives are connected...

Any help you guys can provide will be great.

Ubuntu Server Linux 9.10

```
fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa50be991

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  82  Linux swap / Solaris
/dev/sda2   *         487       48641   386805037+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ef8352e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ef8352e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux
```

```
lsmod
Module                  Size  Used by
fbcon                  36640  70 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
iptable_filter          3100  0 
snd_hda_codec_via      28988  1 
ip_tables              11692  1 iptable_filter
snd_hda_intel          27016  0 
i915                  226760  1 
drm                   160672  1 i915
snd_hda_codec          75708  2 snd_hda_codec_via,snd_hda_intel
x_tables               16544  1 ip_tables
i2c_algo_bit            5760  1 i915
snd_hwdep               7200  1 snd_hda_codec
snd_pcm                75520  2 snd_hda_intel,snd_hda_codec
video                  19380  1 i915
snd_timer              22276  1 snd_pcm
lp                      8964  0 
ppdev                   6688  0 
intel_agp              27940  2 i915
snd                    59204  5 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
parport_pc             32228  1 
agpgart                35020  2 drm,intel_agp
output                  2780  1 video
asus_atk0110            8252  0 
parport                35340  3 lp,ppdev,parport_pc
raid10                 23036  0 
raid456                54140  0 
raid6_pq               80912  1 raid456
async_xor               3324  1 raid456
async_memcpy            1852  1 raid456
async_tx                3260  3 raid456,async_xor,async_memcpy
raid1                  22460  0 
raid0                   8096  0 
multipath               7744  0 
linear                  5184  0 
dm_raid45              84228  0 
xor                    15620  3 raid456,async_xor,dm_raid45
r8169                  32384  0 
mii                     5212  1 r8169
```

```
cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3400832A       Rev: 3.02
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: MAXTOR STM310003 Rev: XM15
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: MAXTOR STM310003 Rev: MX15
  Type:   Direct-Access                    ANSI  SCSI revision: 05
```

---

### Post by fang0654 on 2010-04-08
What is the output of mount?

---

### Post by NXArmada on 2010-04-08
Okay...looking more into it I think cause both drives are SATA that linux is thinking raid here...So I am going to pass **nodmraid** as a boot option and see if that solves the problem

```
mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
```

---

### Post by NXArmada on 2010-04-08
SOLVED:

This most commonly happens with SATA drives. The BIOS incorrectly sees it and instead of doing the check itself, Linux uses the BIOS setting.

Passing **nodmraid** at boot solved the problem.

---

### Post by sirpixalot on 2010-07-23
> Passing **nodmraid** at boot solved the problem. 	


Hi,

I am having a similar problem. Can you please specify how you passed "nodmraid" at boot time? 

Thanks.

---

