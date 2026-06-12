---
title: "Consolidating 2 bare metals into one"
date: 2023-06-19
forum: Server Platforms
---

### Post by aljames2 on 2023-06-19
Currently, my backup server is on a separate subnet (nic) running on a bare metal computer, nothing else on that computer.

I have another box on a separate subnet running KVM hypervisor with 2 VMs for:   Wireguard VPN & Nextcloud.

I am thinking if I could consolidate the backup server into the KVM host box by running the backup server in a VM and passing through a separate NIC to the backup server only, keeping it on a separate physical network from the host and other guests?  I think the networks could be isolated in this way, but I don’t see how to isolate the backup storage drives from the host.

Perhaps too risky.

Trying to save some real estate in my home office, too many computers.

I do have a Raspberry Pi 4 laying around doing nothing.

---

### Post by MAFoElffen on 2023-06-19
Trick question, right?

You pass the partitions through to the VM Guest, just like you do with a NIC. Once they are passed through, they are not available on the host.

You can do this easily from Virtual Manager, or using the virsh attach-disk command
```

virsh attach-disk Guest1 /dev/sdd4 vdc

```
The XML will look similar to
```

<disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none'/>
      <source dev='/dev/sdd4'/>
      <target dev='vdc' bus='virtio'/>
</disk>

```

---

### Post by aljames2 on 2023-06-19
I knew I was missing something simple here.  So admittedly, not a trick question. :)
Is there an emoji for embarrassed.

I have never tried this before, I could clearly see how to isolate the networks on the same machine, but for some reason having the storage attached to the host machine caused me some pause.

---

### Post by MAFoElffen on 2023-06-20
In KVM, adding physical disks to a VM as a resource is referred to in the storage management section of their doc's as a "Disk Pool": [https://libvirt.org/storage.html#disk-pool](https://libvirt.org/storage.html#disk-pool)

You can also use LVM LV's, ZFS datasets, iSCSI, Gluster, NFS Shares... and many more, as VM disks: [https://libvirt.org/storage.html](https://libvirt.org/storage.html)

I have to admit, there are types there that I have never heard about. And I have done IT for a long time. LOL

EDIT: I went through that about 10 years ago. My home lab had 14 servers, 7 desktops, and 3 laptops. I downsized and consolidated them down drastically, putting most of them into VM's. I did learn to think about things a bit differently. One of those things was how I did storage management: NFS Shares and ZFS Pools. Those kinds of things I can now migrate from one system to another, easily.

---

