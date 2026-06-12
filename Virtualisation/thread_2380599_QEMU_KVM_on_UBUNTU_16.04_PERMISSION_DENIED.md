---
title: "QEMU KVM on UBUNTU 16.04 PERMISSION DENIED"
date: 2017-12-19
forum: Virtualisation
---

### Post by mercxi on 2017-12-19
I am trying to add qemu arguments to my vm.  However I am constantly running into an issue with a newly created file that I put into the temp directory, /tmp/ivshmem_socket, in which when I start my domain using virsh I am getting the following error message:
error: internal error: process exited while connecting to monitor: 2017-12-19T14:49:54.446516Z qemu-system-x86_64: -chardev socket,path=/tmp/ivshmem_socket,id=ivshmem: Failed to connect socket: Permission denied

for my setupon /etc/libvirt/qemu.conf
I made the following changes:
```
# Some examples of valid values are:
#
#       user = "qemu"   # A user named "qemu"
#       user = "+0"     # Super user (uid=0)
#       user = "100"    # A user named "100" or a user with uid=100
#
#user = "root"
user = "root"
group = "root"
```


I also rebooted after that as well, please let me know what I am doing wrong?

---

### Post by KillerKelvUK on 2017-12-20
Hey, have you checked to see whether apparmor is denying the file access?

---

### Post by mercxi on 2017-12-21
so it appears there is a bug with apparmor
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1733700](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1733700)

Is there a way around using apparmor for qemu/kvm?

---

### Post by KillerKelvUK on 2017-12-21
Yeah, you can edit the AA profile for kvm to include the /tmp directory but I'm not sure if that's what you say is buggy, would be surprised if that's the case.  Alternatively you can put AA into complain mode which will stop it denying access but you will still get log entries about contraventions.  You could disable AA altogether.  Or most simply just re-edit your qemu arguments so you aren't putting files into locations that are outside of the AA profile scope aka home directory maybe?

---

### Post by mercxi on 2017-12-21
I cannot put it in complain mode, that is the bug I am seeing:
sudo aa-complain foo

ERROR: Syntax Error: Unknown line found in file /etc/apparmor.d/snap.core.3440.usr.lib.snapd.snap-confine line 15:
    include "/var/lib/snapd/apparmor/snap-confine.d"   /etc/ld.so.cache r,


How do I edit the AA profile for kvm?

---

### Post by KillerKelvUK on 2017-12-21
Have you confirmed AA is denying the file access?  So the profiles are stored in /etc/apparmor.d/ google around there are plenty of syntax references but basically you're including the path into the scope of the application and associated AA profile.

If you are unsure if AA is the problem the first place to check is 'dmesg', AA will write a log out showing the deny for the specific profile, you can then use that shown profile to locate the file in the /etc/apparmor.d/ path.

Regards aa-complain, I don't get your problem as it works for me but then this profile isn't anything to do with KVM/Qemu so not sure why you'd be trying to put that into complain mode?

```

:~$ sudo aa-complain usr.lib.snapd.snap-confine.real
Setting /etc/apparmor.d/usr.lib.snapd.snap-confine.real to complain mode.
:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

```

---

### Post by mercxi on 2017-12-21
What version of snapd and appaemor are you using?

I also am positive that I am running intoa  bug since I actually added my issue to different bug on bugs.launchpad.net and the moderator actually redirected me to the link I put above.  One thing I am interested in is editing the aa profile, but I do not know which aa profile I need to edit, is it:
/etc/apparmor.d/usr.lib.libvirt.virt-aa-helper
or
/etc/apparmor.d//libvirt/libvirt-591efeba-43f3-474c-9820-ea537debe1bb

Or am I looking in the wrong spot?

---

### Post by KillerKelvUK on 2017-12-22
So like I say the dmesg output will confirm the profile name you need to be looking for, I'd suggest it is the one named "libvirt-591efeba-43f3-474c-9820-ea537debe1bb".  I believe you are looking in the right place.

```

:~$ dpkg -l snapd apparmor
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                   Version                          Architecture                     Description
+++-======================================================-================================-================================-==================================================================================================================
ii  apparmor                                               2.11.0-2ubuntu17                 amd64                            user-space parser utility for AppArmor
ii  snapd                                                  2.29.4.2+17.10                   amd64                            Daemon and tooling that enable snap packages

```

---

