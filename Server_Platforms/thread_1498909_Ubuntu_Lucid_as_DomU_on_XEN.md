---
title: "Ubuntu Lucid as DomU on XEN"
date: 2010-06-01
forum: Server Platforms
---

### Post by arjun.prakash on 2010-06-01
I have a XEN Dom0 running on Linux version 2.6.16-xen (root@pachy) (gcc version 4.1.0 20060304 (Red Hat 4.1.0-3)).

> #xm info
host : localhost.localdomain
release : 2.6.16-xen
version : #3 SMP Wed Sep 3 20:58:06 EDT 2008
machine : i686
nr_cpus : 1
nr_nodes : 1
sockets_per_node : 1
cores_per_socket : 1
threads_per_core : 1
cpu_mhz : 1862
hw_caps : 0febfbff:20100000:00000000:00000140:00002201:00000000:00000001
total_memory : 968
free_memory : 715
xen_major : 3
xen_minor : 0
xen_extra : .2-2
xen_caps : xen-3.0-x86_32
platform_params : virt_start=0xfc000000
xen_changeset : Thu Apr 13 15:18:37 2006 +0100 9617:5802713c159b
cc_compiler : gcc version 4.1.0 20060304 (Red Hat 4.1.0-3)
cc_compile_by : root
cc_compile_domain : (none)
cc_compile_date : Wed Sep 3 19:26:56 EDT 2008

I created a DomU Ubuntu 10.04 using the following steps:
dd if=/dev/zero of=ubuntu_10.04 bs=1024k count=8000
mkfs.ext3 ubuntu_10.04
mkdir mp
mount -o loop ./ubuntu_10.04 ./mp/
debootstrap --arch i386 lucid mp
update /etc/fstab, /etc/network/interfaces

The DomU's configuration file contains
kernel = "/boot/vmlinuz-2.6-xen"
which is the kernel used by Dom0.

When I start this DomU, I get the following error:

init: ureadahead main process (665) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (668) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

After logging into the maintenance shell, I could see that the root filesystem is mounted, but the services - like networking, ssh are not up. Is this problem related to upstart? I could not downgrade the upstart version as mentioned in [http://ubuntuforums.org/showthread.php?p=8548144](http://ubuntuforums.org/showthread.php?p=8548144) - it breaks the requirement for Lucid.

Are there ready to use DomU images for Ubuntu Lucid? I tried using an image from Ubuntu Enterprise Cloud ([http://uec-images.ubuntu.com/lucid/20100224/](http://uec-images.ubuntu.com/lucid/20100224/)). For this image, the root filesystem did not mount and an emergency shell was started. :confused:

Is this due to incompatibility with my Dom0 kernel?

Any help or suggestion is highly appreciated.. Thanks

---

### Post by alexm@nus.edu.sg on 2010-11-14
I had what looks like the same problem in 9.10, which I posted about here
[http://ubuntuforums.org/showthread.php?t=1409157](http://ubuntuforums.org/showthread.php?t=1409157)

I have kept my server up and running by following the instructions to manually get it into a running state posted here: [http://meeb.org/post/319933907/dont-upgrade-xen-domus-to-ubuntu-karmic-9-10-on-a](http://meeb.org/post/319933907/dont-upgrade-xen-domus-to-ubuntu-karmic-9-10-on-a)

From the fact that this bug [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430374](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430374) is closed, and the mention that this would be fixed in 10.4 in the meeb.org posting above, I had assumed that this would have gone away in 10.4, but it sounds like that **isn't** the case. :(

Does anyone know if it would be safe to upgrade my limping 9.10 server to 10.4/10.10, or will I still have the same problems? 

Also, my ISP is actually about to upgrade their hardware, and have asked if there are any issues that should be taking into consideration - is there anything I can tell them that would enable them to fix this for me on the Xen side?

thanks!
Alex

---

