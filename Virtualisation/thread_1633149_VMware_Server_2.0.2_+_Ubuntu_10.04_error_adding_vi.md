---
title: "VMware Server 2.0.2 + Ubuntu 10.04 error adding virtual appliance"
date: 2010-11-28
forum: Virtualisation
---

### Post by l1nuxfreak on 2010-11-28
Hi guys! Have some weird issues with my installation.
VMware Server 2.0.2 x64 + Ubuntu 10.04 x64

Everything seems to be working perfectly. I can create new VM and have them running fine.

The problem is when I add existing VM to the server. The web gui crashes and gives me this error.
```
The server could not complete a request (HTTP 12029 ).
```

I encountered an error about the upstart job at first but just ignored it.

Did the vmware-config.pl again and this is my output
```

The current administrative user for VMware Server  is 'user'.  Would you like to
specify a different administrator? [no]

Using user as the VMware Server administrator.

You have a pre-existing authorization.xml.  The new version will be created as
/etc/vmware/hostd/NEW_authorization.xml.  Please check the new file for any new
values that you may need to migrate to your current authorization.xml.

You have a pre-existing vmInventory.xml.  The new version will be created as
/etc/vmware/hostd/NEW_vmInventory.xml.  Please check the new file for any new
values that you may need to migrate to your current vmInventory.xml.

You have a pre-existing clients.xml.  The new version will be created as
/usr/lib/vmware/hostd/docroot/client/NEW_clients.xml.  Please check the new
file for any new values that you may need to migrate to your current
clients.xml.

This program previously created the file
/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/work, and was about to
remove it.  Somebody else apparently did it already.

insserv: warning: current stop runlevel(s) (0 2 3 5 6) of script `vmware' overwr                                                                                                                        ites defaults (0 6).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: script vmware-mgmt: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrite                                                                                                                        s defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ecryptfs-utils-save' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `cryptdisks-early' o                                                                                                                        verwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites de                                                                                                                        faults (empty).
insserv: script vmware-core: service VMware already provided!
insserv: warning: current start runlevel(s) (0 6) of script `cryptdisks' overwri                                                                                                                        tes defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwri                                                                                                                        tes defaults (empty).
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defa                                                                                                                        ults (empty).
insserv: script vmware-autostart: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overr                                                                                                                        ides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrite                                                                                                                        s defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overw                                                                                                                        rites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overw                                                                                                                        rites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ecryptfs-utils-restore' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwri                                                                                                                        tes defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and rsyncd if stopped
insserv:  loop involving service rsyncd at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyncd and rsyslog if stopped
insserv: exiting now without changing boot order!
This program previously created the file /etc/rc2.d/K08vmware, and was about to
remove it.  Somebody else apparently did it already.

This program previously created the file /etc/rc3.d/K08vmware, and was about to
remove it.  Somebody else apparently did it already.

This program previously created the file /etc/rc5.d/K08vmware, and was about to
remove it.  Somebody else apparently did it already.

This program previously created the file /etc/rc0.d/K08vmware, and was about to
remove it.  Somebody else apparently did it already.

This program previously created the file /etc/rc6.d/K08vmware, and was about to
remove it.  Somebody else apparently did it already.

In which directory do you want to keep your virtual machine files?
[/home/vmware]

You have a pre-existing datastores.xml.  The new version will be created as
/etc/vmware/hostd/NEW_datastores.xml.  Please check the new file for any new
values that you may need to migrate to your current datastores.xml.

Do you want to enter a serial number now? (yes/no/help) [no]

```

However even if I ignore those errors VMware Server seems to be running fine.
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Bridged networking on /dev/vmnet2                                   done
   Bridged networking on /dev/vmnet3                                   done
   Host-only networking on /dev/vmnet4 (background)                    done
   DHCP server on /dev/vmnet4                                          done
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
```

---

### Post by dcstar on 2010-12-01
> **l1nuxfreak said:**
> Hi guys! Have some weird issues with my installation.
VMware Server 2.0.2 x64 + Ubuntu 10.04 x64

Everything seems to be working perfectly. I can create new VM and have them running fine.

The problem is when I add existing VM to the server. The web gui crashes and gives me this error.
```
The server could not complete a request (HTTP 12029 ).
```
........

Unless the VM is **specifically** built to be compatible with VMware **Server** it probably uses an incompatible virtual hardware configuration.

---

### Post by l1nuxfreak on 2010-12-01
Thanks for the reply. I thought about that too so I tried to import the same VM into my x86 Debian 5 + x86 VMware Server 2.0.2. It works. :confused:

There must be something wrong with either the x64 ubuntu or x64 vmware.

BTW, I'm trying to import an x86 ubuntu 8.04.4 appliance I built using VMware Workstation 7. I'll try to make a new appliance and check the .vmx and .vmdk files for any hardware difference.

Will post here results if I use the same hardware settings.

---

