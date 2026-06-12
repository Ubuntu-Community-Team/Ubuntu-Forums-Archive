---
title: "VMware tools installation fails on Ubuntu Lucid client at VMware Server 2.0.2"
date: 2010-06-04
forum: Virtualisation
---

### Post by bbruecker on 2010-06-04
I try to install the vmware tools (delivered from the linux.iso included in vmware server 2.0.2) following an this artkicle:
[https://help.ubuntu.com/community/VMware/Tools#Installing](https://help.ubuntu.com/community/VMware/Tools#Installing) VMware tools on Ubuntu/Kubuntu/Xubuntu Guests

Installation is no problem but vmware-config-tools.py-script fails and displays many errors. it seems to me, that the tools from the vmware server 2.0.2 and ubuntu 10.4 doesn't fix any more. I could reproduce this on an Windows-7/64-Bit host, Windows-xp-host, and an Ubuntu-10.4/64 host with freshly installed Ubuntu 10.4 64/32-bit server or Ubuntu 10.4 Desktop, 32 bit.

After starting /usr/bin/vmware-config-tools.pl-script the messages from the beginning seemed to me quite like a a problem:

```
Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 2 3 5 6) of script `vmware-tools' overwrites defaults (0 6).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and saned if stopped
insserv:  loop involving service saned at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and saned if stopped
insserv:  loop involving service bluetooth at depth 2
insserv: exiting now without changing boot order!
```

I don't understand the messages, but it seems to me that there is something wrong.

The script tries to build serveral modules. But not one of them could be build successfully. For example this one:

```

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-21-generic/build/include] 

Extracting the sources of the vmmemctl module.

Building the vmmemctl module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config2/vmmemctl-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-config2/vmmemctl-only/backdoorGcc32.o
In file included from /tmp/vmware-config2/vmmemctl-only/backdoor.h:29,
                 from /tmp/vmware-config2/vmmemctl-only/backdoorGcc32.c:45:
/tmp/vmware-config2/vmmemctl-only/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
  CC [M]  /tmp/vmware-config2/vmmemctl-only/os.o
In file included from /tmp/vmware-config2/vmmemctl-only/os.c:51:
/tmp/vmware-config2/vmmemctl-only/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
make[2]: *** [/tmp/vmware-config2/vmmemctl-only/os.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config2/vmmemctl-only] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.32-21-generic'
make: *** [[http://vmmemctl.ko|http://vmmemctl.ko]](http://vmmemctl.ko|http://vmmemctl.ko]) Fehler 2
make: Verlasse Verzeichnis '/tmp/vmware-config2/vmmemctl-only'
Unable to build the vmmemctl module.

The memory manager driver (vmmemctl module) is used by VMware host software to 
efficiently reclaim memory from a virtual machine.
If the driver is not available, VMware host software may instead need to swap 
guest memory to disk, which may reduce performance.
The rest of the software provided by VMware Tools is designed to work 
independently of this feature.

```

The message "unable to build..." is clear. And this continues for every other modul:
* vmmemctl
* vmhgfs-only
* vmxnet (with some other errors)
* vmblock
* vmci (with some other errors)

What is wrong? Would be very nice, if somebody please help me. I want the tools badly.

Benjamin

---

### Post by bribera on 2010-06-22
VMware's kernel modules are built for a slightly older version of the Linux kernel than the one that Lucid uses. There are a few minor pieces of incompatibility with the newer 2.6.32 version that cause compilation to fail. You can apply an unofficial patch to the module source files prior to compilation, and that will make things work. 

Note that if you're running a 64-bit install, you'll want to download the 64-bit version of VMware instead of the 32-bit one that tutorial links to. I can verify that these instructions work with the 64-bit version.

Follow the instructions here: [http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/](http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/)

---

### Post by nethershaw on 2010-07-07
> **bribera said:**
> VMware's kernel modules are built for a slightly older version of the Linux kernel than the one that Lucid uses.

Would you kindly tell us what, exactly, that version of the Linux kernel was?

---

### Post by bribera on 2010-07-07
The highest kernel version I find reference to in the 2.0.2 distribution is...

```
brendan@pequod:~/src/vmware-server-distrib$ ack-grep '2\.6\.' . | grep -o '2\.6\.[0-9]*' | sort | uniq
[snip]
**2.6.27**
[snip]

```

Unfortunately, I can't find an officially supported *kernel* version listed anywhere -- [VMWare's Server 2 manual]("http://www.vmware.com/products/beta/vmware_server/vmserver2.pdf") (PDF!) specifies several supported distributions and versions:


> 64&#8208;bit host computers can run the following operating systems for 64&#8208;bit extended 
systems:
[LIST]
[*]Mandriva Corporate Server 4
[*]Red Hat Enterprise Linux 5.1
[*]Red Hat Enterprise Linux 5.0
[*]Red Hat Enterprise Linux AS 4.5
[*]Red Hat Enterprise Linux ES 4.5
[*]Red Hat Enterprise Linux WS 4.5
[*]SUSE Linux Enterprise Server 10.1
[*]SUSE Linux Enterprise Server 10 SP1
[*]SUSE Linux Enterprise Server 10
[*]SUSE Linux Enterprise Server 9 SP4
[*]Ubuntu Linux 8.04
[*]Ubuntu Linux 7.10
[*]Ubuntu Linux 7.04
[*]Ubuntu Linux 6.10 
[*]Ubuntu Linux 6.06
[/LIST]

32&#8208;bit host computers can run the following operating systems:
[LIST]
[*]Mandrake Linux 10.1
[*]Mandriva Corporate Server 4
[*]Red Hat Enterprise Linux 5.1
[*]Red Hat Enterprise Linux 5.0
[*]Red Hat Enterprise Linux AS 4.5
[*]Red Hat Enterprise Linux ES 4.5
[*]Red Hat Enterprise Linux WS 4.5
[*]SUSE Linux Enterprise Server 10.1
[*]SUSE Linux Enterprise Server 10 SP1
[*]SUSE Linux Enterprise Server 10
[*]SUSE Linux Enterprise Server 9 SP4
[*]TurboLinux Enterprise Server 10
[*]Ubuntu Linux 8.04
[*]Ubuntu Linux 7.10
[*]Ubuntu Linux 7.04
[*]Ubuntu Linux 6.10
[*]Ubuntu Linux 6.06
[/LIST]

This doesn't necessarily mean that newer kernels or distribution releases won't work. All that to say, I don't know at precisely which version compilation was broken.

---

