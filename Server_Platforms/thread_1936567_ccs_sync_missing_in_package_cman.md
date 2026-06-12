---
title: "ccs_sync missing in package cman"
date: 2012-03-06
forum: Server Platforms
---

### Post by Gehaktbal on 2012-03-06
To spread a new configuration in a cluster setup u need the application ccs_sync. The tool cman_tool uses it but it is not installed on the system and it seems that it is not in any of the ubuntu packages.

```

user@node2:~$ sudo cman_tool version -r 2
sh: /usr/bin/ccs_sync: not found
cman_tool: ccs_sync failed.
If you have distributed the config file yourself, try re-running with -S

```

The following tools ARE installed on the system
```

ccs_config_dump      ccs_test             
ccs_config_validate  ccs_tool  

```

My system is the following
```

user@node2:~$ uname -a
Linux node2 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux

```

Shouldn't this tool be a dependancy of the cman package? And if not where can I get it? If searched the packages and my system and it doesn't show up anywhere!?

---

### Post by Gehaktbal on 2012-03-06
It seems that the tool is available in the ricci package (fedora, centos) Why is this package not available for ubuntu? I can't find anything about it.


ricci - Remote Cluster and Storage Management System.
ricci is a cluster and storage management and configuration daemon. The ricci daemon, dispatches incoming messages to underlying management modules.
This package contains the listener daemon (dispatcher), as well as reboot, rpm, storage, service, virtual machine, and log management modules.
[LIST]
[*] Repository: Fedora for Fedora 16
[*] Download size: 606,92 KB
[*] Installed size: 606,92 KB
[*] Package filename: ricci-0.18.7-1.fc15.i686.rpm
[*] Source package: ricci-0.18.7-1.fc15.src.rpm
[/LIST]
```

Provides
config(ricci) = 0.18.7-1.fc15
ricci = 0.18.7-1.fc15
ricci(x86-32) = 0.18.7-1.fc15

```
Files
```

/etc/dbus-1/system.d/ricci-modlog.systembus.conf
/etc/dbus-1/system.d/ricci-modrpm.systembus.conf
/etc/dbus-1/system.d/ricci-modservice.systembus.conf
/etc/dbus-1/system.d/ricci-modstorage.systembus.conf
/etc/dbus-1/system.d/ricci-modvirt.systembus.conf
/etc/dbus-1/system.d/ricci.systembus.conf
/etc/oddjobd.conf.d/ricci-modlog.oddjob.conf
/etc/oddjobd.conf.d/ricci-modrpm.oddjob.conf
/etc/oddjobd.conf.d/ricci-modservice.oddjob.conf
/etc/oddjobd.conf.d/ricci-modstorage.oddjob.conf
/etc/oddjobd.conf.d/ricci-modvirt.oddjob.conf
/etc/oddjobd.conf.d/ricci.oddjob.conf
/etc/pam.d/ricci
/etc/rc.d/init.d/ricci
/usr/bin/ccs_sync
/usr/libexec/ricci-modlog
/usr/libexec/ricci-modrpm
/usr/libexec/ricci-modservice
/usr/libexec/ricci-modstorage
/usr/libexec/ricci-modvirt
/usr/libexec/ricci/
/usr/libexec/ricci/ricci-worker
/usr/sbin/ricci
/usr/share/doc/ricci-0.18.7/
/usr/share/doc/ricci-0.18.7/COPYING
/usr/share/doc/ricci-0.18.7/cluster_api.html
/usr/share/doc/ricci-0.18.7/logging_api.html
/usr/share/doc/ricci-0.18.7/modules.html
/usr/share/doc/ricci-0.18.7/modules_common.html
/usr/share/doc/ricci-0.18.7/reboot_api.html
/usr/share/doc/ricci-0.18.7/ricci_api.html
/usr/share/doc/ricci-0.18.7/rpm_api.html
/usr/share/doc/ricci-0.18.7/service_api.html
/usr/share/doc/ricci-0.18.7/storage-bd_template.html
/usr/share/doc/ricci-0.18.7/storage-bds.html
/usr/share/doc/ricci-0.18.7/storage-content.html
/usr/share/doc/ricci-0.18.7/storage-content_template.html
/usr/share/doc/ricci-0.18.7/storage-mapper_template.html
/usr/share/doc/ricci-0.18.7/storage-mappers.html
/usr/share/doc/ricci-0.18.7/storage_api.html
/usr/share/doc/ricci-0.18.7/variables.html
/usr/share/man/man8/ccs_sync.8.gz
/usr/share/man/man8/ricci.8.gz
/var/lib/ricci/
/var/lib/ricci/certs/
/var/lib/ricci/certs/cacert.config
/var/lib/ricci/certs/clients/
/var/lib/ricci/queue/

```

---

### Post by kevdog on 2012-03-07
Could you just compile from source?  Not an optimal solution.

---

### Post by Gehaktbal on 2012-03-07
> **kevdog said:**
> Could you just compile from source?  Not an optimal solution.

I could probably do that if i found an archive with the source in it? :)

---

