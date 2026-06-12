---
title: "multipath not creating the /dev/mapping/mpath0 device"
date: 2010-05-28
forum: Server Platforms
---

### Post by ashleym1972 on 2010-05-28
Hello everyone,

I really need this problem solved ASAP. I'm trying to mount a multipath from my IBM blade to an IBM DS3400. Ubuntu 9.10.

:~$ sudo multipath -d
create: mpath0 (3600a0b8000687588000001f24bf48e4f)  IBM     ,1726-4xx  FASt
[size=1.1T][features=0][hwhandler=1 rdac]
\_ round-robin 0 [prio=3][undef]
 \_ 0:0:0:1 sda 8:0   [undef][ready]
\_ round-robin 0 [prio=0][undef]
 \_ 0:0:1:1 sdb 8:16  [undef][ghost]

:~$ more /etc/multipath.conf 
defaults {
    user_friendly_names yes
}
blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st)[0-9]*"
    devnode "^hd[a-z]"
    devnode "^sdc"
    devnode "^sdc[0-9]"
}
devices {
    device {
        vendor                  "IBM"
        product                 "1726-4xx"
#        getuid_callout        "/lib/udev/scsi_id --whitelisted --replace-whitespace --device=/block/%n"
        prio_callout            "/sbin/mpath_prio_rdac /dev/%n"    
        features        "0"
        hardware_handler    "1 rdac"
        path_grouping_policy    group_by_prio
        failback        immediate
        rr_weight        uniform
        no_path_retry        300
        rr_min_io        1000
        path_checker            rdac
    }
}
:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 01
  Vendor: IBM      Model: 1726-4xx  FAStT  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 00 Lun: 31
  Vendor: IBM      Model: Universal Xport  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 01
  Vendor: IBM      Model: 1726-4xx  FAStT  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 31
  Vendor: IBM      Model: Universal Xport  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: IBM      Model: 1726-4xx  FAStT  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 31
  Vendor: IBM      Model: Universal Xport  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 00
  Vendor: IBM      Model: 1726-4xx  FAStT  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 01 Lun: 31
  Vendor: IBM      Model: Universal Xport  Rev: 0617
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: IBM-ESXS Model: MBE2147RC        Rev: SC15
  Type:   Direct-Access                    ANSI  SCSI revision: 06
Host: scsi2 Channel: 00 Id: 01 Lun: 00
  Vendor: IBM-ESXS Model: ST9146852SS      Rev: B624
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 01 Id: 01 Lun: 00
  Vendor: LSILOGIC Model: Logical Volume   Rev: 3000
  Type:   Direct-Access                    ANSI  SCSI revision: 02


I'm seeing these errors in the syslog
May 28 09:39:59 plus-prod-db1 kernel: [51511.241685] device-mapper: table: 252:0: multipath: error getting device
May 28 09:39:59 plus-prod-db1 kernel: [51511.241724] device-mapper: ioctl: error adding target to table
May 28 09:39:59 plus-prod-db1 kernel: [51511.245703] device-mapper: table: 252:0: multipath: error getting device
May 28 09:39:59 plus-prod-db1 kernel: [51511.245743] device-mapper: ioctl: error adding target to table

---

