---
title: "VMware server 2.0.2 on Ubuntu 10.04 having an epic failure"
date: 2010-07-20
forum: Virtualisation
---

### Post by lackskill on 2010-07-20
Preface:  I'm a linux n00b.  I've been fumbling through Ubuntu and Mandriva for a few months now, but the more I learn the more I realize how little I know.  I apologize if this is a general failure between the keyboard and chair, but I have been beating myself over the head about this for almost 2 days now, scouring google, several forums, and RTFMing with no success.

Background:  I had Ubuntu 9.10 running (not well, but running), upgraded to 10.04 (still running, but still not well), had VMware server 2.0.2 installed with Ubuntu 9.10 server and I was successfully using that as a testing environment for my webserver.  I managed to completely hose my Ubuntu 10.04 install so I decided to wipe the drive and start over from scratch.

So at that point I'm starting from a fresh install of Ubuntu 10.04 and it's running stable (best it's been since I started playing with Linux) so I install VMware server again, using the 3rd party script/patch that's needed to make VMwS work on the newer kernels.  I have my data store on a separate disk than my OS so the datastore was still in tact with my 9.10 server VM install.  The VMwS install appeared to be successful so I imported the vm and started trying to connect to the webserver.  I couldn't seem to get my testing environment running even though the VM seemed to be running ok so I tried changing from bridged to NAT and back, none of which worked.  So then I wanted to see if my router was registering a connection from the VM in bridged mode but I'm using a god forsaken Apple Airport Extreme.  I don't have a windows install currently and I sold my mac ages ago so I decided I would install an XP Pro vm and try that out.  I had a couple freezes during the install, but it eventually worked.  I was able to get online and download the airport utility, but it requires SP3, so I had to run windows update.  I ran the first round of updates, which was just the updated windows installer, and changed the resolution to 1024x768 so that web pages fit better and then I had to reboot the vm to complete that round of updates.  And this is where it goes completely sideways on me...

When the vm tries to restart it just hangs.  I recognize that it's hung so I log out of the web interface and use /etc/init.d/vmware restart.  I got a failure on "Virtual ethernet", so I decided to reboot the machine entirely.  When I open the web interface again and try to power on either VM at this point I get an error that says "Could not open /dev/vmmon: No such file or directory. Please make sure that the kernel module `vmmon' is loaded." and sure enough /dev/vmmon does not exist.  

So at this point I'm really doing a lot more reading than trying because I haven't the slightest as to what's wrong.  I don't ever really find anyone with the same problem that has fixed it and with no other conclusive data I decided to try to reconfigure.  So I tried running the config script and it just errored out.  Getting frustrated I decided to reinstall so I went sudo vmware-uninstall.pl which tells me it completes successfully and then I initiate the install again using the 3rd party script.  All goes well.  Apparently.

So I log back into the web interface again and my datastore with my configured VMs is still there, which seems a little fishy to me.  So I try to power on a VM and now the error has changed.  It now reads "Failed to power on: a general system error occurred".  So I delete that XP Pro vm completely and decide to start over with a new XP Pro vm.  Same error.  Now I've uninstalled again.  I get a ton of errors (they seem like errors to me) here's the output:

```
lackskill@lackskill:~$ sudo vmware-uninstall.pl
[sudo] password for lackskill: 
Uninstalling the tar installation of VMware Server.

Checking for active VMs:
There are no Active VMs.
Stopping services for VMware Server

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop VMware Server's services.

insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gssd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-core: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'smbd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: script vmware-mgmt: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rpc_pipefs' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'portmap' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'idmapd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'statd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and portmap if stopped
insserv:  loop involving service portmap at depth 4
insserv:  loop involving service nfs-kernel-server at depth 3
insserv: There is a loop between service nfs-kernel-server and rsyslog if stopped
insserv:  loop involving service rsyslog at depth 5
insserv:  loop involving service hwclock at depth 4
insserv: There is a loop between service portmap and nfs-kernel-server if stopped
insserv: exiting now without changing boot order!
File 
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/conf/tomcat-users.xml is 
backed up to 
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/conf/tomcat-users.xml.old.0.


This program previously created the directory 
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/conf, and was about to 
remove it. Since there are files in that directory that this program did not 
create, it will not be removed.

This program previously created the directory 
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16, and was about to remove 
it. Since there are files in that directory that this program did not create, 
it will not be removed.

This program previously created the directory /usr/lib/vmware/webAccess/tomcat,
and was about to remove it. Since there are files in that directory that this 
program did not create, it will not be removed.

This program previously created the directory /usr/lib/vmware/webAccess, and 
was about to remove it. Since there are files in that directory that this 
program did not create, it will not be removed.

This program previously created the directory /usr/lib/vmware, and was about to
remove it. Since there are files in that directory that this program did not 
create, it will not be removed.

This program previously created the directory /etc/vmware, and was about to 
remove it. Since there are files in that directory that this program did not 
create, it will not be removed.

The removal of VMware Server 2.0.2 build-203138 for Linux completed 
successfully.  Thank you for having tried this software.
```That's where I stand at the moment.  I greatly appreciate any help anyone can give me.  Thanks.

Ryan

---

### Post by lackskill on 2010-07-20
Here's the output of my attempt to reinstall:

```
lackskill@lackskill:~/vmrc$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
[sudo] password for lackskill: 
You have VMware Server archive: 
    VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-23-generic-pae package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.i386.tar.gz
Found .tar file for vmnet module
Found .tar file for vsock module
Found .tar file for vmci module
Found .tar file for vmmon module
Extracting .tar files in order to apply the patch...
Untarring /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock.tar
Untarring /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon.tar
Testing patch...
Applying patch...
Preparing new tar file for vmnet module
Preparing new tar file for vsock module
Preparing new tar file for vmci module
Preparing new tar file for vmmon module
Checking that the compiling will succeed...
Trying to compile vmnet module to see if it works
Performing make in /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
Trying to compile vsock module to see if it works
Performing make in /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock-only
Using 2.6.x kernel build system.
WARNING: "VMCIDatagram_CreateHnd" [/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vsock-only/vsock.ko] undefined!
Trying to compile vmci module to see if it works
Performing make in /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Trying to compile vmmon module to see if it works
Performing make in /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only
Using 2.6.x kernel build system.
In file included from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.h:29,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:101:
/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_module.h:27,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.h:29,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:101:
/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_module.h:27,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./common/hostif.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:73:
/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/mmzone.h:7,
                 from include/linux/gfp.h:4,
                 from include/linux/mm.h:8,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_page.h:23,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/linux/hostif.c:32:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.c:40:
/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/common/vmx86.c:32:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./common/vmx86.h:32,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/vmcore/moduleloop.c:35:
/home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/./include/compat_sched.h:23,
                 from /home/lackskill/vmrc/vmware-server-distrib/lib/modules/source/vmmon-only/vmcore/moduleloop.c:31:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
Rebuilding tar files...
Replacing original file vmnet.tar with patched file...
Replacing original file vsock.tar with patched file...
Replacing original file vmci.tar with patched file...
Replacing original file vmmon.tar with patched file...
Removing binaries directory...
Patching vmware-install.pl...
patching file /home/lackskill/vmrc/vmware-server-distrib/bin/vmware-config.pl
Starting VMware Server original install script...
Creating a new VMware Server installer database using the tar4 format.

Installing VMware Server.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware] 

The path "/usr/lib/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware Server 2.0.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.
```

and:

```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-23-generic-pae/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.32-23-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/./common/hostif.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/hostif.c:73:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/mmzone.h:7,
                 from include/linux/gfp.h:4,
                 from include/linux/mm.h:8,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_page.h:23,
                 from /tmp/vmware-config0/vmmon-only/linux/hostif.c:32:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-config0/vmmon-only/common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/common/vmx86.c:40:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /tmp/vmware-config0/vmmon-only/common/vmx86.c:32:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.c:35:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:56,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:56,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_sched.h:23,
                 from /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.c:31:
/usr/src/linux-headers-2.6.32-23-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The vmmon module loads perfectly into the running kernel.

None of the pre-built vmci modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmci module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmci module.

Building the vmci module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmci-only'
make -C /lib/modules/2.6.32-23-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/vmware-config0/vmci-only/common/vmciResource.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmci-only/vmci.mod.o
  LD [M]  /tmp/vmware-config0/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-config0/vmci-only'
The vmci module loads perfectly into the running kernel.

VMWare config patch VMCI!
`/tmp/vmware-config0/vmci-only/Module.symvers' -> `/tmp/vmware-config0/../Module.symvers'
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

VMWare config patch VSOCK!
`/tmp/vmware-config0/../Module.symvers' -> `/tmp/vmware-config0/vsock-only/Module.symvers'
Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.32-23-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config0/vsock-only'
The vsock module loads perfectly into the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Please specify a name for this network. 
[Bridged] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Please specify a name for this network. [NAT] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.216.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.216.0.

Do you wish to configure another NAT network? (yes/no) [no] 

Do you want to be able to use host-only networking in your virtual machines? 
[yes] 

Configuring a host-only network for vmnet1.

Please specify a name for this network. 
[HostOnly] 

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.17.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.17.0.

Do you wish to configure another host-only network? (yes/no) [no] 

None of the pre-built vmnet modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmnet module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.32-23-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic-pae'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The vmnet module loads perfectly into the running kernel.

Please specify a port for remote connections to use [902] 

Please specify a port for standard http connections to use [8222] 

Please specify a port for secure http (https) connections to use [8333] 

The current administrative user for VMware Server  is ''.  Would you like to 
specify a different administrator? [no] 

Using root as the VMware Server administrator.

insserv: warning: script 'K01acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gssd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-core: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'smbd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: script vmware-mgmt: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rpc_pipefs' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'portmap' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'idmapd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'statd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'nmbd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and portmap if stopped
insserv:  loop involving service portmap at depth 4
insserv:  loop involving service nfs-kernel-server at depth 3
insserv: There is a loop between service nfs-kernel-server and rsyslog if stopped
insserv:  loop involving service rsyslog at depth 5
insserv:  loop involving service hwclock at depth 4
insserv: There is a loop between service portmap and nfs-kernel-server if stopped
insserv: exiting now without changing boot order!
In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  XXXXX-XXXXX-XXXXX-XXXXX

Creating a new VMware VIX API installer database using the tar4 format.

Installing VMware VIX API.

In which directory do you want to install the VMware VIX API binary files? 
[/usr/bin] 

In which directory do you want to install the VMware VIX API library files? 
[/usr/lib/vmware-vix/lib] 

The path "/usr/lib/vmware-vix/lib" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the VMware VIX API document pages? 
[/usr/share/doc/vmware-vix] 

The path "/usr/share/doc/vmware-vix" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware VIX API 1.6.2 build-203138 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-vix.pl".

Enjoy,

--the VMware team

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.2 build-203138 for Linux for this 
running kernel completed successfully.

Housekeeping...
Thank you for using the script!
Patch provided by: 
    Ramon de Carvalho Valle
    http://risesecurity.org
Script author: 
    Radu Cotescu
    http://radu.cotescu.com
```

Sorry for the long posts and I apologize if this stuff I'm posting isn't helpful for fixing the problem.

---

### Post by lackskill on 2010-07-20
I'm back up and running.  Apparently when I uninstalled it left some things behind.  Apparently those things were causing my problem.  I deleted a few remnants before I reinstalled this time and it seems to be working now.

---

### Post by lackskill on 2010-07-21
Just a quick update for anyone that cares.  For whatever reason, the Windows install from that iso would crash the VMwS completely.  I gave up on that particular VM, got my networking figured out on the 9.10 server VM, and found a different way to manage my Airport Extreme.

This can be marked as solved.

---

