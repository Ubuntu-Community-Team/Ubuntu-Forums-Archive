---
title: "LXC Ubuntu22.04 VM + XFS. Nonstandard args?"
date: 2024-07-25
forum: Virtualisation
---

### Post by errolflynn on 2024-07-25
I'm setting up a demo k8s cluster for use with [MinIO storage system]([https://min.io](https://min.io)). I've encountered issues with the nodes running on LXC/LXD with Ubuntu 22.04. [According to one of the MinIO project members]([https://github.com/minio/directpv/issues/919](https://github.com/minio/directpv/issues/919)), the failures are due to non-standard arguments supported for XFS. Does anyone know if this is true and how to check or correct it? It seems like the default kernel for the LXD Ubuntu22.04 VM is based on 5.15 and with some modifications for kvm. It seems like XFS is working on some level, but may not support all arguments used by [DirectPV]([https://github.com/minio/directpv](https://github.com/minio/directpv)) for setting up the storage drives

```
root@ubuntu-k3s-homelab-4:~# uname -a
Linux ubuntu-k3s-homelab-4 5.15.0-1062-kvm #67-Ubuntu SMP Wed Jun 19 13:44:51 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
# Create test xfs filesystem, showing reflink supported
root@ubuntu-k3s-homelab-4:~# mkfs.xfs /dev/sde
meta-data=/dev/sde               isize=512    agcount=4, agsize=2752512 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=1, sparse=1, rmapbt=0
         =                       reflink=1    bigtime=0 inobtcount=0
data     =                       bsize=4096   blocks=11010048, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0, ftype=1
log      =internal log           bsize=4096   blocks=5376, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
Discarding blocks...Done.
root@ubuntu-k3s-homelab-4:~# mount /dev/sde /mnt/test
root@ubuntu-k3s-homelab-4:~# df -hT /mnt/test/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sde       xfs    42G  332M   42G   1% /mnt/test
```


Unable to setup due to invalid arg with XFS

```
&#10140;  ~ kubectl directpv discover

 Discovered node 'ubuntu-k3s-homelab-3' &#10004;
 Discovered node 'ubuntu-k3s-homelab-4' &#10004;
 Discovered node 'ubuntu-k3s-homelab-5' &#10004;
 Discovered node 'ubuntu-k3s-homelab-kubernetes-2' &#10004;

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; ID                  &#9474; NODE                 &#9474; DRIVE &#9474; SIZE    &#9474; FILESYSTEM &#9474; MAKE               &#9474; AVAILABLE &#9474; DESCRIPTION &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474; 8:0$lEwxKEUO56Nv... &#9474; ubuntu-k3s-homelab-4 &#9474; sda   &#9474; 42 GiB  &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:32$guHrIB+MilW... &#9474; ubuntu-k3s-homelab-4 &#9474; sdc   &#9474; 42 GiB  &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:48$6v3flv4STNc... &#9474; ubuntu-k3s-homelab-4 &#9474; sdd   &#9474; 42 GiB  &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:64$2M83bdXhXgW... &#9474; ubuntu-k3s-homelab-4 &#9474; sde   &#9474; 42 GiB  &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:16$xIJClQ3ZRhX... &#9474; ubuntu-k3s-homelab-5 &#9474; sdb   &#9474; 190 GiB &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:32$CYsmluXJnIB... &#9474; ubuntu-k3s-homelab-5 &#9474; sdc   &#9474; 190 GiB &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:48$dmx9SRkh27g... &#9474; ubuntu-k3s-homelab-5 &#9474; sdd   &#9474; 190 GiB &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9474; 8:64$qbOcPZbdJTY... &#9474; ubuntu-k3s-homelab-5 &#9474; sde   &#9474; 190 GiB &#9474; -          &#9474; QEMU QEMU_HARDDISK &#9474; YES       &#9474; -           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

&#10140;  ~ kubectl directpv init drives.yaml --dangerous

 &#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;&#9617;  50%

 Processing initialization request '8045f27a-e55b-4f64-8a64-b25b6dd8efa5' for node 'ubuntu-k3s-homelab-5' &#8729;&#8729;&#8729;
 Processing initialization request 'e91bb963-9d67-4d7f-b05e-6d16e8765076' for node 'ubuntu-k3s-homelab-4' &#8729;&#8729;&#8729;

 Error; unable to initialize devices; context deadline exceeded 

&#10140;  ~ kubectl logs -f node-server-vv5f9 -n directpv -c node-controller
I0725 19:01:24.975211    7952 reflector.go:289] Starting reflector *v1beta1.DirectPVNode (5m0s) from k8s.io/client-go@v0.28.11/tools/cache/reflector.go:229
I0725 19:01:24.975447    7952 reflector.go:325] Listing and watching *v1beta1.DirectPVNode from k8s.io/client-go@v0.28.11/tools/cache/reflector.go:229
I0725 19:01:25.075027    7952 controller.go:141] node controller synced and ready
E0725 19:01:25.372691    7952 event.go:310] "unable to create initrequest event handler" err="unable to mount; invalid argument"
E0725 19:01:25.372940    7952 main.go:147] "unable to execute command" err="initrequest controller stopped"
```

---

### Post by TheFu on 2024-07-25
I know nothing about XFS. Haven't used it myself on any Linux, just on Irix.  In the old days, XFS was the choice for performance and huge file system support.  ext4 solved most of those things and works really great with LVM, allowing extending and reducing a file system much easier than XFS.

I know less than nothing about k8. Sorry.

LXC runs containers, not VMs.  Containers are light because they share the kernel from the host system. Not just any kernel can be used. There are some specific options that have to be enabled to support Linux containers. With an Ubuntu host and I imagine almost any other mainstream Linux distro, those options should be enabled already.  There are probably exceptions, but I've never seen any that didn't support containers since before 2015, perhaps 2010.  I don't really recall.

If you want control the kernel, you should use a full VM, like KVM+QEMU supports.

LXD really wants the block storage for each container to be ZFS storage. I find it a bit frustrating, but that's likely just my ignorance and the LXD team's love of ZFS so they don't bother using terms that LVM admins easily understand.

Sorry if this post isn't helpful at all. Hopefully someone with knowledge will post.

---

