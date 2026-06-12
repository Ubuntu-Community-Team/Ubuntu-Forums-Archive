---
title: "Vmware server 2 on Server 9.10"
date: 2009-11-01
forum: Server Platforms
---

### Post by talsemgeest on 2009-11-01
Since Vmware server doesn't install in Ubuntu Server 9.10, due to an error when compiling one of the kernel modules (Im guessing caused by the newer version of GCC in Karmic?), I thought I had better ask if anyone has any information on how to get it working (if a solution exists) under 9.10? I will try to post the error, but I don't have had to stay with 9.04 server because of this.

Thanks for any info,

talsemgeest.

---

### Post by DDRBoxman on 2009-11-02
Same issue here, this is the error I get:

```
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function âLinuxDriverSyncCallOnEachCPUâ:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1423: error: too many arguments to function âsmp_call_functionâ
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âfsuidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âegidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âfsgidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config1/vmmon-only/linux/driver.c:2007: error: too many arguments to function âsmp_call_functionâ
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

```

---

### Post by madsen853 on 2009-11-04
I have exactly the same problem since I upgraded to Ubuntu 9.10.

---

### Post by mwjones on 2009-11-04
[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)

---

