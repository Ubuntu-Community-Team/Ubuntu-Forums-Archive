---
title: "Mount point order change on server reboot - Ubuntu 14.04.1 LTS"
date: 2015-07-10
forum: Server Platforms
---

### Post by Loz_Bigrave on 2015-07-10
Hi all. I am running several of these servers as Virtual machines with VMware ESXi5.5 as the hypervisor. I monitor the servers disk and memory usage by snmp and produce monthly reports on this. I find, however, that if a server reboots its mount points change order, and therefore messes up my reports.

I have tried using 'noauto' in fstab, to not allow the system to mount disks and use a manual script, but the same thing happens. 

Mount order:
/dev/sda on disk1
/dev/sdd1 on disk2
/dev/sdc1 on disk3
/dev/sdb1 on disk4

after boot..
/dev/sdd1 on disk2
/dev/sdc1 on disk3
/dev/sdb1 on disk4
/dev/sda on disk1

So after reboot my snmp poller and the web server in squirts data into thinks that disk 2 is disk 1, disk 3 is disk 2 etc.

---

### Post by darkod on 2015-07-10
Do you rely on using /dev/sdX in your work or you only need a certain device to mount at certain mount point and afterwards you use the mount point?

If the latter, there is an easy fix. In /etc/fstab use UUIDs instead of /dev/sdX and a specific partition will always mount at the correct point.

If that is not enough for you, look at vmware/VM settings too. The letters in /dev/sdX are usually assigned by bios/port order. In virtual world, make sure vmware presents the disks always in the same order (first, second, etc) and ubuntu should detect them as such.

The uuid way is preferred as long as you only care the mounting to be correct. But if you also use the disks as /dev/sdX then that is not enough.

---

### Post by Loz_Bigrave on 2015-07-10
Thanks for replying. I have tried UUID method - same result. Will look at your other comments.

---

### Post by frits-b on 2015-10-02
I guess you are using a [FONT=courier new]includeAllDisks[/FONT] statement in [FONT=courier new]/etc/snmp/snmpd.conf[/FONT].
This seems to iterate mount points on different OID's upon each reboot, very annoying when monitored using cacti or Nagios or what you are using.
I would suggest removing the [FONT=courier new]includeAllDisks [/FONT]and using a [FONT=courier new]disk[/FONT] config line for each mount point you want monitored.
Like this:
[FONT=courier new]disk      /         5%
disk      /var     10%
disk      /home     5%
[FONT=arial]The mount points I define this way seem to keep the same OID through reboots.
BTW. reload the snmpd service to pick up the changes.[/FONT][/FONT]

---

### Post by cariboo on 2015-10-02
> **frits-b said:**
> I guess you are using a [FONT=courier new]includeAllDisks[/FONT] statement in [FONT=courier new]/etc/snmp/snmpd.conf[/FONT].
This seems to iterate mount points on different OID's upon each reboot, very annoying when monitored using cacti or Nagios or what you are using.
I would suggest removing the [FONT=courier new]includeAllDisks [/FONT]and using a [FONT=courier new]disk[/FONT] config line for each mount point you want monitored.
Like this:
[FONT=courier new]disk      /         5%
disk      /var     10%
disk      /home     5%
[FONT=arial]The mount points I define this way seem to keep the same OID through reboots.
BTW. reload the snmpd service to pick up the changes.[/FONT][/FONT]

This really has nothing to do with what the op asked, he had a problem with multiple disks changing order after a reboot, to cure the problem, use UUID instead of the device name to mount the disks, using something like this:


```
#/dev/sdd1 mounted as documents
UUID=6f1f0afb-8cfe-4d7b-9ba9-15d42c37c4ab	/media/documents	xfs	defaults	0	2
```

---

