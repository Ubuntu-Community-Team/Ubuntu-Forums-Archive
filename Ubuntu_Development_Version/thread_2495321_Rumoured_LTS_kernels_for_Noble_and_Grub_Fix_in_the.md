---
title: "Rumoured LTS kernel/s for Noble and Grub Fix in the Pipeline"
date: 2024-02-14
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2024-02-14
Things are looking good on "ubuntu-uefi-team/noble for grub so far:
**NOTE: for testing purpose's only** Showing only for progression.
```
apt policy grub-common grub-efi-amd64-signed
grub-common:
  Installed: 2.12-1ubuntu2
  Candidate: 2.12-1ubuntu2
  Version table:
 *** 2.12-1ubuntu2 500
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     2.12-1ubuntu1 100
        100 http://us.archive.ubuntu.com/ubuntu noble-proposed/main amd64 Packages
     2.12~rc1-12ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
grub-efi-amd64-signed:
  Installed: 1.201+2.12-1ubuntu1
  Candidate: 1.201+2.12-1ubuntu1
  Version table:
 *** 1.201+2.12-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     1.201+2.12-1ubuntu1 500
        500 https://ppa.launchpadcontent.net/ubuntu-uefi-team/build/ubuntu noble/main amd64 Packages

```
**initramfs- now shows:
```
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-9-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Some pools couldn't be imported and will be ignored:
cannot import 'rpool': pool already exists
cannot import 'bpool': pool already exists
[COLOR="#FF0000"]Found linux image: vmlinuz-6.8.0-7-lowlatency in rpool/ROOT/ubuntu_2wtpxc
Found initrd image: initrd.img-6.8.0-7-lowlatency in rpool/ROOT/ubuntu_2wtpxc[/COLOR]
Found linux image: vmlinuz-6.6.0-14-generic in rpool/ROOT/ubuntu_2wtpxc
Found initrd image: initrd.img-6.6.0-14-generic in rpool/ROOT/ubuntu_2wtpxc
[COLOR="#FF0000"]Found linux image: vmlinuz-6.8.0-7-lowlatency in rpool/ROOT/ubuntu_2wtpxc@friday
Found initrd image: initrd.img-6.8.0-7-lowlatency in rpool/ROOT/ubuntu_2wtpxc@friday[/COLOR]
Found linux image: vmlinuz-6.6.0-14-generic in rpool/ROOT/ubuntu_2wtpxc@friday
Found initrd image: initrd.img-6.6.0-14-generic in rpool/ROOT/ubuntu_2wtpxc@friday
Found memtest86+ 64bit EFI image: /BOOT/ubuntu_2wtpxc@/memtest86+x64.efi
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done

```

Before this it would import 'bpool': pool  even though it already exists..(Mostly for or on zfs)

The Low-Lat kernel is only 4 hrs old on this install, but so far so good on my ZFS-Root. Working as expected.

---

