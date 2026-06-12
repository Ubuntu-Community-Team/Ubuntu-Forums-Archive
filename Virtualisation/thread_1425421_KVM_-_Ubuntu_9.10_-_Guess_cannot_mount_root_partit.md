---
title: "KVM - Ubuntu 9.10 - Guess: cannot mount root partition"
date: 2010-03-09
forum: Virtualisation
---

### Post by romansoft on 2010-03-09
Hello,

I'm trying to create a vm/guest system in an Intel VT machine (kvm/virsh). I know there are some alternatives (vmbuilder, etc). I'm using virt-install.

My problem is when using LVM as virtual disk. I launch the install process with:

# virt-install -n ubuntu-plantilla -r 512 --vcpus=1 -w network:private7 -v -c /home/roman/ubuntu-9.10-server-i386.iso -f /dev/vg/vm --accelerate --vnc --noautoconsole --os-type=linux

where /dev/vg/vm is 6 GB LV inside my VG. Install process begins, I configure keyboard, partitioning... But the install process fails just after formatting the root partition, when trying to mount that root partition (the error msg says something like "it couldn't mount root partition" -not literal-).

If I repeat the very same process, but using a file instead of a LV, it works perfectly:

# virt-install -n ubuntu-plantilla -r 512 --vcpus=1 -w network:private7 -v -c /home/roman/ubuntu-9.10-server-i386.iso -f /home/roman/kk.img -s 6 --accelerate --vnc --noautoconsole --os-type=linux

Why? Did I miss some point when using LVM? I suppose that the error with "mounting root partition" is due to the root partition not being formatted correctly and/or being corrupted at some point. It seems -f parameter should work ok with LVM, it detects as a block device as well as the LV size:
[Mon, 08 Mar 2010 22:47:05 virt-install 3032] DEBUG (VirtualDisk:336) Setting size for existing storage to '6.0'
[Mon, 08 Mar 2010 22:47:05 virt-install 3032] DEBUG (VirtualDisk:370) Detected storage as type 'block'

Any idea what am I missing?

Cheers,
-r

---

### Post by kiranmurari on 2010-03-09
Hi,

I have tried to simulate your problem, but I was able to successfully install the VM on logical volume with "-f /dev/vg/vm".
   
So it looks like either the logical volume is already mounted or it might be having some blocks. Please check if the disk is clean.

The following link might be helpful to find and repair bad blocks.
[http://ubuntu-rescue-remix.org/node/50](http://ubuntu-rescue-remix.org/node/50)

---

### Post by romansoft on 2010-03-09
I also checked that LV wasn't mounted. It wasn't. Indeed, my steps were fist to create the LV and just after that, running virt-install. The host machine (hardware, I mean) is new, so the hard disk is not supposed to be damaged. And I didn't suffered from any other sympthon of hard disk errors.

I also googled a bit and found some users with similar behaviour (don't recall URLs, sorry), which solved the issue by leaving free space at the very beginning of the LV device (yes, strange).

That's why I'm suspecting it is KVM/LVM related... probably something I've missed :/

Cheers,
-r

---

