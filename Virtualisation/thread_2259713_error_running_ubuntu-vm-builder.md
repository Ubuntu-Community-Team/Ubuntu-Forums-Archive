---
title: "error running ubuntu-vm-builder"
date: 2015-01-06
forum: Virtualisation
---

### Post by rumpumpel1 on 2015-01-06
Hi,

I' trying to build my first vm as described in [HTML]https://help.ubuntu.com/community/KVM/CreateGuests[/HTML].
The following command:

 ```
ubuntu-vm-builder kvm trusty \
                  --domain ovpnvm \
                  --dest ovpnvm \
                  --arch amd64 \
                  --hostname vpn \
                  --mem 1024 \
                  --user vmuser \
                  --pass vmuser \
                  --ip 192.168.0.50 \
                  --mask 255.255.255.0 \
                  --net 192.168.0.0 \
                  --bcast 192.168.0.255 \
                  --gw 192.168.0.1 \
                  --dns 192.168.0.1 \
                  --components main,universe,restricted \
                  --addpkg acpid \
                  --addpkg vim \
                  --addpkg openssh-server \
                  --libvirt qemu:///system

```

ends with an error message:

```
Selecting previously unselected package linux-image-3.13.0-43-generic.
(Reading database ... 17748 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb ...
Selecting previously unselected package linux-image-virtual.
Preparing to unpack .../linux-image-virtual_3.13.0.43.50_amd64.deb ...
Unpacking linux-image-virtual (3.13.0.43.50) ...
, stderr: grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-43-generic_3.13.0-43.72_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any help appreciated.

---

### Post by TheFu on 2015-01-06
That article looks really old - 2008.  Be certain to read the manpages for any commands to see what may have changed.

So - for someone new to KVM, it is much easier to use libvirt and virt-manager to create virtual machines than the CLI tools. Only the ssh port to the KVM server needs to be available for this to work.  I find hat manually created bridges work better than the automatically created NAT thing too. Here's a [presentation ]("http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html")I've given a few places about KVM setup. Hope it helps.

After you get the first VMs working this way, you can come back and screw around with scripted VM creation. I don't do scripted VMs - just don't need that many new VMs created in a year to make it useful to me.

---

