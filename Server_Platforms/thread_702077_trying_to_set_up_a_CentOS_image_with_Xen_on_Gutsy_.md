---
title: "trying to set up a CentOS image with Xen on Gutsy (amd64)"
date: 2008-02-19
forum: Server Platforms
---

### Post by jlapier on 2008-02-19
Hey all - 

On Gutsy (amd64) and I installed the ubuntu-xen-desktop-amd64 package. Then I tried to create an image for CentOS 4 with this:

```
xen-create-image --dist centos4 --hostname=xen-centos --dhcp --ide --dir /home/jason/xens --memory 256Mb --swap 256Mb --size 8Gb --force  --install-method=rpmstrap
```

After it creates the image and the ext3 filesystem, it tries install CentOS and fails. Here's the log file:

```
General Information
--------------------
Hostname       :  xen-centos
Distribution   :  centos4
Fileystem Type :  ext3

Size Information
----------------
Image size     :  8Gb
Swap size      :  256Mb
Image type     :  sparse
Memory size    :  256Mb
Kernel path    :  /boot/vmlinuz-2.6.22-14-xen
Initrd path    :  /boot/initrd.img-2.6.22-14-xen

Networking Information
----------------------
IP Address     : DHCP

Creating swap image: /home/jason/xens/domains/xen-centos/swap.img
256+0 records in
256+0 records out
268435456 bytes (268 MB) copied, 3.96921 seconds, 67.6 MB/s
Done

Creating disk image: /home/jason/xens/domains/xen-centos/disk.img
0+0 records in
0+0 records out
0 bytes (0 B) copied, 3.4015e-05 seconds, 0.0 kB/s
Done

Creating ext3 filesystem on /home/jason/xens/domains/xen-centos/disk.img
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
1048576 inodes, 2097152 blocks
104857 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2147483648
64 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: 23/64
48/64
done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 34 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
Done
Setting up swapspace version 1, size = 268431 kB
no label, UUID=7f4495fb-edd5-4c1a-a74e-cc4cb11d20b0
Installation method: rpmstrap
rpmstrap: warning: target directory /tmp/vvTfbYbFtS already exists
setup-2.5.37-1.3.noarch.rpm: not an rpm package (or package manifest): 
rpmstrap: critical error: command "rpm --install   --root /tmp/vvTfbYbFtS --dbpath /tmp/vvTfbYbFtS/var/lib/rpm setup-2.
5.37-1.3.noarch.rpm" failed
The installation of the new system has failed.

The system is missing the common file: /bin/ls
Done
System installation failed.  Aborting

```

I'm not really sure what's going wrong. Seems to be trying to extract the setup rpm and failing. Anyone have any guesses?

Thanks,

Jason

---

### Post by chefkoch666 on 2008-02-21
Hi,
same problem over here, still googling.
Greetz,
Marek

---

### Post by chefkoch666 on 2008-02-21
Followed instructions over here and applied the patch but got the same error??

[https://bugs.launchpad.net/xen/+bug/148005](https://bugs.launchpad.net/xen/+bug/148005)

---

### Post by jlapier on 2008-02-23
Yeah, it seems the rpmstrap script is definitely out of date. You could try the script provided here for CentOS4.4: [http://www.cryptronic.de/patches/rpmstrap/](http://www.cryptronic.de/patches/rpmstrap/)

Or you could try the perl script here to generate the rpmstrap script: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=359140](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=359140)

You could try grabbing the most recent xen-tools which seems to eb a little more up-to-date (if not, the mercurial repository is very recent): [http://www.xen-tools.org/software/xen-tools/](http://www.xen-tools.org/software/xen-tools/)

There are also some pre-made images you can try, such as on this site: [http://jailtime.org/](http://jailtime.org/)

I haven't had time to mess with any of these possible fixes, except I did try the  centos 5.1 image on jailtime and it wouldn't boot up (Kernel panic because it couldn't mount the filesystem). 

Hope this helps, and please let me know if you have any success.

---

