---
title: "Unable to start services. VMware"
date: 2012-05-06
forum: Virtualisation
---

### Post by netkd on 2012-05-06
Hello,
Help Please.

```
Unable to start services.
See log file /tmp/vmware-root/modconfig-10645.log for details.

```log
```
2012-05-06T21:05:05.304+02:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-06T21:05:05.304+02:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-06T21:05:05.311+02:00| vthread-3| I120: Your GCC version: 4.6
2012-05-06T21:05:05.338+02:00| vthread-3| I120: Your GCC version: 4.6
2012-05-06T21:05:05.413+02:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-06T21:05:05.413+02:00| vthread-3| I120: Building module vmci.
2012-05-06T21:05:05.413+02:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-06T21:05:05.449+02:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-ge$
2012-05-06T21:05:06.883+02:00| vthread-3| I120: Building module vsock.
2012-05-06T21:05:06.883+02:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-06T21:05:06.917+02:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-g$
2012-05-06T21:05:19.522+02:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-24-generic/misc.
2012-05-06T21:05:19.523+02:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-24-generic/misc/vsock.ko
```uname -a
```
root@root:/# uname -a
Linux root 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

VMware-Workstation-Full-8.0.3-703057.x86_64.bundle

---

### Post by hasan.akgoz on 2012-05-06
let's give me syslog output.

---

### Post by netkd on 2012-05-07
solved. n.p 

[http://communities.vmware.com/message/2039055#2039055](http://communities.vmware.com/message/2039055#2039055) 
check.

---

### Post by dcstar on 2012-05-08
> **netkd said:**
> solved. n.p 


Then **MARK** the thread!

---

