---
title: "Ubuntu Server 12.04 + Xen - Trouble with creating PV Guests"
date: 2012-07-15
forum: Virtualisation
---

### Post by m0gg3 on 2012-07-15
Hello!

I'm going nuts on this stuff. Been testing whole weekend without getting it to work.

I can't create DomU's using PV and LVM setup. My testcomputer is old and doesn't support HVM, but I don't want to use that anyway.

My setup is as follows:

Install a clean Ubuntu Server 12.04

Partitioning using LVM:
/boot = ext2 @ 300MB
/ = ext4 @ 6GB
swap = swap @ 1GB

After installation, doing a dist upgrade > reboot.

Then I install Xen using this guide: [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

but I change amd64 to i386 as of my old CPU.

I then want to install ubuntu server as ParaVirtualized guest.
As kernel and ramdisk I've been using this mirror:
[http://ftp.ds.karen.hj.se/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/](http://ftp.ds.karen.hj.se/ubuntu/dists/precise/main/installer-i386/current/images/netboot/xen/)

But also tried others.

I create a LV as told.

My /etc/xen/ubuntu.cfg:
```

name = "Merkurius"

memory = 256

disk = ['phy:/dev/Uranus/Merkurius,xvda,w']
vif = [' ']

#bootloader = "pygrub"

kernel = "/var/lib/xen/images/ubuntu-netboot/vmlinuz"
ramdisk = "/var/lib/xen/images/ubuntu-netboot/initrd.gz"
extra = "debian-installer/exit/always_halt=true -- console=hvc0"

```

I can install Ubuntu Server without issues. When complete I create a symlink to pygrub and change ubuntu.cfg as the guide says (# before kernel, ramdisk & extra and remove the # from bootloader)

Then when I try to start it with
```
sudo xm create /etc/xen/ubuntu.cfg -c
```
it says:
```

Using config file "/etc/xen/ubuntu.cfg".
Error: (2, 'Invalid kernel', 'elf_xen_note_check: ERROR: Will only load images built for the generic loader or Linux images')

```

I've been reinstalling everything tons of times testing.
Searched around and a lot of people seems to have this problem, but I don't really find a solution? Most say it needs to be a kernel with xen support, but shouldn't ubuntu have this? And I use a mirror that is up-to-date.

Testing different partitioning setups as well. Tested with XL toolstack. Same thing all the time.


Thanks for your time,
Mogge

---

### Post by m0gg3 on 2012-07-16
Update:

I got my new computer parts today and built a new server which had 64bit CPU. I installed ubuntu server x64 and xen x64, and now it working perfect!

I don't know if x86 of ubuntu/xen is bugged, or if you have to anything else outside the guide I've followed. Anyway it works!

---

### Post by rodrigorrm on 2012-12-28
Hi guys, I have the very same situation but cannot afford changing over to a 64 bit machine. Can someone point me to a solution using 32 bit kernel?

---

