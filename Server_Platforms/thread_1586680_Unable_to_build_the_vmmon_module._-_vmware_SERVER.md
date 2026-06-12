---
title: "Unable to build the vmmon module. - vmware SERVER"
date: 2010-10-02
forum: Server Platforms
---

### Post by Marwelln on 2010-10-02
```

marwelln@ubuntu:/tmp$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet2                                          done
   NAT service on /dev/vmnet2                                          done
   Host-only networking on /dev/vmnet2                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-25-server/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Server 2.0.2 build 203138 detected. Building for Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.32-25-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-server'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:52:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:97:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.32-25-server/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.32-25-server/arch/x86/include/asm/smp.h:13,
                 from /usr/src/linux-headers-2.6.32-25-server/arch/x86/include/asm/mmzone_64.h:12,
                 from /usr/src/linux-headers-2.6.32-25-server/arch/x86/include/asm/mmzone.h:4,
                 from include/linux/mmzone.h:783,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:16:
/usr/src/linux-headers-2.6.32-25-server/arch/x86/include/asm/apicdef.h:136:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:107,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:273:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:277:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:345:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:351:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:404:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:450:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:495:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:539:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:584:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:628:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:673:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:717:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:719:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:760:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:804:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:806:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:847:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:889:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:891:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:930:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:972:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:974:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1013:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1167:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1171:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1257:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1470:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1597:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1730:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for âpoll_initwaitâ
include/linux/poll.h:70: note: previous declaration of âpoll_initwaitâ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:25,
                 from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:56:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:479:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:772:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:812:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:56:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:42:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:83:
/tmp/vmware-config0/vmmon-only/./common/hostif.h:39:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function âLinuxDriver_Openâ:
/tmp/vmware-config0/vmmon-only/linux/driver.c:575: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function â__LinuxDriver_Ioctlâ:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1495: error: âstruct task_structâ has no member named âsuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1496: error: âstruct task_structâ has no member named âcap_permittedâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1761: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1761: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1762: error: âstruct task_structâ has no member named âfsuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1762: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1763: error: âstruct task_structâ has no member named âegidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1763: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1764: error: âstruct task_structâ has no member named âfsgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1764: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config0/vmmon-only/linux/driver.c:1781: error: too many arguments to function âsmp_call_functionâ
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

Getting so ****ing tired of this. All solutions are for older kernel versions or desktop versions.

My kernel: 2.6.32-25-server

How can i fix this??

---

### Post by littlegreiger on 2010-10-02
Do you have the lastest header files for your kernel?
If you don't you can easily install them by running
```
sudo apt-get install linux-headers-`uname -r`
```
That will grab you the correct header files for your kernel and you should be able to compile the vmmon module. Unfortunately you'll have to run this every time you upgrade kernels.

---

### Post by Marwelln on 2010-10-02
Solution: Install VirtualBox

---

### Post by tercon91 on 2010-10-04
Hey Marwelln,
Don't give up just yet... :)
 
I got the exact same problem here. Manage to get it working after referring to this forum topic:
 
[https://help.ubuntu.com/community/VMware/Server#Ubuntu](https://help.ubuntu.com/community/VMware/Server#Ubuntu) 10.04 (VMware Server 2.0.x)
 
** Take note on the Section "Ubuntu 9.10 (VMWare Server 2.0.x)" **Point (2),** and Section "Ubuntu 9.04 (VMWare Server 2.0.1 Build 156745)" **Point (4) **and also "littlegreiger" addition about the linux-headers-X update and you should be good to go.

---

### Post by windependence on 2010-10-04
A much better solution would have been ESXi. It's free and bare metal. No OS to install at all.
 
-Tim

---

