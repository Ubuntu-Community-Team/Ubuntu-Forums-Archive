---
title: "Virtualization with physical disk access"
date: 2009-03-17
forum: Virtualisation
---

### Post by kextyn on 2009-03-17
I'm currently running VMWare Server 1 on Ubuntu Server.  I'm wondering what alternatives there are to VMWare Server 1 that will allow physical disk or partition access without losing any data on the drive.

I have a VM running that has physical access (actually I think it's partition, not full disk) to two drives.  The reason I did this is because it's my torrent seeding box and I didn't want huge virtual drives.  I also like knowing that if my VMWare setup gets fubared I can always remove the disks and access them from any Windows installation (they're NTFS partitions.)  So if I use another Virtualization product I'd like to do the same, unless someone can convince me that having 80GB+ virtual drives is better.

I was thinking about going to a hypervisor like ESX or Hyper-V but that brings up problems with my Ubuntu Server.  The main purpose of my server is a file server with Linux software RAID (mdadm.)  I've heard that the free version of ESX doesn't allow physical drive access (could be wrong, I just remember hearing this somewhere and haven't researched it) and I know that Hyper-V requires no partitions on the drive before letting a VM have direct access (according to all the Technet threads I've seen.)

VWMare Server 1 is working fine for me right now but I'm not sure how much longer it's going to be supported now that VMWare Server 2 is out (with no direct drive access.)  I'm probably going to end up using VWMare Server for the foreseeable future but I'd like to try alternatives to see what works best for me.

---

### Post by bodhi.zazen on 2009-03-17
You can very easily access physical partitions with KVM (assuming you have the hard ware) or virutalBox.

To be honest, IMO you are being a little "silly", virtual Hard drives are portable as well (and you can convert formats).

I would call that which you seek "Backups" :twisted;

---

### Post by Brazen on 2009-03-18
My rule of thumb has been, if it's bigger than 20GB, I don't use a virtual disk.  Or if it needs the space of the entire physical drive, then I don't use a virtual disk.

I use KVM with libvirt, and it very easily allows access to physical disks.  In fact, I do that same thing with a home file server using RAID 1 with access directly to the physical disks.  Qemu with Kqemu would also work the same way, in case your hardware does not support KVM.

---

### Post by kextyn on 2009-03-18
I'm trying out a virtual disk today. I set it to 250GB and didn't allocate the space at once.  So now I have over 100GB of files being transferred from the physical disks to the virtual disk.  I'll be running some benchmarks and monitoring the CPU usage on the server, but I usually have very low resource usage anyway so it shouldn't get in the way of anything.

---

