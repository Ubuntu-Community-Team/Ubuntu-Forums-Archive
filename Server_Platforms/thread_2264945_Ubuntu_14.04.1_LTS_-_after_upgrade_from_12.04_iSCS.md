---
title: "Ubuntu 14.04.1 LTS - after upgrade from 12.04 iSCSI no longer fully functional"
date: 2015-02-11
forum: Server Platforms
---

### Post by Joe_Jenkins on 2015-02-11
I have an Ubuntu 14.04.1 LTS server that I did a "do-release-upgrade" on from 12->13->Ubuntu 14.04.1 LTS

Since that upgrade I can no longer map iSCSI volumes to local SCSI devices. iSCSI appears to be working properly. The iSCSI target is a Buffalo TeraStation that worked fine in 12.04 / 12.10. There are no ACLs or any security on the volume I am trying to map / mount to my Ubuntu server. I have removed and --reinstall install open-iscsi, then removed it and compiled it from scratch, same results. 

Everything looks ok but I cannot mount / vgscan / access the volume whatsoever.

If anyone has any suggestions, I'd appreciate it! I'll keep digging and post any progress here. I think it might be a kernel / kernel module issue somewhere with iscsi.

Here is the output of various commands that hopefully illustrate the problem:

```

root@blackhole:~# cat /etc/issue
Ubuntu 14.04.1 LTS \n \l


root@blackhole:~# uname -a
Linux blackhole 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

root@blackhole:~# iscsiadm -m discovery -t st -p 192.168.10.20
192.168.10.20:3260,1 iqn.2004-08.jp.buffalo:Proxbackups-B0C74509088C:ProxBackups1
169.254.245.160:3260,1 iqn.2004-08.jp.buffalo:Proxbackups-B0C74509088C:ProxBackups1

root@blackhole:~# iscsiadm -m node --targetname iqn.2004-08.jp.buffalo:Proxbackups-B0C74509088C:ProxBackups1 --portal 192.168.10.20:3260 --login

root@blackhole:~#   iscsiadm -m session
tcp: [1] 192.168.10.20:3260,1 iqn.2004-08.jp.buffalo:Proxbackups-B0C74509088C:ProxBackups1

root@blackhole:~# dmesg | grep -i scsi
[    0.324896] SCSI subsystem initialized
[    0.726205] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    6.322377] scsi0 : Fusion MPT SAS Host
[    6.998441] scsi1 : ahci
[    6.998530] scsi2 : ahci
[    6.998610] scsi3 : ahci
[    6.998691] scsi4 : ahci
[    6.998773] scsi5 : ahci
[    6.998852] scsi6 : ahci
[   14.793829] scsi 0:0:0:0: Sequential-Access IBM      ULTRIUM-HH6      D8E5 PQ: 0 ANSI: 6
[   14.886056] scsi 0:0:0:0: SSP: handle(0x0009), sas_addr(0x500e09e0106dca10), phy(3), device_name(0x630705504b0a1012)
[   14.984024] scsi 0:0:0:0: SSP: enclosure_logical_id(0x5b083fe0c9fff700), slot(4)
[   15.083711] scsi 0:0:0:0: qdepth(254), tagged(1), simple(0), ordered(0), scsi_level(7), cmd_que(1)
[   15.190085] scsi 0:0:0:0: TLR Enabled
[   15.243187] scsi 0:0:0:0: Attached scsi generic sg0 type 1
[   15.294938] scsi 1:0:0:0: Direct-Access     ATA      ST9500620NS      n/a  PQ: 0 ANSI: 5
[   15.394648] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   15.548645] sd 1:0:0:0: [sda] Attached SCSI disk
[   15.815397] st 0:0:0:0: Attached scsi tape st0
[   27.087800] Loading iSCSI transport class v2.0-870.
[   27.170579] iscsi: registered transport (tcp)
[   27.346450] iscsi: registered transport (iser)
[   67.607950] scsi7 : iSCSI Initiator over TCP/IP

root@blackhole:~# lsscsi
[0:0:0:0]    tape    IBM      ULTRIUM-HH6      D8E5  /dev/st0
[1:0:0:0]    disk    ATA      ST9500620NS      n/a   /dev/sda

root@blackhole:~# iscsiadm -m session -P3
iSCSI Transport Class version 2.0-870
version 2.0-873
Target: iqn.2004-08.jp.buffalo:Proxbackups-B0C74509088C:ProxBackups1
    Current Portal: 192.168.10.20:3260,1
    Persistent Portal: 192.168.10.20:3260,1
        **********
        Interface:
        **********
        Iface Name: default
        Iface Transport: tcp
        Iface Initiatorname: iqn.2005-03.org.open-iscsi:4b1ce28aaf5
        Iface IPaddress: 192.168.10.15
        Iface HWaddress: <empty>
        Iface Netdev: <empty>
        SID: 1
        iSCSI Connection State: LOGGED IN
        iSCSI Session State: LOGGED_IN
        Internal iscsid Session State: NO CHANGE
        *********
        Timeouts:
        *********
        Recovery Timeout: 120
        Target Reset Timeout: 30
        LUN Reset Timeout: 30
        Abort Timeout: 15
        *****
        CHAP:
        *****
        username: <empty>
        password: ********
        username_in: <empty>
        password_in: ********
        ************************
        Negotiated iSCSI params:
        ************************
        HeaderDigest: None
        DataDigest: None
        MaxRecvDataSegmentLength: 262144
        MaxXmitDataSegmentLength: 8192
        FirstBurstLength: 65536
        MaxBurstLength: 262144
        ImmediateData: Yes
        InitialR2T: Yes
        MaxOutstandingR2T: 1
        ************************
        Attached SCSI devices:
        ************************
        Host Number: 7    State: running

```

---

### Post by Joe_Jenkins on 2015-02-11
Additional info - it looks like the system at least has some idea about the attached scsi device, but I still cannot mount it / vgscan / pvscan etc to access it.

```

root@blackhole:~# tree -d /sys/bus/scsi/devices/host7
/sys/bus/scsi/devices/host7
&#9500;&#9472;&#9472; iscsi_host
&#9474;   &#9492;&#9472;&#9472; host7
&#9474;       &#9500;&#9472;&#9472; device -> ../../../host7
&#9474;       &#9500;&#9472;&#9472; power
&#9474;       &#9492;&#9472;&#9472; subsystem -> ../../../../../class/iscsi_host
&#9500;&#9472;&#9472; power
&#9500;&#9472;&#9472; scsi_host
&#9474;   &#9492;&#9472;&#9472; host7
&#9474;       &#9500;&#9472;&#9472; device -> ../../../host7
&#9474;       &#9500;&#9472;&#9472; power
&#9474;       &#9492;&#9472;&#9472; subsystem -> ../../../../../class/scsi_host
&#9500;&#9472;&#9472; session1
&#9474;   &#9500;&#9472;&#9472; connection1:0
&#9474;   &#9474;   &#9500;&#9472;&#9472; iscsi_connection
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; connection1:0
&#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472; device -> ../../../connection1:0
&#9474;   &#9474;   &#9474;       &#9500;&#9472;&#9472; power
&#9474;   &#9474;   &#9474;       &#9492;&#9472;&#9472; subsystem -> ../../../../../../../class/iscsi_connection
&#9474;   &#9474;   &#9492;&#9472;&#9472; power
&#9474;   &#9500;&#9472;&#9472; iscsi_session
&#9474;   &#9474;   &#9492;&#9472;&#9472; session1
&#9474;   &#9474;       &#9500;&#9472;&#9472; device -> ../../../session1
&#9474;   &#9474;       &#9500;&#9472;&#9472; power
&#9474;   &#9474;       &#9492;&#9472;&#9472; subsystem -> ../../../../../../class/iscsi_session
&#9474;   &#9492;&#9472;&#9472; power
&#9492;&#9472;&#9472; subsystem -> ../../../bus/scsi

```

---

### Post by darkod on 2015-02-12
I couldn't understand if you can see it at all as /dev/sdX device or not? Is it /dev/sda from your posting? If the iscsi is sda does that mean you have no other local disks (not really relevant to iscsi)?

What does sudo parted /dev/sda print show?
Is the iscsi target working correctly from another computer on the same network? Have you tried accessing it?

---

