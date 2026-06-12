---
title: "dm-multipath / multipath-tools trouble on 8.04"
date: 2008-07-01
forum: Server Platforms
---

### Post by mernisse on 2008-07-01
We are looking to migrate a large application at work onto Ubuntu server 8.04 but are having troubles getting dm-multipath to function.

The general layout is a fairly standard multipath fiber channel setup.  4x NetApp FAS3070c storage arrays in clustered pair, each with 1 FC connection to one each of a pair of Cisco 9124 SAN switches.  My test client is an IBM x330 attached directly to the 9124s with a dual-port Qlogic 2312 PCI-X HBA.

This is a fresh install of 8.04, with nothing else on it on a 36G LUN exported on one of the clusters.  At boot the lun shows up as /dev/sd[a-d].  I installed onto /dev/sda from the -server CD.

I am running kernel 2.6.24-19-server and multipath-tools 0.4.8-7ubuntu2.

My multipath.conf at this point:

```

defaults {
	path_checker	tur
}

multipaths {
	multipath {
		wwid		360a98000486e5770584a4a3944577365
		alias		netapp
	}
}

devices {
	device {
		vendor			"NETAPP  "
		product			"LUN "
	}
}


```

multipath -d outputs:
```

create: netapp (360a98000486e5770584a4a3944577365)  NETAPP  ,LUN           
[size=36G][features=0][hwhandler=0]
\_ round-robin 0 [prio=1][undef]
 \_ 1:0:0:0 sda 8:0   [undef][ready]
\_ round-robin 0 [prio=1][undef]
 \_ 1:0:1:0 sdb 8:16  [undef][ready]
\_ round-robin 0 [prio=1][undef]
 \_ 4:0:0:0 sdc 8:32  [undef][ready]
\_ round-robin 0 [prio=1][undef]
 \_ 4:0:1:0 sdd 8:48  [undef][ready]

```

This seems to indicate after some googling that the dm layer is in an unknown state.  When multipathd starts at boot, the following is emitted to the kernel log ringbuffer:

```

[   97.196268] device-mapper: uevent: version 1.0.3
[   97.196360] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   97.223509] device-mapper: multipath: version 1.0.5 loaded
[   97.688328] device-mapper: multipath round-robin: version 1.0.0 loaded
[   97.697552] device-mapper: table: 254:0: multipath: error getting device
[   97.697620] device-mapper: ioctl: error adding target to table
[   97.701790] device-mapper: table: 254:0: multipath: error getting device
[   97.701866] device-mapper: ioctl: error adding target to table
[   97.705501] device-mapper: table: 254:0: multipath: error getting device
[   97.705587] device-mapper: ioctl: error adding target to table
[   97.709331] device-mapper: table: 254:0: multipath: error getting device
[   97.709402] device-mapper: ioctl: error adding target to table
[   97.726491] device-mapper: table: 254:0: multipath: error getting device
[   97.726562] device-mapper: ioctl: error adding target to table
[   97.732499] device-mapper: table: 254:0: multipath: error getting device
[   97.732572] device-mapper: ioctl: error adding target to table
[   97.743522] device-mapper: table: 254:0: multipath: error getting device
[   97.743598] device-mapper: ioctl: error adding target to table
[   97.761402] device-mapper: table: 254:0: multipath: error getting device
[   97.761480] device-mapper: ioctl: error adding target to table
[   97.773240] device-mapper: table: 254:0: multipath: error getting device
[   97.773309] device-mapper: ioctl: error adding target to table
[   97.836975] device-mapper: table: 254:0: multipath: error getting device
[   97.837052] device-mapper: ioctl: error adding target to table
[   97.848610] device-mapper: table: 254:0: multipath: error getting device
[   97.848684] device-mapper: ioctl: error adding target to table
[   97.859221] device-mapper: table: 254:0: multipath: error getting device
[   97.859292] device-mapper: ioctl: error adding target to table
[   97.874788] device-mapper: table: 254:0: multipath: error getting device
[   97.874860] device-mapper: ioctl: error adding target to table
[   97.968836] device-mapper: table: 254:0: multipath: error getting device
[   97.968852] device-mapper: ioctl: error adding target to table
[   97.992795] device-mapper: table: 254:0: multipath: error getting device
[   97.992810] device-mapper: ioctl: error adding target to table
[   98.011870] device-mapper: table: 254:0: multipath: error getting device
[   98.011937] device-mapper: ioctl: error adding target to table
[   98.037471] device-mapper: table: 254:0: multipath: error getting device
[   98.037539] device-mapper: ioctl: error adding target to table

```

If I try to load the multipath map manually (eg: sudo multipath -v2) the program emits no output, but more lines like above (the table: and ioctl: lines) are output to the kernel log.  

multipath -ll outputs nothing, there are no device-mapper devices registered to the system (no nodes in /dev/mapper other than control, nothing listed in dmsetup list)

The only mention of this kind of error that I find is for something back in Dapper/Feisty era telling to remove evms.  This system has never had evms installed on it.

I would be thrilled at any assistance anyone could offer, there isn't much google could offer about dm-multipath on ubuntu, or dm-multipath in general.  It seems to just work for most people.

---

### Post by RollMeDice on 2008-12-12
Hi,
I am experiencing this same problem on a debian server. My symptoms are exactly the same. I use open-iscsi to connect a target, which works perfectly, I currently mount the discovered device via its label but would like to mount it through multipath. however /dev/mapper is empty except for control. Multipath outputs:
```
device-mapper: multipath round-robin: version 1.0.0 loaded
device-mapper: table: 254:0: multipath: error getting device
device-mapper: ioctl: error adding target to table
```
just after open-iscsi outputs:
```
iscsi: registered transport (iser)
scsi1 : iSCSI Initiator over TCP/IP
scsi2 : iSCSI Initiator over TCP/IP
scsi 1:0:0:0: Direct-Access     iSCSI    DISK             0    PQ: 0 ANSI: 4
sd 1:0:0:0: [sdb] 314386432 512-byte hardware sectors (160966 MB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 77 00 00 08
sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 1:0:0:0: [sdb] 314386432 512-byte hardware sectors (160966 MB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 77 00 00 08
sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1
sd 1:0:0:0: [sdb] Attached SCSI disk
scsi 2:0:0:0: Direct-Access     iSCSI    DISK             0    PQ: 0 ANSI: 4
sd 2:0:0:0: [sdc] 314386432 512-byte hardware sectors (160966 MB)
sd 2:0:0:0: [sdc] Write Protect is off
sd 2:0:0:0: [sdc] Mode Sense: 77 00 00 08
sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 2:0:0:0: [sdc] 314386432 512-byte hardware sectors (160966 MB)
sd 2:0:0:0: [sdc] Write Protect is off
sd 2:0:0:0: [sdc] Mode Sense: 77 00 00 08
sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
 sdc: sdc1
sd 2:0:0:0: [sdc] Attached SCSI disk

```

Googling for this problem seems to point to evms as the OP stated, however evms has never lived on this server.

Does anyone have any clues on where to look for a solution?

Kind Regards,
Dice

---

### Post by RollMeDice on 2008-12-13
After some searching I found that the problem (at least for me) is caused by the storage on which my iscsi targets live.
Apparently the disks were not supplied with a unique serial number. Running sginfo -a against any of the disks returned the same information:
```
INQUIRY response (cmd: 0x12)
----------------------------
Device Type                        0
Vendor:                    iSCSI   
Product:                   DISK            
Revision level:            0   

Serial Number '    '
```

After resolving this issue with the storage everything worked fine.
Hope this helps anyone.

Dice

ps: sginfo wasn't installed on my system, it's part of the sg3-utils package.

---

### Post by brianfinley on 2009-02-06
Me too.

I'm experiencing the exact same issue.  2x QLogic Fibre channel cards, and NEXSAN SATABeast as the target.  One 500G volume.

I am using dm-multipath on CentOS before with great success, but Ubuntu is our standard OS, and I'd really like to get this working properly under Hardy.

---

### Post by brianfinley on 2009-04-15
**Implementing on Ubuntu Hardy**

**multipath-tools**
First, make sure the multipath-tools package is installed:
```

sudo aptitude install multipath-tools

```

Then take a look at the config before making any changes:
```

sudo mutipath -ll

```

Make our local changes.  A simple '''/etc/multipath.conf''' file that should do the trick:
```

# Don't include blacklisted devices when creating multipaths
devnode_blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
    devnode "^hd[a-z][[0-9]*]"
    devnode "^cciss!c[0-9]d[0-9]*[p[0-9]*]"

    # also blacklist local SAS disks on our Sun boxes -BEF-
    device {
        vendor = FUJITSU.*
        product = MAY2073RCSUN72G
    }
    device {
        vendor = HITACHI.*
        product = H101414SCSUN146G
    }
}

defaults {
    path_grouping_policy    multibus
    failback                immediate
    polling_interval 5
}

#
# As new volumes get added, they can be named.
#
multipaths {
    multipath {
        wwid    36000402001fc4151615fb5ae00000000
        alias   satabeast4vol1
    }
}

```


Then restart the daemon, and take another look at the config in use:
```

sudo /etc/init.d/multipath-tools restart
sudo mutipath -ll

```

**LVM**
The default LVM config on most linuxes, including Ubuntu Hardy, is to scan all available block devices for LVM signatures to see if they are a PV (Physical Volume).  Once multipathing is configured, LVM will now find a signature on a) the device file representing the singular multipathed device and b) the device files representing each of the paths to the volume in question (Ie.: /dev/sdd, /dev/sde, and /dev/mapper/multipath_volume_made_from_sdd_and_sde).

In the example above, all of the device files represent the same volume, and will all have the same PV signature.  Therefore, LVM may choose to use any one of them to access the volume.  This may appear to work fine, except in a fail event.  If LVM is using one of the non-multipathed device files, then it has effectively by-passed the multipath driver, rendering it useless in a fail event.

Therefore, we need to tell LVM to disregard the non-multipathed device files.  On Ubuntu, we've found that the best way to ensure this is to explicitly include multipathed devices, and other devices we want LVM to use, and to exclude everything else.

Edit /etc/lvm/lvm.conf and find the entry that looks like this:
```

    # By default we accept every block device:
    filter = [ "a/.*/" ]

```

and comment it out.  Then explicitly add _only_ the devices we know we want to see.  In this example, we want to see software RAID devices (/dev/md*) and specific multipath devices (in this case, a volume from SATABeast4), and remove everything else:
```

    ## By default we accept every block device:
    #filter = [ "a/.*/" ]

    # Explicitly add deviced we want to the beginning of this filter. -BEF-
    filter = [ "a|^/dev/md.$|", "a|^/dev/mapper/satabeast4vol1$|", "r/.*/" ]

```

'''WARNING:''' Although it appears from the config file that you can combine filters on multiple lines, you cannot.  You may only have one filter line that includes everything.

**QLogic Driver**
To compliment the multipath-tools configuration, create a file called '''/etc/modprobe.d/qla2xxx''' with the following contents.  This tells the qlogic driver to failover immediately (no lag) if a cable is pulled or cut:
```

options qla2xxx qlport_down_retry=1

```

After creating this file, it is necessary to re-build the initrd so that these settings take effect when the driver is first loaded:
```

ver=$(uname -r)
sudo mkinitramfs -o /boot/initrd.img-$ver $ver

```

After rebooting with the new initrd, you should see the new setting reflected here:
```

$ cat /sys/module/qla2xxx/parameters/qlport_down_retry
1

```

---

### Post by ntenzpunishment on 2009-04-15
Hi Brian,

Appreciate the time you took to explain how to solve this issue. I will try it tomorrow - hopefully it will work otherwise we are forced to use centOS.

Are you using 8.04 /QLogic/multipath in a production environment?
Has there been any issues?
Do you think the same procedure will work on 9.04?
btw we are using netapp.

Kind regards,

ntenz

---

