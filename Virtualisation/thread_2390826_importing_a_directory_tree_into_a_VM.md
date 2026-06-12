---
title: "importing a directory tree into a VM"
date: 2018-05-03
forum: Virtualisation
---

### Post by Skaperen on 2018-05-03
**is there any VM implementation, yet, that can import a directory tree from the host instead of a virtualized block device, and not via NFS?**  i would expect this will also need a new file system type on the guest OS (i'm intending to only run a variety of Linux things this way ... no Windows for me) to see the file system.  i am wanting to import the guest root (/) file system this way.

---

### Post by ajgreeny on 2018-05-03
I'm not totally sure what you want to do but if you have sharing set up in the system between the host and guest you should be able to simply drag and drop a folder using the file manager or use a **cp -R** command, or similar, to copy across the folder recursively.

If I've misunderstood your question come back again with more detail.

---

### Post by Skaperen on 2018-05-03
my goal is to have the root file system (/) of the guest (Linux) reside in the host (Linux) system as some exported directory tree. normally, the guest root file system is mounted on a block device as it appears in the virtual machine with backing store in the host system usually as a large file, but sometimes as a partition as seen by the host on on of its own block devices.  i have set up VMs both of these ways, many times.  another way that can be done when the opportunity to configure the kernel exists and networking is set up for this is to use NFS.  the guest will be the NFS client mounting as / and the host will run an NFS server, exporting one or more file systems or directory trees.  this allows both guest and host to see the same files (stored by the host).  i have been away from VMs for a few years and have noticed a lot of development has taken place and have wondered if any of it has implement what i consider to be the "holy grail" of VM deployment.  this would involve the virtualization support or emulator to have some code to pass along virtual file system i/o requests to the host OS as regular i/o operations.  it would then create a means for the guest OS to pass file system i/o requests to it, more like NFS but not with the networking.  the guest kernel would then need a virtual file system module that can allow mounts (including at / if compiled in).  i do know Linux has a lot of new virtual file system implementations.  this feature can be one of those.

---

### Post by TheFu on 2018-05-04
Do you mean like a Linux container?  These are commonly used there.  I've never seen this provided in VMs, since it breaks the limited access part of VMs, which is a key security consideration.

If I'm reading it correctly, what you seek has real security and VM breakout concerns for the host and VM. 
I'm probably misunderstanding.

In theory, any device can be passed thru using VT-d. Nothing says that device can't be a file system, but almost always, file systems have built-in protection to prevent being opened by different processes as a way to prevent corruption. This is why Linux won't read an NTFS partition that wasn't properly closed by Windows.  OTOH, networked file systems have methods to deal with multiple locks for safety.

You can always use rsync, sftp, to "import" a directory tree into a Guest VM.  But that will make a copy.  

Vbox makes something called vboxsf which connects local host storage to a VM, but I've had locking failures with it and ended up using NFS instead.

---

### Post by Skaperen on 2018-05-05
i am talking about a virtual machine or a machine emulator such as QEMU in system mode.  yes, there is a security concern if the host system has untrusted users on it.  this is not the case for me.

copying the files with tools like rsync and sftp is not achieving my intended goal.  i want to run the guest system on the imported (and mounted as /) file system.  i have done this in the past with NFS.  but using NFS requires more host side setup (NFS server exporting the directory trees).

i was hoping to see this better integrated by now.

another way to do this is to have the virtual machine or emulation software create an internal NFS server that is securely presented only to the guest it is running.  if this is enabled for system root mode, then it would pass a default parameter string to the guest kernel to have it access NFS and mount the proper IP address NFS as mount point /

i did mention i wanted something not NFS.  but the above scheme would meet my desires.

if this has not been implemented, _and apparently it has not_, then i will need to just use NFS.  i want to have no virtual disks.

---

