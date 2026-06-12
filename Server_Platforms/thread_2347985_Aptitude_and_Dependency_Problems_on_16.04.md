---
title: "Aptitude and Dependency Problems on 16.04"
date: 2016-12-30
forum: Server Platforms
---

### Post by astarmathsandphysics on 2016-12-30
When I try to update/upgrade I get this message

```
dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-core
 dovecot-lmtpd
 dovecot-imapd
 dovecot-mysql
 dovecot-pop3d
 python3
 python-apt-common
 python3-apt
 python3-xkit
 ubuntu-drivers-common
 lsb-release
 dh-python
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

autoclean and any dpkg configure with any options does not fix it.  

How can I solve this problem?

---

### Post by TheFu on 2016-12-31
* please use "code tags" so things line up as we expect.
* Please post the exact command and relevant output.
* if any packages were installed outside the package manager (apt or apt-get or aptitude), perhaps using dpkg, that could be holding some old packages back. 

Accuracy is important. Details are important.  If the 'update' fails, then the 'upgrade' isn't useful.

---

### Post by astarmathsandphysics on 2016-12-31
Cant work out what xman does. Very bad day today. Have been through a day of nonbooting and blank screens. I managed to recover it though, and now I have these messages on sudo apt-get install -f

```
dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3
 lsb-release
 python3-apt
 python3-dbus
 python3-gi
 dovecot-core
 firefox
 gconf2
 gir1.2-ibus-1.0:amd64
 gnome-shell
 gdm3
 gdm
 python3-cairo
 python3-gi-cairo
 gedit
 libgksu2-0
 gksu
 ibus
 libgnomevfs2-common
 libgnomevfs2-0:amd64
 libgnome2-common
 libgnome-2-0:amd64
 libgnome2-bin
 libgnome2-0:amd64
 libbonoboui2-0:amd64
 libgnomeui-0:amd64
 python3-bs4
 python3-pkg-resources
 python3-chardet
 python3-cups
 python3-six
 python3-urllib3
 python3-requests
 python3-cupshelpers
 python3-html5lib
 python3-lxml
 python3-defer
 python3-aptdaemon
 python3-aptdaemon.pkcompat
 system-config-printer-common
 system-config-printer-gnome
 system-config-printer-udev
 ubuntu-system-service
 aptdaemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can still install some packages - I installed gedit and I can't work out why these other things do not install

---

### Post by ian-weisser on 2016-12-31
Like TheFU wrote,

1) Please use [CODE] tags to contain your pastes. [Instructions]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"). It preserves the formatting, and makes the output easier to read.

3) Package errors like yours are usually due to version conflicts. There are other possibilities, but version conflicts are most frequent. Version conflicts occur when you install software from non-Ubuntu sources...like external python3 packages.

 Did you, by chance, change the version of Python3 on your system from some other source?

---

### Post by astarmathsandphysics on 2016-12-31
I am only having these problems since I upgraded to 16.04. I know then I had python 2.7 or something. During the upgrade updates to mysql also failed and I had to install that manually with a lot of pfaffing around

---

### Post by TheFu on 2016-12-31
> pfaffing around probably broke lots of dependencies. Find what you did. That should help undo. Look for any .deb installs or PPA additions.

The default python on 14.04 is v2.7.6.
The default python on 16.04 is v2.7.12.

The default python3 on 14.04 is v3.4.3.
The default python3 on 16.04 is v3.5.2.

Don't know if this matters to you or not.  The best practice for any scripting language is NOT to touch the system python and to use a localization method to have some other version.  Don't know how to do it on python, but for ruby, it is rbenv or rvm. For perl it is perlbrew. Python definitely has a method too, if that matters to you.

---

### Post by astarmathsandphysics on 2017-01-01
I uninstalled python3, ran apt-get clean autoclean autoremove then install -f

I get

```
astarmathsandphysics@server:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up dovecot-core (1:2.2.22-1ubuntu2.2) ...
Job for dovecot.service failed because the control process exited with error code. See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TheFu on 2017-01-01
1) what does the **journalctl** cmd show? Anything useful?
2) I'd try reinstalling dovecot-core.

Did you ever install anything by downloading a .deb file? If you don't say, we'll never know and assume that is the root issue.

---

### Post by astarmathsandphysics on 2017-01-01
journalctl returns a lot of junk. Here is a page of it

```
-- Logs begin at Sat 2016-12-31 14:12:28 GMT, end at Sun 2017-01-01 19:40:09 GMT. --
Dec 31 14:12:28 server systemd-journald[415]: Runtime journal (/run/log/journal/) is 8.0M, max 160.4M, 152.4M free.
Dec 31 14:12:28 server kernel: Initializing cgroup subsys cpuset
Dec 31 14:12:28 server kernel: Initializing cgroup subsys cpu
Dec 31 14:12:28 server kernel: Initializing cgroup subsys cpuacct
Dec 31 14:12:28 server kernel: Linux version 4.4.0-45-generic (buildd@lgw01-34) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.2) ) #66-Ubuntu SMP 
Dec 31 14:12:28 server kernel: Command line: BOOT_IMAGE=/vmlinuz-4.4.0-45-generic root=/dev/mapper/SERVER--vg-root ro recovery nomodeset
Dec 31 14:12:28 server kernel: KERNEL supported cpus:
Dec 31 14:12:28 server kernel:   Intel GenuineIntel
Dec 31 14:12:28 server kernel:   AMD AuthenticAMD
Dec 31 14:12:28 server kernel:   Centaur CentaurHauls
Dec 31 14:12:28 server kernel: x86/fpu: Legacy x87 FPU detected.
Dec 31 14:12:28 server kernel: x86/fpu: Using 'lazy' FPU context switches.
Dec 31 14:12:28 server kernel: e820: BIOS-provided physical RAM map:
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009ffff] usable
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cffa7fff] usable
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x00000000cffa8000-0x00000000cffb7bff] ACPI data
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x00000000cffb7c00-0x00000000cfffffff] reserved
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x00000000fe000000-0x00000000ffffffff] reserved
Dec 31 14:12:28 server kernel: BIOS-e820: [mem 0x0000000100000000-0x000000042fffffff] usable
Dec 31 14:12:28 server kernel: NX (Execute Disable) protection: active
Dec 31 14:12:28 server kernel: SMBIOS 2.4 present.
Dec 31 14:12:28 server kernel: DMI: Dell Inc. PowerEdge 1900/0TW855, BIOS 1.3.7 03/26/2007
Dec 31 14:12:28 server kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Dec 31 14:12:28 server kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Dec 31 14:12:28 server kernel: e820: last_pfn = 0x430000 max_arch_pfn = 0x400000000
Dec 31 14:12:28 server kernel: MTRR default type: uncachable
Dec 31 14:12:28 server kernel: MTRR fixed ranges enabled:
Dec 31 14:12:28 server kernel:   00000-9FFFF write-back
Dec 31 14:12:28 server kernel:   A0000-BFFFF uncachable
Dec 31 14:12:28 server kernel:   C0000-CFFFF write-protect
Dec 31 14:12:28 server kernel:   D0000-EBFFF uncachable
Dec 31 14:12:28 server kernel:   EC000-FFFFF write-protect
Dec 31 14:12:28 server kernel: MTRR variable ranges enabled:
Dec 31 14:12:28 server kernel:   0 base 0000000000 mask 3F80000000 write-back
Dec 31 14:12:28 server kernel:   1 base 0080000000 mask 3FC0000000 write-back
Dec 31 14:12:28 server kernel:   2 base 00C0000000 mask 3FF0000000 write-back
Dec 31 14:12:28 server kernel:   3 base 0100000000 mask 3F00000000 write-back
Dec 31 14:12:28 server kernel:   4 base 0200000000 mask 3E00000000 write-back
Dec 31 14:12:28 server kernel:   5 base 0400000000 mask 3FC0000000 write-back
Dec 31 14:12:28 server kernel:   6 disabled
Dec 31 14:12:28 server kernel:   7 disabled
Dec 31 14:12:28 server kernel: x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Dec 31 14:12:28 server kernel: e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
Dec 31 14:12:28 server kernel: e820: last_pfn = 0xcffa8 max_arch_pfn = 0x400000000
Dec 31 14:12:28 server kernel: found SMP MP-table at [mem 0x000fe710-0x000fe71f] mapped at [ffff8800000fe710]
Dec 31 14:12:28 server kernel: Scanning 1 areas for low memory corruption
Dec 31 14:12:28 server kernel: Base memory trampoline at [ffff880000099000] 99000 size 24576
Dec 31 14:12:28 server kernel: BRK [0x02201000, 0x02201fff] PGTABLE
Dec 31 14:12:28 server kernel: BRK [0x02202000, 0x02202fff] PGTABLE
Dec 31 14:12:28 server kernel: BRK [0x02203000, 0x02203fff] PGTABLE
Dec 31 14:12:28 server kernel: BRK [0x02204000, 0x02204fff] PGTABLE
Dec 31 14:12:28 server kernel: BRK [0x02205000, 0x02205fff] PGTABLE
Dec 31 14:12:28 server kernel: BRK [0x02206000, 0x02206fff] PGTABLE
Dec 31 14:12:28 server kernel: RAMDISK: [mem 0x334e2000-0x35a68fff]
Dec 31 14:12:28 server kernel: ACPI: Early table checksum verification disabled
Dec 31 14:12:28 server kernel: ACPI: RSDP 0x00000000000F2620 000024 (v02 DELL  )
Dec 31 14:12:28 server kernel: ACPI: XSDT 0x00000000000F26A0 00004C (v01 DELL   PE_SC3   00000001 DELL 00000001)

```

Deleting reinstalling dovecot-core makes no difference. I was using apt-get i a terminal to install, not using deb files

---

### Post by ian-weisser on 2017-01-01
Exactly which version of Python 3 is currently installed on your system?
```
$ python3 --version
```

What did you install that caused the problem? Dovecot? Python? Something else?
From which source or PPA did you install it?
Were you following instructions? If so, can we see the instructions?

Can you please show us the complete output of:
```
sudo apt update
sudo apt upgrade
```

---

### Post by astarmathsandphysics on 2017-01-02
Am using python3.5.2
I noticed the problem originally when trying to install dovecot-core

```
astarmathsandphysics@server:~$ sudo apt update
[sudo] password for astarmathsandphysics: 
Hit:1 http://ppa.launchpad.net/atareao/nautilus-extensions/ubuntu trusty InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                                          
Ign:3 http://dl.google.com/linux/talkplugin/deb stable InRelease                                 
Hit:4 http://ppa.launchpad.net/noobslab/apps/ubuntu trusty InRelease                                                                              
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                          
Hit:6 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease                                                                                           
Ign:7 http://dl.google.com/linux/mod-pagespeed/deb stable InRelease                                                                                         
Hit:8 http://dl.google.com/linux/talkplugin/deb stable Release                                            
Get:9 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                     
Get:10 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                               
Hit:11 http://dl.google.com/linux/mod-pagespeed/deb stable Release       
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [303 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [183 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]  
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:19 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.2 kB]
Get:24 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:25 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Fetched 1,218 kB in 2s (554 kB/s)                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.

```

```
astarmathsandphysics@server:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
61 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python3 (3.5.1-3) ...
running python rtupdate hooks for python3.5...
dpkg-query: package 'gnome-applets-data' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gnome-applets-data
error running python rtupdate hook gnome-applets-data
dpkg: error processing package python3 (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xkit:
 python3-xkit depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-xkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 ubuntu-drivers-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 ubuntu-drivers-common depends on python3-xkit; however:
  Package python3-xkit is not configurNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                                                                  No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                 No apport report written because MaxReports has already been reached
        No apport report written because MaxReports has already been reached
                                                                            No apport report written because MaxReports has already been reached
                                                                                                                                                No apport report written because MaxReports has already been reached
                                                       No apport report written because MaxReports has already been reached
                                                                                                                           No apport report written because MaxReports has already been reached
                                  No apport report written because MaxReports has already been reached
                                                                                                      No apport report written because MaxReports has already been reached
             No apport report written because MaxReports has already been reached
                                                                                 No apport report written because MaxReports has already been reached
                                                                                                                                                     No apport report written because MaxReports has already been reached
                                                            ed yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pkg-resources:
 python3-pkg-resources depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pkg-resources (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-chardet depends on python3-pkg-resources; howeNo apport report written because MaxReports has already been reached
                                                                                                                           No apport report written because MaxReports has already been reached
                                  No apport report written because MaxReports has already been reached
                                                                                                      No apport report written because MaxReports has already been reached
             No apport report written because MaxReports has already been reached
                                                                                 No apport report written because MaxReports has already been reached
                                                                                                                                                     No apport report written because MaxReports has already been reached
                                                            No apport report written because MaxReports has already been reached
                                                                                                                                No apport report written because MaxReports has already been reached
                                       No apport report written because MaxReports has already been reached
                                                                                                           ver:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-six:
 python3-six depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-six (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-debian:
 python3-debian depends on python3-chardet; however:
  Package python3-chardet is not configured yet.
 python3-debian depends on python3-six (>> 1.4~); however:
  Package python3-six is not configured yet.
 python3-debian depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python3:any; however:
  Package python3 is not configured yet.
 update-notifier-common depends on python3-apt; however:
  Package python3-apt is not configured yet.
 update-notifier-common depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 update-notifier-common depends on python3-debian; however:
  Package python3-debian is not configured yet.

dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.5); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on lsb-release; however:
  Package lsb-release is not configured yet.
 python3-commandnotfound depends on python3-apt; however:
  Package python3-apt is not configured yet.
 python3-commandnotfound depends on python3-gdbm; however:
  Package python3-gdbm:amd64 is not configured yet.
 python3-commandnotfound depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-update-manager depends on python3-apt (>= 0.8.5~); however:
  Package python3-apt is not configured yet.
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:16.04.19); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:16.04.4); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-apport depends on python3-apt (>= 0.7.9); however:
  Package python3-apt is not configured yet.
 python3-apport depends on python3-problem-report (>= 0.94); however:
  Package python3-problem-report is not configured yet.
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.
 apport depends on python3-apport (>= 2.20.1-0ubuntu2.4); however:
  Package python3-apport is not configured yet.
 apport depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing package apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3; however:
  Package python3 is not configured yet.
 apport-gtk depends on python3-apport (>= 2.20.1-0ubuntu2.4); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on python3-gi; however:
  Package python3-gi is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xapian1.3:
 python3-xapian1.3 depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-xapian1.3 depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-xapian1.3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apt-xapian-index:
 apt-xapian-index depends on python3-xapian1.3; however:
  Package python3-xapian1.3 is not configured yet.
 apt-xapian-index depends on python3-apt (>= 0.7.93.2); however:
  Package python3-apt is not configured yet.
 apt-xapian-index depends on python3-debian (>= 0.1.14); however:
  Package python3-debian is not configured yet.
 apt-xapian-index depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package apt-xapian-index (--configure):
 dependency problems - leaving unconfigured
Setting up dovecot-core (1:2.2.22-1ubuntu2.2) ...
Job for dovecot.service failed because the control process exited with error code. See "systemctl status dovecot.service" and "journalctl -xe" for details.
invoke-rc.d: initscript dovecot, action "start" failed.
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing package firefox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gir1.2-ibus-1.0:amd64:
 gir1.2-ibus-1.0:amd64 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package gir1.2-ibus-1.0:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gir1.2-ibus-1.0 (>= 1.5.2); however:
  Package gir1.2-ibus-1.0:amd64 is not configured yet.
 gnome-shell depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package gnome-shell (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gdm3:
 gdm3 depends on gnome-shell (>= 3.10.1-2~); however:
  Package gnome-shell is not configured yet.

dpkg: error processing package gdm3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gdm3; however:
  Package gdm3 is not configured yet.

dpkg: error processing package gdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-cairo:
 python3-cairo depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-cairo depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cairo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-gi-cairo:
 python3-gi-cairo depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-gi-cairo depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.
 python3-gi-cairo depends on python3-gi (= 3.20.0-0ubuntu1); however:
  Package python3-gi is not configured yet.
 python3-gi-cairo depends on python3-cairo (>= 1.10.0+dfsg-3~exp2); however:
  Package python3-cairo is not configured yet.

dpkg: error processing package python3-gi-cairo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of gedit:
 gedit depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 gedit depends on python3-gi (>= 3.0); however:
  Package python3-gi is not configured yet.
 gedit depends on python3-gi-cairo (>= 3.0); however:
  Package python3-gi-cairo is not configured yet.

dpkg: error processing package gedit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-blinker:
 python3-blinker depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-blinker (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-cffi-backend:
 python3-cffi-backend depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-cffi-backend depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cffi-backend (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-idna:
 python3-idna depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-idna (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-pyasn1:
 python3-pyasn1 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pyasn1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-cryptography:
 python3-cryptography depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-cryptography depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.
 python3-cryptography depends on python3-cffi-backend-api-9729; however:
  Package python3-cffi-backend-api-9729 is not installed.
  Package python3-cffi-backend which provides python3-cffi-backend-api-9729 is not configured yet.
 python3-cryptography depends on python3-idna; however:
  Package python3-idna is not configured yet.
 python3-cryptography depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.
 python3-cryptography depends on python3-pyasn1 (>= 0.1.8); however:
  Package python3-pyasn1 is not configured yet.
 python3-cryptography depends on python3-six (>= 1.4.1); however:
  Package python3-six is not configured yet.

dpkg: error processing package python3-cryptography (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-httplib2:
 python3-httplib2 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-httplib2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-jwt:
 python3-jwt depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-jwt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-oauthlib depends on python3-blinker; however:
  Package python3-blinker is not configured yet.
 python3-oauthlib depends on python3-cryptography; however:
  Package python3-cryptography is not configured yet.
 python3-oauthlib depends on python3-jwt (>= 1.0.0); however:
  Package python3-jwt is not configured yet.

dpkg: error processing package python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-pycurl:
 python3-pycurl depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-pycurl depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pycurl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3-apt (>= 0.6.20ubuntu16); however:
  Package python3-apt is not configured yet.
 python3-software-properties depends on python3-pycurl; however:
  Package python3-pycurl is not configured yet.
 python3-software-properties depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3-gi; however:
  Package python3-gi is not configured yet.
 software-properties-common depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 software-properties-common depends on python3-software-properties (= 0.96.20.5); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-systemd:
 python3-systemd depends on python3 (<< 3.6); however:
  Package python3 is not configured yet.
 python3-systemd depends on python3 (>= 3.5~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-systemd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-xdg:
 python3-xdg depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-xdg (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of software-center-aptdaemon-plugins:
 software-center-aptdaemon-plugins depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing package software-center-aptdaemon-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-defer:
 python3-defer depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-defer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-aptdaemon depends on python3-apt (>= 0.8.5~ubuntu1); however:
  Package python3-apt is not configured yet.
 python3-aptdaemon depends on python3-defer (>= 1.0.6); however:
  Package python3-defer is not configured yet.
 python3-aptdaemon depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 python3-aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3; however:
  Package python3 is not configured yet.
 aptdaemon depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu14); however:
  Package python3-aptdaemon is not configured yet.
 aptdaemon depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of python3-piston-mini-client:
 python3-piston-mini-client depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-piston-mini-client depends on python3-httplib2; however:
  Package python3-httplib2 is not configured yet.
 python3-piston-mini-client depends on python3-oauthlib; however:
  Package python3-oauthlib is not configured yet.

dpkg: error processing package python3-piston-mini-client (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: too many errors, stopping
Errors were encountered while processing:
 python3
 python3-apt
 python3-xkit
 ubuntu-drivers-common
 python3-dbus
 python3-pkg-resources
 python3-chardet
 python3-six
 python3-debian
 update-notifier-common
 lsb-release
 python3-gdbm:amd64
 python3-commandnotfound
 python3-distupgrade
 python3-update-manager
 python3-gi
 ubuntu-release-upgrader-core
 update-manager-core
 python3-problem-report
 python3-apport
 apport
 apport-gtk
 python3-xapian1.3
 apt-xapian-index
 dovecot-core
 firefox
 gir1.2-ibus-1.0:amd64
 gnome-shell
 gdm3
 gdm
 python3-cairo
 python3-gi-cairo
 gedit
 python3-blinker
 python3-cffi-backend
 python3-idna
 python3-pyasn1
 python3-cryptography
 python3-httplib2
 python3-jwt
 python3-oauthlib
 python3-pycurl
 python3-software-properties
 software-properties-common
 python3-systemd
 python3-xdg
 software-center-aptdaemon-plugins
 python3-defer
 python3-aptdaemon
 aptdaemon
 python3-piston-mini-client
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2017-01-02
We seem to have identified two problems so far....

First, dovecot isn't working:
> **astarmathsandphysics said:**
> 
Setting up dovecot-core (1:2.2.22-1ubuntu2.2) ...
Job for dovecot.service failed because the control process exited with error code.** See "systemctl status dovecot.service" and "journalctl -xe" for details.**
invoke-rc.d: initscript dovecot, action "start" failed.

Troubleshooting that problem starts in a straightforward way...follow those instructions.


Second, there's a fascinating version or package conflict somewhere:
> **astarmathsandphysics said:**
> [...]
61 not fully installed or removed.
[...]
Setting up python3 (3.5.1-3) ...
running python rtupdate hooks for python3.5...
**dpkg-query: package 'gnome-applets-data' is not installed**
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gnome-applets-data
error running python rtupdate hook gnome-applets-data

The dpkg-query notice in the middle of setting up python seems unexpected.
Try installing that package, and see if it helps.

---

### Post by astarmathsandphysics on 2017-01-02
Installed gnome-applets-data, then ran through 
```
sudo iinstall-get apt -f sudo dpkg --configure -a
```
 Only thing that is not installing now is dovecot-core

---

### Post by ian-weisser on 2017-01-02
Happy to see that solved most of your problem.
What's the current dovecot-core error?

---

### Post by mc4man on 2017-01-02
If you get stuck on the dovecot-core deal maybe take a glance here
[https://ubuntuforums.org/showthread.php?t=2320414](https://ubuntuforums.org/showthread.php?t=2320414)

---

### Post by astarmathsandphysics on 2017-01-03
dovecot-core is 1:2.2.22-1ubuntu2.2

---

