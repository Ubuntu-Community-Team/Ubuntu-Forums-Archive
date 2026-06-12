---
title: "Ubuntu 8.1 &amp; sil3114"
date: 2010-05-07
forum: Server Platforms
---

### Post by w00tie on 2010-05-07
Hi, 

I have a very strange problem...
I'm running ubuntu server for some time now & decided to add more harddrive space.

I installed and sil3114 card along with 2 WD harddisks and the stripe was showing up in dev/mapper/ and i was able to create a file system and mounted the stripe w/o problems.

Today, i've swapped the 2 WD for 2 Samsung harddisks and nothing shows up in /dev/mapper/.

This is the ouput of 

dmraid  -b

/dev/sdg:    976773168 total, "S20BJ9CZ403174"
/dev/sdf:    976773168 total, "S20BJ9CZ403173"
/dev/sde:   1953525168 total, "WD-WCASJ1827405"
/dev/sdd:   1953525168 total, "WD-WCASJ1827735"
/dev/sdc:   1953525168 total, "WD-WCAU45684031"
/dev/sdb:   1953525168 total, "WD-WCAU46001164"
/dev/sda:   1953525168 total, "WD-WCAU45892266"

dmraid -s 

*** Active Set
name   : nvidia_abgdcjdh
size   : 3907050240
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
*** Active Set
name   : nvidia_edgidahf
size   : 3907050240
stride : 128
type   : raid5_ls
status : ok
subsets: 0
devs   : 3
spares : 0

dmraid -vvv -ddd -ay

WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdh
NOTICE: /dev/sdg: asr     discovering
NOTICE: /dev/sdg: ddf1    discovering
NOTICE: /dev/sdg: hpt37x  discovering
NOTICE: /dev/sdg: hpt45x  discovering
NOTICE: /dev/sdg: isw     discovering
NOTICE: /dev/sdg: jmicron discovering
NOTICE: /dev/sdg: lsi     discovering
NOTICE: /dev/sdg: nvidia  discovering
NOTICE: /dev/sdg: pdc     discovering
NOTICE: /dev/sdg: sil     discovering
NOTICE: /dev/sdg: via     discovering
NOTICE: /dev/sdf: asr     discovering
NOTICE: /dev/sdf: ddf1    discovering
NOTICE: /dev/sdf: hpt37x  discovering
NOTICE: /dev/sdf: hpt45x  discovering
NOTICE: /dev/sdf: isw     discovering
NOTICE: /dev/sdf: jmicron discovering
NOTICE: /dev/sdf: lsi     discovering
NOTICE: /dev/sdf: nvidia  discovering
NOTICE: /dev/sdf: pdc     discovering
NOTICE: /dev/sdf: sil     discovering
NOTICE: /dev/sdf: via     discovering
NOTICE: /dev/sde: asr     discovering
NOTICE: /dev/sde: ddf1    discovering
NOTICE: /dev/sde: hpt37x  discovering
NOTICE: /dev/sde: hpt45x  discovering
NOTICE: /dev/sde: isw     discovering
NOTICE: /dev/sde: jmicron discovering
NOTICE: /dev/sde: lsi     discovering
NOTICE: /dev/sde: nvidia  discovering
NOTICE: /dev/sde: nvidia metadata discovered
NOTICE: /dev/sde: pdc     discovering
NOTICE: /dev/sde: sil     discovering
NOTICE: /dev/sde: via     discovering
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: nvidia metadata discovered
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: nvidia metadata discovered
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: nvidia metadata discovered
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: nvidia metadata discovered
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching nvidia_abgdcjdh
DEBUG: _find_set: not found nvidia_abgdcjdh
DEBUG: _find_set: searching nvidia_abgdcjdh
DEBUG: _find_set: not found nvidia_abgdcjdh
NOTICE: added /dev/sde to RAID set "nvidia_abgdcjdh"
DEBUG: _find_set: searching nvidia_abgdcjdh
DEBUG: _find_set: found nvidia_abgdcjdh
DEBUG: _find_set: searching nvidia_abgdcjdh
DEBUG: _find_set: found nvidia_abgdcjdh
NOTICE: added /dev/sdd to RAID set "nvidia_abgdcjdh"
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: not found nvidia_edgidahf
DEBUG: _find_set: not found nvidia_edgidahf
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: not found nvidia_edgidahf
NOTICE: added /dev/sdc to RAID set "nvidia_edgidahf"
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: found nvidia_edgidahf
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: found nvidia_edgidahf
NOTICE: added /dev/sdb to RAID set "nvidia_edgidahf"
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: found nvidia_edgidahf
DEBUG: _find_set: searching nvidia_edgidahf
DEBUG: _find_set: found nvidia_edgidahf
NOTICE: added /dev/sda to RAID set "nvidia_edgidahf"
DEBUG: checking nvidia device "/dev/sdd"
DEBUG: checking nvidia device "/dev/sde"
DEBUG: set status of set "nvidia_abgdcjdh" to 16
DEBUG: checking nvidia device "/dev/sda"
DEBUG: checking nvidia device "/dev/sdb"
DEBUG: checking nvidia device "/dev/sdc"
DEBUG: set status of set "nvidia_edgidahf" to 16
RAID set "nvidia_abgdcjdh" already active
INFO: Activating stripe RAID set "nvidia_abgdcjdh"
RAID set "nvidia_edgidahf" already active
INFO: Activating raid5_ls RAID set "nvidia_edgidahf"
NOTICE: discovering partitions on "nvidia_abgdcjdh"
NOTICE: /dev/mapper/nvidia_abgdcjdh: dos     discovering
NOTICE: discovering partitions on "nvidia_edgidahf"
NOTICE: /dev/mapper/nvidia_edgidahf: dos     discovering
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "nvidia_abgdcjdh"
DEBUG: freeing device "nvidia_abgdcjdh", path "/dev/sdd"
DEBUG: freeing device "nvidia_abgdcjdh", path "/dev/sde"
DEBUG: freeing devices of RAID set "nvidia_edgidahf"
DEBUG: freeing device "nvidia_edgidahf", path "/dev/sda"
DEBUG: freeing device "nvidia_edgidahf", path "/dev/sdb"
DEBUG: freeing device "nvidia_edgidahf", path "/dev/sdc"

So what am i missing  ? Worked with WDs & does not work with Samsungs ? 

Any help would be very appreciated!!!

---

