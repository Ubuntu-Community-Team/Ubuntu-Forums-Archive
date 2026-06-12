---
title: "Multipath Fibre Channel SAN problems"
date: 2010-11-11
forum: Server Platforms
---

### Post by martin@cabo.dk on 2010-11-11
Hi,

I have a server installed with Ubuntu 10.04LTS connected to a SAN via a qlogic HBA with two ports.

I have two LUNs mapped to this server and have installed multipath-tools with the following configuration:

```

defaults {
         failback            immediate
         user_friendly_names yes
}

devices {
        device {
               vendor        IBM
               product       "1815      FASt"
               hardware_handler        "1 rdac"
               path_checker            rdac
        }
}

multipaths {
           multipath {
                     wwid 3600a0b8000116360000083304cd9efa5
                     alias valve002-test2
                     }
           multipath {
                     wwid 3600a0b800011a00600001c204cda05cf
                     alias valve002-test1
                     }

}

```This seems to work fine under normal operation aside from some issues during boot:

```

[    2.569468] sd 4:0:1:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    2.569475] sd 4:0:1:1: [sdc] Sense Key : Illegal Request [current]
[    2.569481] sd 4:0:1:1: [sdc] <<vendor>> ASC=0x94 ASCQ=0x1ASC=0x94 ASCQ=0x1
[    2.569490] sd 4:0:1:1: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    2.569501] end_request: I/O error, dev sdc, sector 0
[    2.569505] Buffer I/O error on device sdc, logical block 0
[    2.569539] sd 4:0:1:2: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    2.569544] sd 4:0:1:2: [sdd] Sense Key : Illegal Request [current]
[    2.569548] sd 4:0:1:2: [sdd] <<vendor>> ASC=0x94 ASCQ=0x1ASC=0x94 ASCQ=0x1
[    2.569555] sd 4:0:1:2: [sdd] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[    2.569565] end_request: I/O error, dev sdd, sector 0
[    2.569568] Buffer I/O error on device sdd, logical block 0

```And another issue I have which is that the local disk is named sdi because the qlogic driver seems to take precedence over the local raid-controller. Is there any way to force the local drive to be persistently named /dev/sda? This is not a big issue since LVM catches the PV on /dev/sdi during boot and thus the system works.

My topology looks like follows:

```

# multipath -d -l
valve002-test2 (3600a0b8000116360000083304cd9efa5) dm-4 IBM     ,1815      FASt
[size=25G][features=0][hwhandler=1 rdac]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:0:2 sdg 8:160 [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:0:2 sdb 8:16  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:1:2 sdd 8:48  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:1:2 sde 8:192 [active][undef]
valve002-test1 (3600a0b800011a00600001c204cda05cf) dm-3 IBM     ,1815      FASt
[size=20G][features=0][hwhandler=1 rdac]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:1:1 sdf 8:176 [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:0:1 sda 8:0   [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:1:1 sdc 8:32  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:0:1 sdh 8:144 [active][undef]

```The real issue comes when I test the multipathing by yanking one of the connections from the server some time passes and I get a few I/O errors but the system survives. Good enough.. But when I re-insert the connection and I get redundant connections again, the system doesn't reuse the previous device nodes. Instead it creates new ones which makes the topology look like this:

```

# multipath -d -l
valve002-test2 (3600a0b8000116360000083304cd9efa5) dm-4 IBM     ,1815      FASt
[size=25G][features=0][hwhandler=1 rdac]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:0:2 sdk 8:160 [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:0:2 sdb 8:16  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:1:2 sdd 8:48  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:1:2 sdm 8:192 [active][undef]
valve002-test1 (3600a0b800011a00600001c204cda05cf) dm-3 IBM     ,1815      FASt
[size=20G][features=0][hwhandler=1 rdac]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:1:1 sdl 8:176 [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:0:1 sda 8:0   [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 4:0:1:1 sdc 8:32  [active][undef]
\_ round-robin 0 [prio=0][enabled]
 \_ 6:0:0:1 sdj 8:144 [active][undef]

```And then multipathd starts complaining every 30 seconds about the connections that will never come back:

```

Nov 11 14:00:32 valve002 multipathd: sdh: rdac checker reports path is down
Nov 11 14:00:37 valve002 multipathd: sde: rdac checker reports path is down
Nov 11 14:00:37 valve002 multipathd: sdf: rdac checker reports path is down
Nov 11 14:00:37 valve002 multipathd: sdg: rdac checker reports path is down
Nov 11 14:00:37 valve002 multipathd: sdh: rdac checker reports path is down

```It seems to me that the main issue here is device node naming persistency. However, I've not been able to find others with the same problems. Certainly, I can't be the only one having an Ubuntu server connected to a SAN? :)

Regards from,
Martin Dalum

---

### Post by Vegan on 2010-11-11
Looks like a clash between the local RAID and the SAN.

Usually SAN resources are used by supercomputers where they lack local storage and rely on the HBA for storage etc.

---

### Post by martin@cabo.dk on 2010-11-11
Hi,

> **Vegan said:**
> Looks like a clash between the local RAID and the SAN.

The issue about the local raid vs. the LUNs from my SAN is my smallest issue. I can live with the fact that my local disk is named /dev/sdi - that's just cosmetic. My real issue is that the device nodes for the SAN LUNs change every time there's a path loss. Just after boot the 8 device nodes for my 4 paths to two different LUNs are named sda -> sdg. After a path failure/recovery they're suddenly taking sdj -> sdm also while multipathd keeps complaining about the initial (now lost) device nodes.

> Usually SAN resources are used by supercomputers where they lack local storage and rely on the HBA for storage etc.I've seen very few systems that boot from SAN. It seems much more common that a system boots from local disks and keeps its application data on SAN LUNs.

Regards from,
Martin Dalum

---

### Post by dnaand on 2011-02-18
Hi Martin,

In order to have your LUNs mapped to persistent name across reboots and fail overs you will need to add an entry to your udev rules. Have a google on this or alternatively have a look in the RHEL administration guide docs - there is some good examples and info in there.

To prevent multipath from scanning your DAS you will need to add something like the following in your multipath config file:

devnode_blacklist {[INDENT]devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
devnode "^cciss!c[0-9]d[0-9]*"
devnode "^hd[a-z]*"
[/INDENT]}

Note the "^cciss...blah" is specific to my HP server... the local raid controller shows up as cciss. Again there is pretty good info and examples in the RHEL doc set.

Good luck

---

