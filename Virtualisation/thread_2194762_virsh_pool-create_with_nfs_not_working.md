---
title: "virsh pool-create with nfs not working"
date: 2013-12-20
forum: Virtualisation
---

### Post by kdf on 2013-12-20
I'm relatively new to KVM and libvirt and hoping someone can provide some assistance or guidance creating nfs pools for guest machines.  I've tried to read up but am stumped.  Any ideas or guidance would be appreciated.

I'm unable to get a net-fs (nfs) pool created using virsh pool-create (on Ubuntu server 13.10).  I'm using standard apt packages for kvm, nfs-client, libvirt etc.

I'm running this command (on the KVM server):
sudo virsh pool-create --file nfs-libvirt-pool.xml

I get this error:
error: Failed to create pool from nfs-libvirt-pool.xml
error: cannot open path '/var/lib/libvirt/images/local-mount-point': Permission denied

The directory permissions appear correct and I am able to manually mount the directory to the mount point and use the mount point.  However when I create a net-fs pool it fails with the above error.  The user group for my mount directory is libvirtd and I've set permissions using chmod a+rwx so all users should have permission to the local mount directory:

drwxrwxrwx 2 root users 4096 Dec 20 13:02 local-mount-point


The content of "nfs-libvirt-pool.xml":
<pool type="netfs">
  <name>virtimages</name>
  <source>
    <host name="my-nfs-server"/>
    <dir path="/path/to/mount"/>
    <format type='nfs'/>
  </source>
  <target>
    <path>/var/lib/virt/images/local-mount-point</path>
  </target>
</pool>

---

### Post by TheFu on 2013-12-20
A shot in the dark, but did you "define" the pool already? Is that needed?

I handle storage outside virsh, so I'm not much help.

---

### Post by kdf on 2013-12-21
The pool is new and undefined.  I was attempting to create and start the nfs based pool but every attempt to do so leads to a "permissions denied" error.  My latest theory has to do with the nfs server.  I'm using a Storcenter IX2.  The IX2 only support NFS3 and I'm wondering if the virsh command is attempting to use NFS4 instead.  If I come to any solution I'll post it. 

> **TheFu said:**
> A shot in the dark, but did you "define" the pool already? Is that needed?

I handle storage outside virsh, so I'm not much help.

---

### Post by TheFu on 2014-08-29
So, I'm running into this myself now - attempting to use an NFS storage pool.
The export from the NFS server allows remote root - this is critical and when I mount it, the local root can create files/directories with root.root ownership.  libvirtd exists on both systems - same uid too.

I found a Redhat advisory [https://bugzilla.redhat.com/show_bug.cgi?id=589922](https://bugzilla.redhat.com/show_bug.cgi?id=589922) about SE-Linux settings to allow nfs use for libvirt.  Have not found the equiv advisory for Ubuntu's apparmor ... yet.  I need to look more.

I tested the mount - location created by libvirt and it does not allow any files to be created by users or libvirtd or root. /var/lib/libvirt/images/romnfs
Here's the mounts:
romulus:/raid/media/VMs            1.8T  729G 1003G  43% /var/lib/libvirt/images/romnfs
romulus:/raid/media/VMs            1.8T  729G 1003G  43% /VMs

Under /VMs - it works.
Under ..../romnfs - it doesn't. 
The mount source is identical with rw,no_root_squash,async options on the NFS server side.

Without NFS controlled by libvirt, live-migrations can't work.

Did you find a solution?

---

