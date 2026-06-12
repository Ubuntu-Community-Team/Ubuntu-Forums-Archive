---
title: "VM-Builder: 'unpacking' takes a lot of time..."
date: 2011-03-29
forum: Virtualisation
---

### Post by FiVAL on 2011-03-29
Hi Hi Everybody,

after some testing with the vmbuilder AND a local mirror
with all the packages, the system still needs more than
12 minutes for a clean and minimum VM-image...

Is there a way to speed this proces up?

With the --debug option I found out that the 'unpacking'
task takes, by far, the most time of building a VM...

---

I'm testing on three Ubuntu Server (10.04) KVM/QEmu Hosts
on three new Dell PowerEdge R310 RackServers.

The 64bit host os's are installed on two 2Tb mirrored SataHDDs
with Ext4.


Thx in Advanced for any ideas..!!

---

### Post by FiVAL on 2011-03-31
I know it for SURE..!

When I change the **/tmp** of the host OS from EXT4 to EXT3,
my vmbuilder builds the same VM in _less than 4 minutes_!!!!!
(in stad of more than 12 minutes)


Now I only have an other problem :sad:

When I build to a RAW logica volume (lvm),
the GUEST OS gives the following error:

EXT4-fs error (device sda1): ext4_mb_generate_buddy:
EXT4-fs group 2: 3431 blocks in bitmap, 3597 in gd

This looks like an conversion error from EXT3 to EXT4
on the guest OS!??


By the way...
When I build to a QCOW2 file, everything is/looks fine!!!

---

### Post by FiVAL on 2011-04-01
Some extra info about EXT3 and EXT4 partition:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance regressions with ext4 under certain workloads]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Performance regressions with ext4 under certain workloads")

---

### Post by FiVAL on 2011-04-04
Just to keep this topic also informed...

You could subscribe to the bug report I made friday:
[https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/747068]("https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/747068")

For now, I build my VM's the following way:

1.) VMBuilder (with the EXT3 /tmp partition) to a QCow2 file
2.) Convert the QCow2 file to a RAW file
3.) Create a new LVM logical volume
4.) sudo dd if=disk0.raw bs=512k of=/dev/vg-1/VM01-Disk0 (don't forget the option bs=512k !!)
5.) Minor adjustment to the xml in /etc/libvirt/qemu/

<disk type='block' device='disk'>
  <driver name='qemu' type='raw' cache='none'/>
  <source dev='/dev/vg-1/VM01-Disk0'/>
  <target dev='vda' bus='virtio'/>
</disk>

6.) :-) Done!

Today I'll try to script this...
Only #5 will be (for me) a difficult one.


By the way!
Some people have the following problem with VMBuilder:

"*First everything seems to work ok, but soon after certain volume of traffic goes through the thing will freeze for a while. For example, I start copying 500 mb file. I will get 200 MB done superfast (50MB/s). Then everything will freeze for a while. After that copying resumes a bit slower for a few seconds and again, everything freezes.*"

This is because the QCow2 files. When you use RAW files or (just like me) a LVM logical volume. This problem is solved...

---

