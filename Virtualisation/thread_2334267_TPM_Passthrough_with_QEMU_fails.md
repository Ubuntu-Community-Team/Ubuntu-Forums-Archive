---
title: "TPM Passthrough with QEMU fails"
date: 2016-08-17
forum: Virtualisation
---

### Post by dschalk-a on 2016-08-17
I am running Ubuntu 16.04 and I have installed the following:

qemu - version 2.5
qemu-kvm - version 2.5
libvirt - 1.3.1-1
virt-manager - version 1.3.2-3
virt-viewer - version 1.0-1
trousers - version 0.3.13-4
tpm-tools - version 1.3.8-2

I prefer to use Linux, but need a Windows platform with a virtual digital badge for work and would like to run it in a VM. Once I create the VM and add the TPM device, I get the following error:

[COLOR=#000080]Unable to complete install: 'internal error: process exited while connecting to monitor: 2016-08-17T23:57:55.383617Z qemu-system-x86_64: -tpmdev passthrough,id=tpm-tpm0,path=/dev/fdset/1,cancel-path=/dev/fdset/2: '/dev/fdset/1' is not a TPM device.'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 90, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 2277, in _do_async_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 501, in start_install
    noboot)
  File "/usr/share/virt-manager/virtinst/guest.py", line 416, in _create_guest
    dom = self.conn.createLinux(start_xml or final_xml, 0)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 3606, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error: process exited while connecting to monitor: 2016-08-17T23:57:55.383617Z qemu-system-x86_64: -tpmdev passthrough,id=tpm-tpm0,path=/dev/fdset/1,cancel-path=/dev/fdset/2: '/dev/fdset/1' is not a TPM device.

[/COLOR]The path is correct in virt-manager when the TPM device is added, but the error shows the path to be /dev/fdset/1 and the cancel-path to be /dev/fdset/2. The cancel path should be /sys/class/tpm/tpm0/device/cancel, but cancel does not exist there. Below are some outputs from tpm_version and dmesg | grep -I tpm:


~$ tpm_version
  TPM 1.2 Version Info:
  Chip Version:        1.2.3.19
  Spec Level:          2
  Errata Revision:     2
  TPM Vendor ID:       IFX
  Vendor Specific data: 0313000b 00
  TPM Version:         01010000
  Manufacturer Info:   49465800


~$ dmesg | grep -I tpm
[    3.946348] tpm_tis 00:01: 1.2 TPM (device-id 0xB, rev-id 16)
[  200.751309] audit: type=1400 audit(1471478263.879:29): apparmor="DENIED" operation="file_perm" profile="libvirt-e5dd312d-8a15-4652-925e-cc915a27b98e" name="/dev/tpm0" pid=6534 comm="qemu-system-x86" requested_mask="w" denied_mask="w" fsuid=123 ouid=123
[  200.751320] audit: type=1400 audit(1471478263.879:30): apparmor="DENIED" operation="file_perm" profile="libvirt-e5dd312d-8a15-4652-925e-cc915a27b98e" name="/dev/tpm0" pid=6534 comm="qemu-system-x86" requested_mask="w" denied_mask="w" fsuid=123 ouid=123
[  212.248188] audit: type=1400 audit(1471478275.380:35): apparmor="DENIED" operation="file_perm" profile="libvirt-e5dd312d-8a15-4652-925e-cc915a27b98e" name="/dev/tpm0" pid=6649 comm="qemu-system-x86" requested_mask="w" denied_mask="w" fsuid=123 ouid=123
[  212.248194] audit: type=1400 audit(1471478275.380:36): apparmor="DENIED" operation="file_perm" profile="libvirt-e5dd312d-8a15-4652-925e-cc915a27b98e" name="/dev/tpm0" pid=6649 comm="qemu-system-x86" requested_mask="w" denied_mask="w" fsuid=123 ouid=123

Before trying to add the TPM device, I stopped and disabled trousers. Any help would be appreciated. Thank you in advance!
DJ

---

### Post by KillerKelvUK on 2016-08-19
Hi, just tried this and hit the same issues as you...the key is the apparmor denies you see in the dmesg output (I had the same).  Stopping the apparmor process from loading at boot solved this problem for me however once in Windows the device manager says my TPM chip cannot be started due to insufficient resources but it is there.

Would appreciate your feedback if this solution works for you and whether you have the same problem once in Windows?

For completeness I have an ASRock Z97 Extreme 6 mobo with the ASRock v1.2 TPM, Ubuntu 16.04 host and Win10 guest.

Word of caution:  disabling or removing apparmor altogether should only be considered if you know what you are doing and are operating in a closed system i.e. its there to protect you.  I personally hate it as its the cause of so many problems especially in the libvirt/qemu/kvm space, however if you wish to preserve its use then you could look to defining a new/editing an apparmor profile that will allow access to the /dev/tpm0 device which is what apparmor is denying qemu access to.

---

### Post by KillerKelvUK on 2016-08-19
Okay more digging on the windows error, seems likely that there is a bug in qemu causing it to not load the TPM driver properly (see here [https://bugzilla.redhat.com/show_bug.cgi?id=1281413](https://bugzilla.redhat.com/show_bug.cgi?id=1281413)).  Latest git source includes the patch referenced in the bugzilla thread and all commits say the patch is planned into qemu v2.6 which for ubuntu doesn't officially land until 16.10.  Will dig around as someone likely has a ppa building later qemu/kvm versions, failing that will build myself and test.

---

### Post by KillerKelvUK on 2016-08-19
Okay so I added a PPA which was providing later version of qemu, libvirt etc ([https://launchpad.net/~jacob/+archive/ubuntu/virtualisation](https://launchpad.net/~jacob/+archive/ubuntu/virtualisation)), confirmed that qemu 2.6.0 was installed and retested, the TPM module now correctly loads in Windows 10 so this is most definitely a bug with qemu 2.5.

---

### Post by KillerKelvUK on 2016-08-22
If using qemu 2.5 and experiencing the problem where the Windows guest fails to initialize the TMP driver with the reason: 'device cannot find enough free resources' then I've raised a bug, please acknowledge yourself and your issue here [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1615722](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/1615722)

---

### Post by dschalk-a on 2016-08-25
@KillerKelvUK, thanks for the replies. It is working out of the box in Fedora 23/24, which uses selinux and not apparmor. I believe apparmor is a fork of selinux. I discovered that today. I too was able to get it working with an Ubuntu guest. I will test my Win10 guest in the morning and post back.

---

### Post by KillerKelvUK on 2016-08-25
> **dschalk-a said:**
> @KillerKelvUK, thanks for the replies. It is working out of the box in Fedora 23/24, which uses selinux and not apparmor. I believe apparmor is a fork of selinux. I discovered that today. I too was able to get it working with an Ubuntu guest. I will test my Win10 guest in the morning and post back.

Hey, yeah I tested in Fed24 also and the driver started without issue however I still hit the same problem with the Windows TPM Admin so would be great to get your comparison to is if you get different results.

---

### Post by dschalk-a on 2016-08-25
I had to reinstall Ubuntu since I broke it by switching to selinux. I found this article for following apparmor while using an application and automating the allow/deny policies within.

[http://www.howtogeek.com/118328/how-to-create-apparmor-profiles-to-lock-down-programs-on-ubuntu/](http://www.howtogeek.com/118328/how-to-create-apparmor-profiles-to-lock-down-programs-on-ubuntu/)

I still haven't spun up my win10 VM, busy morning, but I should be able to this afternoon. I'll post the results of both tests (apparmor and win10).

---

### Post by dschalk-a on 2016-08-25
I also noticed that there is no win10 option when using virt-manager with qemu, so it may not support it yet. I'll follow this rabbit hole and see where it leads though:

[http://www.linux-kvm.org/page/Guest_Support_Status](http://www.linux-kvm.org/page/Guest_Support_Status)

[https://social.technet.microsoft.com/Forums/en-US/695c8997-52cf-4c30-a3f7-f26a40dc703a/failed-install-of-build-10041-in-the-kvm-virtual-machine-system-thread-exception-not-handled?forum=WinPreview2014Setup](https://social.technet.microsoft.com/Forums/en-US/695c8997-52cf-4c30-a3f7-f26a40dc703a/failed-install-of-build-10041-in-the-kvm-virtual-machine-system-thread-exception-not-handled?forum=WinPreview2014Setup)

---

### Post by KillerKelvUK on 2016-08-25
Win10 qemu/kvm support and what options virt-manager gives you are two different things.  virt-manager I believe tracks the stable libvirt release and libvirt in turn always lags behind qemu which incorporates new options for testing but which libvirt doesn't class as stable.  You'll notice the stock Fedora install of virt-manager is typically more recent that the latest Ubuntu, certainly the Ubuntu LTS releases anyway.

Regardless Win10 is well tried and tested with qemu so that isn't a problem, those links you posted are pretty old and certainly out of date.

---

### Post by dschalk-a on 2016-08-27
> **KillerKelvUK said:**
> Win10 qemu/kvm support and what options virt-manager gives you are two different things.  virt-manager I believe tracks the stable libvirt release and libvirt in turn always lags behind qemu which incorporates new options for testing but which libvirt doesn't class as stable.  You'll notice the stock Fedora install of virt-manager is typically more recent that the latest Ubuntu, certainly the Ubuntu LTS releases anyway.

Regardless Win10 is well tried and tested with qemu so that isn't a problem, those links you posted are pretty old and certainly out of date.

[SIZE=2]I do not see win10 or version 10.0, but I am running qemu-kvm 2.5. After running 'osinfo-query os' I get the following:

ubuntu9.10           | Ubuntu 9.10                                        | 9.10     | [http://ubuntu.com/ubuntu/9.10](http://ubuntu.com/ubuntu/9.10)           
 win1.0               | Microsoft Windows 1.0                              | 1.0      | [http://microsoft.com/win/1.0](http://microsoft.com/win/1.0)            
 win2.0               | Microsoft Windows 2.0                              | 2.0      | [http://microsoft.com/win/2.0](http://microsoft.com/win/2.0)            
 win2.1               | Microsoft Windows 2.1                              | 2.1      | [http://microsoft.com/win/2.1](http://microsoft.com/win/2.1)            
 win2k                | Microsoft Windows 2000                             | 5.0      | [http://microsoft.com/win/2k](http://microsoft.com/win/2k)             
 win2k12              | Microsoft Windows Server 2012                      | 6.3      | [http://microsoft.com/win/2k12](http://microsoft.com/win/2k12)           
 win2k12r2            | Microsoft Windows Server 2012 R2                   | 6.3      | [http://microsoft.com/win/2k12r2](http://microsoft.com/win/2k12r2)         
 win2k3               | Microsoft Windows Server 2003                      | 5.2      | [http://microsoft.com/win/2k3](http://microsoft.com/win/2k3)            
 win2k3r2             | Microsoft Windows Server 2003 R2                   | 5.2      | [http://microsoft.com/win/2k3r2](http://microsoft.com/win/2k3r2)          
 win2k8               | Microsoft Windows Server 2008                      | 6.0      | [http://microsoft.com/win/2k8](http://microsoft.com/win/2k8)            
 win2k8r2             | Microsoft Windows Server 2008 R2                   | 6.1      | [http://microsoft.com/win/2k8r2](http://microsoft.com/win/2k8r2)          
 win3.1               | Microsoft Windows 3.1                              | 3.1      | [http://microsoft.com/win/3.1](http://microsoft.com/win/3.1)            
 win7                 | Microsoft Windows 7                                | 6.1      | [http://microsoft.com/win/7](http://microsoft.com/win/7)              
 win8                 | Microsoft Windows 8                                | 6.2      | [http://microsoft.com/win/8](http://microsoft.com/win/8)              
 win8.1               | Microsoft Windows 8.1                              | 6.3      | [http://microsoft.com/win/8.1](http://microsoft.com/win/8.1)            
 win95                | Microsoft Windows 95                               | 4.0      | [http://microsoft.com/win/95](http://microsoft.com/win/95)             
 win98                | Microsoft Windows 98                               | 4.1      | [http://microsoft.com/win/98](http://microsoft.com/win/98)             
 winme                | Microsoft Windows Millennium Edition               | 4.9      | [http://microsoft.com/win/me](http://microsoft.com/win/me)             
 winnt3.1             | Microsoft Windows NT Server 3.1                    | 3.1      | [http://microsoft.com/winnt/3.1](http://microsoft.com/winnt/3.1)          
 winnt3.5             | Microsoft Windows NT Server 3.5                    | 3.5      | [http://microsoft.com/winnt/3.5](http://microsoft.com/winnt/3.5)          
 winnt3.51            | Microsoft Windows NT Server 3.51                   | 3.51     | [http://microsoft.com/winnt/3.51](http://microsoft.com/winnt/3.51)         
 winnt4.0             | Microsoft Windows NT Server 4.0                    | 4.0      | [http://microsoft.com/winnt/4.0](http://microsoft.com/winnt/4.0)          
 winvista             | Microsoft Windows Vista                            | 6.0      | [http://microsoft.com/win/vista](http://microsoft.com/win/vista)          
 winxp                | Microsoft Windows XP                               | 5.1      | [http://microsoft.com/win/xp](http://microsoft.com/win/xp)             

I get the same 'device cannot find enough free resources' error though. I will see what I can come up with this weekend. I will compile and install the newest version of qemu-kvm since I am running 2.5. I see that 2.6.1 and 2.7rc are out. And, I will chime in on the bugs you've reported.

I did, however, get apparmor to allow me to start a VM with TPM enabled in Ubuntu 16.04. I edited /etc/apparmor.d/abstractions/libvirt-qemu and added the following:
 
/dev/tpm0 rw,[/SIZE]

above:

/dev/net/tun rw,
/dev/tap* rw,
/dev/kvm rw,
[LEFT][COLOR=windowtext][FONT=&quot][COLOR=windowtext][FONT=Calibri][/FONT][/COLOR][FONT=Calibri] [/FONT][/FONT][/COLOR][/LEFT]
It was at line 23.

---

### Post by KillerKelvUK on 2016-08-27
Hey, result on fixing apparmor...do you have to run qemu as root also?

I didn't have osinfo-query installed, found it in the libosinfo-bin package so took a look, I get lots more results than what you have posted so assume you gave a triaged list.  Anyways I tracked the source and the changelog shows Win10 is included which is odd as like yours it wasn't in my osinfo-query output.  [https://gitlab.com/libosinfo/libosinfo/blob/master/NEWS](https://gitlab.com/libosinfo/libosinfo/blob/master/NEWS)

---

### Post by dschalk-a on 2016-08-29
> **KillerKelvUK said:**
> Hey, result on fixing apparmor...do you have to run qemu as root also?

I didn't have osinfo-query installed, found it in the libosinfo-bin package so took a look, I get lots more results than what you have posted so assume you gave a triaged list.  Anyways I tracked the source and the changelog shows Win10 is included which is odd as like yours it wasn't in my osinfo-query output.  [https://gitlab.com/libosinfo/libosinfo/blob/master/NEWS](https://gitlab.com/libosinfo/libosinfo/blob/master/NEWS)

I do not run qemu as root, when installing libvirt-bin, i believe it adds the current user to the libvirt group and apparmor allows the application to access the hardware and not a particular user.

As for libosinfo, if you are looking at the changelog for 0.3.0, it's odd that they add Win10 and not Server 2016 since they are both 10.0.*. I wonder if it is a misprint.

---

