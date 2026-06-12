---
title: "Failed to probe capabilities for /usr/local/bin/qemu-system-x86_64: internal error"
date: 2021-07-28
forum: Virtualisation
---

### Post by marietto2008 on 2021-07-28
Hello.

I've just launched "virt-manager" on my Ubuntu 21.04 and with my big surprise I've seen the error "kvm is not available. It could means that the kvm package is not installed and so on" ; this is not true. I've installed kvm and it is working great,as u can see the image below :

[https://ibb.co/tqmdcYD](https://ibb.co/tqmdcYD)

please give a look at what the terminal is telling : "/dev/kvm exists ; kvm acceleration can be used". What's missing ? 

By looking more deeply inside,I found this :

> # apt install qemu-kvm libvirt-clients libvirt-daemon-system

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'qemu-system-x86' instead of 'qemu-kvm'
qemu-system-x86 is already the newest version (1:5.2+dfsg-9ubuntu3.1).

libvirt-clients is already the newest version (7.0.0-2ubuntu2).
libvirt-daemon-system is already the newest version (7.0.0-2ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

# virt-host-validate

  QEMU: Checking for hardware virtualization                                 : PASS
  QEMU: Checking if device /dev/kvm exists                                   : PASS
  QEMU: Checking if device /dev/kvm is accessible                            : PASS
  QEMU: Checking if device /dev/vhost-net exists                             : PASS
  QEMU: Checking if device /dev/net/tun exists                               : PASS
  QEMU: Checking for cgroup 'cpu' controller support                         : PASS
  QEMU: Checking for cgroup 'cpuacct' controller support                     : PASS
  QEMU: Checking for cgroup 'cpuset' controller support                      : PASS
  QEMU: Checking for cgroup 'memory' controller support                      : PASS
  QEMU: Checking for cgroup 'devices' controller support                     : PASS
  QEMU: Checking for cgroup 'blkio' controller support                       : PASS
  QEMU: Checking for device assignment IOMMU support                         : PASS
  QEMU: Checking if IOMMU is enabled by kernel                               : PASS
  QEMU: Checking for secure guest support                                    : WARN (Unknown if this platform has Secure Guest support)
   LXC: Checking for Linux >= 2.6.26                                         : PASS
   LXC: Checking for namespace ipc                                           : PASS
   LXC: Checking for namespace mnt                                           : PASS
   LXC: Checking for namespace pid                                           : PASS
   LXC: Checking for namespace uts                                           : PASS
   LXC: Checking for namespace net                                           : PASS
   LXC: Checking for namespace user                                          : PASS
   LXC: Checking for cgroup 'cpu' controller support                         : PASS
   LXC: Checking for cgroup 'cpuacct' controller support                     : PASS
   LXC: Checking for cgroup 'cpuset' controller support                      : PASS
   LXC: Checking for cgroup 'memory' controller support                      : PASS
   LXC: Checking for cgroup 'devices' controller support                     : PASS
   LXC: Checking for cgroup 'freezer' controller support                     : PASS
   LXC: Checking for cgroup 'blkio' controller support                       : PASS
   LXC: Checking if device /sys/fs/fuse/connections exists                   : PASS

and this :

> &#9679; libvirtd.service - Virtualization daemon
     Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2021-07-28 13:18:31 CEST; 41min ago
TriggeredBy: &#9679; libvirtd-admin.socket
             &#9679; libvirtd-ro.socket
             &#9679; libvirtd.socket
       Docs: man:libvirtd(8)
             [https://libvirt.org](https://libvirt.org)
   Main PID: 2091 (libvirtd)
      Tasks: 21 (limit: 32768)
     Memory: 49.3M
     CGroup: /system.slice/libvirtd.service
             &#9500;&#9472;2091 /usr/sbin/libvirtd
             &#9500;&#9472;2405 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
             &#9492;&#9472;2406 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper

Jul 28 12:45:30 Z390-AORUS-PRO libvirtd[2091]: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied
Jul 28 12:45:30 Z390-AORUS-PRO libvirtd[2091]: Failed to probe capabilities for /usr/local/bin/qemu-system-x86_64: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: internal error: libxenlight state driver is not active
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: End of file while reading data: Input/output error
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: invalid argument: could not find capabilities for arch=x86_64 domaintype=qemu 
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: internal error: Cannot find suitable emulator for x86_64
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied
Jul 28 13:58:54 Z390-AORUS-PRO libvirtd[2091]: Failed to probe capabilities for /usr/local/bin/qemu-system-x86_64: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied
Jul 28 13:59:06 Z390-AORUS-PRO libvirtd[2091]: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied
Jul 28 13:59:06 Z390-AORUS-PRO libvirtd[2091]: Failed to probe capabilities for /usr/local/bin/qemu-system-x86_64: internal error: Failed to start QEMU binary /usr/local/bin/qemu-system-x86_64 for probing: libvirt:  error : cannot execute binary /usr/local/bin/qemu-system-x86_64: Permission denied


---

### Post by MAFoElffen on 2021-07-28
Just because Qemu/KVM is installed does nott mean everything is running and setup right... It just means it is installed and things are capable fo possibly working. It's possible to have it installed and part of it working... If KVM is not working, it will still run, but with depricated performance, because it is not getting hardware virtualization, just using the software virtualization of Qemu.
 
Please post the output of these:
```

grep -Eoc '(vmx|svm)' /proc/cpuinfo    #This will check if the virtualization flags are present in the CPU and/or the BIOS is configured as having it turned on...
sudo lsmod | grep kvm                  # This will check if the KVM kernel module is present in the kernel...
dmesg | grep -i -a5 kvm                # This will check if the KVM kernel module was loaded or if there was an error loading it...
sudo systemctl is-active libvirtd      # This will check if the libvirtd daemon is active. 
systemctl status livirtd               # This will check the libvirt daemon status in more detail, and check the communication of it's sockets to other services..
groups $USER | grep -i "(libvirt\|kvm)" # This will check if the current user is a part of the correct groups

```

Usually with that specific error... It will show up in the first 3 of those commands. If it is having trouble communicating with other services needed for virtualization, it will show up in the next 2 commands. 

If the current user is not a member of the correct groups, then that user will get permission errors running and accessing resources... That is usually a different error, but still should b checked.

---

### Post by deadflowr on 2021-07-28
Why is it looking in the /usr/local/bin directory?
Should be looking in the /usr/bin directory as that's where the qemu-system-x86 package installs it to.
Did you at some point install from source?

---

### Post by MAFoElffen on 2021-07-28
> **deadflowr said:**
> Why is it looking in the /usr/local/bin directory?
Should be looking in the /usr/bin directory as that's where the qemu-system-x86 package installs it to.
Did you at some point install from source?
Dang... That was a very good catch on those errors... I didn't see those... 

```
ls /usr/bin/ | grep -E '(qemu-system-x86_64|virt-install)'
```

Why is thel ibvirtd.service pointing to an empty/ incorrect directory?

EDIT:
I guess  what be be more specific/correct is to look at where his Qemu/KVM system thinks those are located...
```
virsh --connect qemu:///system capabilities | grep emulator
```

---

### Post by TheFu on 2021-07-28
I like to keep it simple:
```
$ kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
```

Whatever is pointing at  /usr/local/bin/qemu-system-x86_64 was probably installed outside the package manager. It is best to do everything inside the package manager for virtual machine tools.  Don't mix where qemu-kvm, libvirt-bin and virt-manager are installed from.  Keep those all from the same repo.  If you need the latest, use a PPA.  Don't go off and manually grab source code, then compile and install it.  That's what  /usr/local/bin/ tells us happened.

Getting KVM working isn't very hard these days, but trying a mixed install would be a bad idea.
If you don't have too much invested in setting up the KVM host, I'd do a fresh installation of the OS (20.04), patch everything, reboot, then do the standard installation.  Also, set the system with a static IP and only use the wired ethernet connections, never wifi.
```
sudo apt install qemu-kvm libvirt-bin virt-manager
```
Then logout and login, so your userid group membership is updated (must be in the libvirtd group).
Next I'd setup a network bridge for use by the VMs.  Depending on the security requirements, that could entail using PCI passthru of a dedicated PCIe NIC to a specific VM, but to start, a simple bridge in the /etc/netplan/ directory should be fine.
Setup password-less ssh access from the workstation you plan to use to manage the VM host.
And finally, run virt-manager from your management workstation, using the ssh+qemu:// connection URL in virt-manager. Run this as your normal userid, never root, never with sudo.

Now you are ready to use the virt-manager wizard to create VMs and install using ISO files.

---

### Post by MAFoElffen on 2021-07-28
I think there was just a a typo on the groups you should add yourself to after installing... There is no "libvirtd" group. The Debian Branch KVM Docs say to add yourself to the groups "libvirt" and "kvm" for our repo installed packages...

Most distribution libvirt packages are configured to run qemu as the qemu:qemu user. Debian and Ubuntu uses libvirt-qemu:kvm. Although Instructions for installing Qemu/KVM say that after installing, add yourself to the groups: kvm and lbvirt... If you are not a member of both those 2 groups, you cannot create or manage VM's. 

I also add myself to group libvirt-qemu, because as mentioned above, Debian branched KVM runs as libvirt-qemu:kvm user.  I'll explain why I do that below.

If you look at the UID+GID reported by your install's config/capabilities file like this:
```
virsh --connect qemu:///system capabilities | grep baselabel
```
As for instance on mine:
```

mafoelffen@Opti-Ubuntu-Main:~$ virsh --connect qemu:///system capabilities | grep baselabel
      <baselabel type='kvm'>+64055:+108</baselabel>
      <baselabel type='qemu'>+64055:+108</baselabel>

```
And look at the groups in own your system's group file
```

mafoelffen@Opti-Ubuntu-Main:~$ cat /etc/group | grep -E '(libvirt|kvm)'
kvm:x:108:mafoelffen
libvirt:x:137:mafoelffen,libvirtdbus
libvirt-qemu:x:64055:mafoelffen,libvirt-qemu
libvirt-dnsmasq:x:138:
libvirtdbus:x:998:

```
It shows two types, kvm and qemu, with a UID of libvirt-qemu (64055) and a GID of group kvm (108). If you look at the baseline of type qemu, it points to the same (64055:108). I think having both kvm and qemu there is for distro compatibilty...

If you are not a member of those groups, and if those baselines don't come up with those, then qemu/kvm and you do not have permissions to access /dev/kvm. As that relates back to this error code, if that is not how his is set on his, then libvirtd is will not advertise kvm support and will throw an error.saying KVM is not installed. (But his points back to a configuration error).

Then on the /dev/kvm permissions that is set at installation in Debian Branches as root:kvm, 660... But on rhel branches is set to their default as 666. I'm not sure why that difference is there... but it does help when running your own scripts from the commandline.

---

### Post by TheFu on 2021-07-28
I'm on ubuntu server:
```
$ lsb_release -d
Description:    Ubuntu 18.04.5 LTS
```
NOT Debian.

```
$ id
uid=1000(thefu) gid=1000(thefu) groups=1000(thefu),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),110(lxd),116(**libvirtd**),117(lpadmin),118(sambashare)
```

**libvirtd** appears to be the correct group here and should be automatically added to the userid that installed libvirt-bin (even via dependency). 

Oh man ...  more cat abuse.
```
cat /etc/group | grep -E '(libvirt|kvm)'
```
Srsly?  ;)  DO NOT USE CAT when it just wastes a process.  Leave the cat alone! ;)  I use tac more than cat. **tac** is actually useful.

```
$ egrep 'libvirt|kvm' /etc/group
```
or better
```
$ getent group|egrep 'libvirt|kvm' 
```

Don't know when libvirtd and libvirt happened, but both names are in my group DB, just with the same gid.  libvirtd is first in order, so that's what gets reported. My KVM systems have been upgraded since 10.04.

Regardless, the userid that does the install will be automatically added to the libvirt-whatever group as required.  Can't recall ever needing to add it manually, unless there was another userid involved that needed to control KVM.  

[https://askubuntu.com/questions/930491/group-libvirtd-does-not-exist-while-installing-qemu-kvm](https://askubuntu.com/questions/930491/group-libvirtd-does-not-exist-while-installing-qemu-kvm)   Looks like this is the answer:
> The group was renamed to libvirt for Ubuntu 16.10 and later
and rather than correct it in the group DB, they just added another groupname with the same gid. I can promise that I didn't manually add libvirt on any of my 4 KVM hosts. I've verified that 3 of them have both libvirtd and libvirt groups.  Can't easily check the other system. It is in standby in another part of the house.

Anyway - while I didn't intend for libvirt to be typed, since 2017, that does appear to be the new, correct, answer. Just another data point that only experience teaches.

---

