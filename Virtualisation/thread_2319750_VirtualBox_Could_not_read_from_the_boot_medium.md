---
title: "VirtualBox Could not read from the boot medium"
date: 2016-04-06
forum: Virtualisation
---

### Post by jaynv0i on 2016-04-06
I have an Ubuntu 14.04 physical server which I am attempting to virtualize.

Following are the steps I have followed.
 - Create an image of the drive.  dd if=/dev/sdb of=server.raw bs=1024
 - Create a VDI using VBoxManage.  VBoxManage convertdd server.raw TestServer.vdi --format VDI --variant Fixed
 - Created a virtual machine using TestServer.vdi as the disk.

When I attempt to boot the virtual machine, I receive a message stating, "FATAL: Could not read from the boot medium!  System halted."

I started the VM using an Ubuntu CD and checked the partitions.  They match the physical system exactly and the fstab on the virtual system matches the physical system exactly.

UUIDs are used in fstab and they match on the physical and virtual systems.

Any suggestions as to why the VM will not boot would be greatly appreciated.

Thank you!

---

### Post by jaynv0i on 2016-04-06
It is probably very helpful if I include all of the necessary information in my posts.  VirtualBox 4.3.36 which was installed from the repositories and has the extensions installed is running on Ubuntu 14.04.

I do not know if it matters or not, but the drive in the server I am attempting to virtualize is a SSD.

Thank you!

---

### Post by jaynv0i on 2016-04-06
I might have found something, but I am not sure.  The raw image is 64023257088 bytes, but the completed image is only 61058MB.  Should the completed image be 64023 MB?  The size is being reported as 61057 MB.

Thank you!

---

### Post by jaynv0i on 2016-04-06
This has been solved.  It was a brain fart on my part.  I forgot the system was using UEFI.  Once I changed the system settings to enable EFI, I was able to boot the system without any problems.

Thank you everyone for taking the time to read my posts, and I hope this prevents a headache for someone in the future.

---

