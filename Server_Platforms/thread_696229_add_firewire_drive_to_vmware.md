---
title: "add firewire drive to vmware"
date: 2008-02-13
forum: Server Platforms
---

### Post by Pitt Stains on 2008-02-13
Hi, I have a firewire drive that I'd like to add to one of my virtual machines.  I'm running Ubuntu 7.10 Server Edition on the host machine as well as all the VMs, and I'm using VMware Server Console 1.0.4 build-56528.

I've passed USB drives and other devices to the VMs before by clicking "Edit virtual machine settings" from the console and using the "Hardware" tab.  When I click "Add..." I get options for adding Hard Disk, DVD/CD-ROM Drive, Floppy Drive, Ethernet Adapter, Sound Adapter, USB Controller, Serial Port, Parallel Port, or General SCSI Device.  I was hoping to see "Firewire Device" or something like that in the list of choices, but no such luck.

Is this simply not possible with this software?

Thanks,
-Pitt

---

### Post by HermanAB on 2008-02-14
Mount it in the Host system, then share it.

---

### Post by Pitt Stains on 2008-02-14
Thanks!  I know how to mount it in the host system, but I'm not sure how I'd share it.  Would I do that via Samba -- that's probably not necessary since both systems are Linux, right?

---

### Post by HermanAB on 2008-02-14
Sharing depends on your VMware version.  VMware Server doesn't seem to have the ability to share a host directory built in - VMware Workstation does however.  So with Workstation, it is a no-brainer.  With Server, you would need to run a NFS, Samba or FTP client in the VM and a corresponding server on the host system.

Hope that helps

H.

---

### Post by Pitt Stains on 2008-02-14
Thanks, Herman,

Seems like the easiest thing to do here is just use the USB interface on the device.  I'm probably sacrificing a bit on speed, but I guess maybe it would have been wiser to deploy this machine on real hardware rather than virtualized hardware.

-Pitt

---

