---
title: "Problem installing the KVM..."
date: 2011-07-19
forum: Server Platforms
---

### Post by huntkey on 2011-07-19
Hi guys,

I'm trying to install KVM on my Ubuntu 11.04. I was trying to follow the instruction on this link:
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

After the installation (and after a reboot), when I run this command I got the following error.
$ virsh -c qemu:///system list
error: cannot recv data: : Connection reset by peer
error: failed to connect to the hypervisor

[FONT=Arial][SIZE=2]I do have the libvirt-bin package installed and I do have the service running[/SIZE][/FONT]

$ sudo dpkg --list | grep libvirt-bin
ii  libvirt-bin                           0.8.8-1ubuntu6.2                           the programs for the libvirt library
$ sudo service libvirt-bin status
libvirt-bin start/running, process 6873

Then when I check my /var/log/syslog I'm spamed with these error logs and they keep repeating...

```

Jul 19 17:15:29 Ubuntu init: libvirt-bin main process (18145) terminated with status 1
Jul 19 17:15:29 Ubuntu init: libvirt-bin main process ended, respawning
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.421: 18207: info : libvirt version: 0.8.8
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.421: 18207: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -cpu ?) exited with status 1.
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -help) exited with status 1.
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : qemuCreateCapabilities:1046 : out of memory
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : virStateInitialize:795 : Initialization of QEMU state driver failed
Jul 19 17:15:30 Ubuntu kernel: [11120.071446] audit_printk_skb: 15 callbacks suppressed
Jul 19 17:15:30 Ubuntu kernel: [11120.071450] type=1400 audit(1311117330.412:27820): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18245 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu kernel: [11120.072959] type=1400 audit(1311117330.412:27821): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18246 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu kernel: [11120.074464] type=1400 audit(1311117330.412:27822): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18247 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18207: warning : lxcStartup:2128 : Unable to create cgroup for driver: No such device or address
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18207: error : main:3324 : Driver state initialization failed
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18208: warning : qemudDispatchSignalEvent:406 : Shutting down on signal 3
Jul 19 17:15:31 Ubuntu init: libvirt-bin main process (18207) terminated with status 1

(repeat again)

Jul 19 17:15:31 Ubuntu init: libvirt-bin main process ended, respawning
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.474: 18256: info : libvirt version: 0.8.8
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.474: 18256: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -cpu ?) exited with status 1.
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -help) exited with status 1.
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : qemuCreateCapabilities:1046 : out of memory
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : virStateInitialize:795 : Initialization of QEMU state driver failed
Jul 19 17:15:31 Ubuntu kernel: [11121.125198] type=1400 audit(1311117331.462:27823): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18294 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:31 Ubuntu kernel: [11121.126098] type=1400 audit(1311117331.462:27824): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18295 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:31 Ubuntu kernel: [11121.127009] type=1400 audit(1311117331.462:27825): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18296 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18256: warning : lxcStartup:2128 : Unable to create cgroup for driver: No such device or address
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18256: error : main:3324 : Driver state initialization failed
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18257: warning : qemudDispatchSignalEvent:406 : Shutting down on signal 3
Jul 19 17:15:32 Ubuntu init: libvirt-bin main process (18256) terminated with status 1
Jul 19 17:15:32 Ubuntu init: libvirt-bin main process ended, respawning


```Any ideas??
Thanks!

---

### Post by firsttimeuser on 2011-07-27
i have exact same problem, and i am considering to go back to 10.10 now

> **huntkey said:**
> Hi guys,



I'm trying to install KVM on my Ubuntu 11.04. I was trying to follow the instruction on this link:
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

After the installation (and after a reboot), when I run this command I got the following error.
$ virsh -c qemu:///system list
error: cannot recv data: : Connection reset by peer
error: failed to connect to the hypervisor

[FONT=Arial][SIZE=2]I do have the libvirt-bin package installed and I do have the service running[/SIZE][/FONT]

$ sudo dpkg --list | grep libvirt-bin
ii  libvirt-bin                           0.8.8-1ubuntu6.2                           the programs for the libvirt library
$ sudo service libvirt-bin status
libvirt-bin start/running, process 6873

Then when I check my /var/log/syslog I'm spamed with these error logs and they keep repeating...

```

Jul 19 17:15:29 Ubuntu init: libvirt-bin main process (18145) terminated with status 1
Jul 19 17:15:29 Ubuntu init: libvirt-bin main process ended, respawning
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.421: 18207: info : libvirt version: 0.8.8
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.421: 18207: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -cpu ?) exited with status 1.
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -help) exited with status 1.
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : qemuCreateCapabilities:1046 : out of memory
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.422: 18207: error : virStateInitialize:795 : Initialization of QEMU state driver failed
Jul 19 17:15:30 Ubuntu kernel: [11120.071446] audit_printk_skb: 15 callbacks suppressed
Jul 19 17:15:30 Ubuntu kernel: [11120.071450] type=1400 audit(1311117330.412:27820): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18245 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu kernel: [11120.072959] type=1400 audit(1311117330.412:27821): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18246 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu kernel: [11120.074464] type=1400 audit(1311117330.412:27822): apparmor="DENIED" operation="exec" parent=18207 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18247 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18207: warning : lxcStartup:2128 : Unable to create cgroup for driver: No such device or address
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18207: error : main:3324 : Driver state initialization failed
Jul 19 17:15:30 Ubuntu libvirtd: 17:15:30.868: 18208: warning : qemudDispatchSignalEvent:406 : Shutting down on signal 3
Jul 19 17:15:31 Ubuntu init: libvirt-bin main process (18207) terminated with status 1

(repeat again)

Jul 19 17:15:31 Ubuntu init: libvirt-bin main process ended, respawning
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.474: 18256: info : libvirt version: 0.8.8
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.474: 18256: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -cpu ?) exited with status 1.
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : virCommandWait:1229 : internal error Child process (LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin /usr/local/bin/qemu -help) exited with status 1.
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : qemuCreateCapabilities:1046 : out of memory
Jul 19 17:15:31 Ubuntu libvirtd: 17:15:31.475: 18256: error : virStateInitialize:795 : Initialization of QEMU state driver failed
Jul 19 17:15:31 Ubuntu kernel: [11121.125198] type=1400 audit(1311117331.462:27823): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18294 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:31 Ubuntu kernel: [11121.126098] type=1400 audit(1311117331.462:27824): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18295 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:31 Ubuntu kernel: [11121.127009] type=1400 audit(1311117331.462:27825): apparmor="DENIED" operation="exec" parent=18256 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=18296 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18256: warning : lxcStartup:2128 : Unable to create cgroup for driver: No such device or address
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18256: error : main:3324 : Driver state initialization failed
Jul 19 17:15:32 Ubuntu libvirtd: 17:15:32.018: 18257: warning : qemudDispatchSignalEvent:406 : Shutting down on signal 3
Jul 19 17:15:32 Ubuntu init: libvirt-bin main process (18256) terminated with status 1
Jul 19 17:15:32 Ubuntu init: libvirt-bin main process ended, respawning


```Any ideas??
Thanks!

---

