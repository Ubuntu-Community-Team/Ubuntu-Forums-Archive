---
title: "Help with GPU passthrough setup"
date: 2016-08-21
forum: Virtualisation
---

### Post by wbrb on 2016-08-21
Preface - I've run GPU passthrough on VMware for a couple of years using a GTX480 softmodded into a Quadro 6000. But the nVidia driver crippling (-cpu kvm=off) really bothered me so I swore I would go AMD if they had something even halfway decent. I liked what I saw in the benches of the RX4xx so I grabbed a Radeon RX460 and have spent the last few days trying to pass it through to KVM. 

My hardware is:
```

Intel(R) Xeon(R) CPU E3-1230 v3 @ 3.30GHz
ASRock Z87 Extreme4
32GB
Radeon HD6350
Radeon RX460

```

It's disappointing the E3 Xeons don't support ACS. No IGD is fine. 

My /etc/default/grub
```
quiet splash intel_iommu=on iommu=pt iommu=1 pcie_acs_override=downstream
```

My /etc/modprobe.d/kvm-iommu.conf
```
options kvm vfio_iommu_type1
```

My /etc/modprobe.d/vfio.conf
```
vfio-pci ids=1002:67ef,1002:aae0 disable_vga=1
```
These match by RX460 and RX460 Sound. Apparently disable_vga=1 is only for OVMF .fd, I tried without this using seabios.bin as well

My /etc/modprobe.d/blacklist.conf
```
blacklist radeon
```

My /etc/initramfs-tools/modules
```
pci_stub ids=1002:67ef,1002:aae0,1002:68f9
```
These match my HD6350, RX460 and RX460 Sound

Then updates:
```
update-grub
update-initramfs -u

```

My IOMMU group 1 looks like this:
```
/sys/kernel/iommu_groups/1/devices/0000:00:01.0
/sys/kernel/iommu_groups/1/devices/0000:00:01.1
/sys/kernel/iommu_groups/1/devices/0000:01:00.0
/sys/kernel/iommu_groups/1/devices/0000:02:00.0
/sys/kernel/iommu_groups/1/devices/0000:02:00.1

```
I'm unclear what this should look like after the pcie_acs_override=downstream, I was understanding this should have split the groups of 01:00.0 (the HD6350) and the 02:00.0 and .1 (RX460) 

or according to virsh nodevdev-list --tree
```
computer
  |
  +- pci_0000_00_00_0
  +- pci_0000_00_01_0
  |   |
  |   +- pci_0000_01_00_0
  |
  +- pci_0000_00_01_1
  |   |
  |   +- pci_0000_02_00_0
  |   +- pci_0000_02_00_1
```

To start the VM I detach the devices from the host and bind the VFIO
```
virsh nodedev-dettach pci_0000_01_00_0
virsh nodedev-dettach pci_0000_02_00_0
virsh nodedev-dettach pci_0000_02_00_1

vfio-bind 0000:01:00.0
vfio-bind 0000:02:00.0
vfio-bind 0000:02:00.1

```

vfio bind is this (I take no credit, but can't remember who should get it):
```
#!/bin/bash

modprobe vfio-pci

for dev in "$@"; do
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device | tee /sys/bus/pci/drivers/vfio-pci/new_id
done

```

And finally I'm launching qemu-system-x86_64 with variations on:
```
qemu-system-x86_64 \
-enable-kvm \
-M q35 \
-m 4096 \
-cpu host \
-smp 4,sockets=1,cores=4,threads=1 \
-bios /usr/share/qemu/OVMF.fd \
-vga none \
-nographic \
-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \
-device vfio-pci,host=02:00.0,multifunction=on,rombar=0,id=rx460 \
-device vfio-pci,host=02:00.1,id=rx460snd \
-drive file=/var/lib/libvirt/images/u1604dt03.img,id=disk,format=raw,if=none,cache=writeback \
-drive file=/var/lib/libvirt/images/ubuntu-16.04-desktop-amd64.iso,id=isocd2 \
-usb -device usb-host,hostbus=3,hostaddr=2 -device usb-host,hostbus=3,hostaddr=3 \
-d guest_errors,mmu -D /var/log/qemu.log
```

qemu.log only shows:
```
CR0 update: CR0=0x60000010
```
a bunch of times

Any attempt to use an x-vga option fails with:
```
qemu-system-x86_64: -device vfio-pci,host=02:00.0,multifunction=on,rombar=0,id=rx460,x-vga=on: vfio: Device does not support requested feature x-vga
qemu-system-x86_64: -device vfio-pci,host=02:00.0,multifunction=on,rombar=0,id=rx460,x-vga=on: Device initialization failed

```

I thought x-vga was necessary. The results vary without it. I can get "console" splash that proceeds to blind mode. I have got it to display on the 2nd monitor a couple times before I had USB but I feel like I'm doing something wrong. Keyboard works, haven't got to anything that uses mouse yet but I assume it's ok.

I've been trying this on both an empty qcow2 disk and a raw disk with 1604 desktop x64 installed and the AMDGPU pro driver already installed. I've been avoiding virt-install or virt-manager until this is working, trying not to jump between methods. 

Does anyone have any suggestions or simplifications that might help? Anything conceptually wrong with this?

Thanks.

---

### Post by KillerKelvUK on 2016-08-21
Hey, so a couple of things don't look right...

[LIST=1]
[*]Use either vfio-pci or pci-stub not both.  pci-stub was an earlier driver used when there was nothing else to assign a PCI device to at boot to ensure the proper (nouveau, radeon) kernel module didn't grab it, the bash scripts (like yours) would then manually/automagically change the pci cards assigned driver to vfio prior to starting the guest.  However since kernel 4.1 the vfio-pci driver has become available to assign directly to at boot removing both the need for pci-stub as well as the bash script changing the assigned drivers.  If your kernel is compatible I'd recommend vfio-pci as it simplifies the process and is more stable.
[*]IOMMU separation.  I note you've added the grub line but you have multiple devices within a single group, if this group contains your GFX card and other non-passthrough devices then you will not be able to achieve passthrough.  You need to fix this first before moving onto guest creation and execution.  There was a recent thread here digging into Xeon and ACS patching, they got it working so have a read ([https://ubuntuforums.org/showthread.php?t=2329053](https://ubuntuforums.org/showthread.php?t=2329053))
[*]x-vga=on is only used if you want to passthrough the primary GFX card of your host, this is complicated and troublesome at best so I'd suggest you avoid this and focus on passing through the secondard GFX card on your host only...get comfortable with this and then progress to primary assignment.
[*]Last one from me today...guessing the guide(s) you've been following are pretty old, would recommend you follow [http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html](http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-1-hardware.html)
[/LIST]

---

### Post by wbrb on 2016-08-21
KillerKelvUK - Thank you for the suggestions and feedback.

1. I think I've fixed this and removed pci-stub use.

2. This one is fun. I'm not very familiar with Kernel patching. So my first attempt failed. For my second attempt I'm trying again using git to clone the source and this:
```
#!/bin/bash
sudo apt-get install build-essential git libssl-dev ncurses-dev xz-utils kernel-package kernel-wedge
sudo apt-get build-dep linux-image-$(uname -r)
git clone https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/xenial
#because 2GB D/L
rsync -r ./xenial ./xenial_backup
cd xenial
patch -p1 < /root/Ubuntu_Xenial_4.4.0_31_override_for_missing_acs_capabilities-kernel.patch
fakeroot debian/rules clean
chmod -R u+x debian/scripts/*
debian/rules updateconfigs
debian/rules build
faketroot debian/rules binary-headers binary-generic

```

It's cloning as I type this. I hope the 4.4.0_31 patch works with 4.4.0_34 without too much fiddling. Advice again welcome here.

This seems pretty old: [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"). Given that 16.04 is LTS I hope an update is on the todo list. 

3. Thank you for the clarification.

4. I read it already but I think it mixed in with everything else. I've reread and given it priority as you recommend it as newer. I missed the bit in part #3 that pretty clearly answers your first point.
 In addition this article [ this discussion ]("https://lkml.org/lkml/2013/6/18/738") actually cleared up some of the "why" in my head.

---

### Post by wbrb on 2016-08-22
So the ACS patch worked. For some reason I had no vfio-pci modules after the recompile and had to "apt-get -f install" to fix it. I would love to know why, I figured I was going to have to figure out how to rebuild them too. 

after another reboot:

dmesg | grep -i iommu
```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=6c7a3e89-7899-44fb-899e-3b98163ef138 ro quiet splash intel_iommu=on iommu=1 pcie_acs_override=downstream quiet splash intel_iommu=on iommu=1 pcie_acs_override=downstream vt.handoff=7
[    0.000000] Warning: PCIe ACS overrides enabled; This may allow non-IOMMU protected peer-to-peer DMA
[    0.000000] Warning: PCIe ACS overrides enabled; This may allow non-IOMMU protected peer-to-peer DMA
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=6c7a3e89-7899-44fb-899e-3b98163ef138 ro quiet splash intel_iommu=on iommu=1 pcie_acs_override=downstream quiet splash intel_iommu=on iommu=1 pcie_acs_override=downstream vt.handoff=7
[    0.000000] DMAR: IOMMU enabled
[    0.000000] DMAR: IOMMU enabled
[    0.034836] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.604895] iommu: Adding device 0000:00:00.0 to group 0
[    0.604905] iommu: Adding device 0000:00:01.0 to group 1
[    0.604912] iommu: Adding device 0000:00:01.1 to group 2
[    0.604918] iommu: Adding device 0000:00:14.0 to group 3
[    0.604926] iommu: Adding device 0000:00:16.0 to group 4
[    0.604931] iommu: Adding device 0000:00:19.0 to group 5
[    0.604937] iommu: Adding device 0000:00:1a.0 to group 6
[    0.604943] iommu: Adding device 0000:00:1b.0 to group 7
[    0.604949] iommu: Adding device 0000:00:1c.0 to group 8
[    0.604955] iommu: Adding device 0000:00:1c.2 to group 9
[    0.604961] iommu: Adding device 0000:00:1d.0 to group 10
[    0.604972] iommu: Adding device 0000:00:1f.0 to group 11
[    0.604977] iommu: Adding device 0000:00:1f.2 to group 11
[    0.604983] iommu: Adding device 0000:00:1f.3 to group 11
[    0.604989] iommu: Adding device 0000:01:00.0 to group 12
[    0.605018] iommu: Adding device 0000:02:00.0 to group 13 ***
[    0.605044] iommu: Adding device 0000:02:00.1 to group 13 ***
[    0.605050] iommu: Adding device 0000:04:00.0 to group 14

```

If I don't use pci-stub and I directly assign the ids to vfio-pci I suppose I don't need to bind the vfio driver to the devices anymore? /dev/vfio/13 already exists after a reboot now.

I followed  [ part 4 ]("http://vfio.blogspot.ca/2015/05/vfio-gpu-how-to-series-part-4-our-first.html") to create the virtual machine using virt-manager (only I was doing steam on ubuntu 16.04 desktop) and to my surprise it passed through! I still have to unplug and hotplug my USB devices before passing them to the guest, I passed my motherboard sound adapter just for testing, my disk I/O is only like 300k on /dev/vda (virtio/qcow2) BUT IT WORKS! I installed Steam/Halflife1 (cause it was only 500MB and 3D and it runs in 1080 at a silly FPS with sound). I can play with xpad/modern games/disk throughput/etc once I have a host build documented. 

I'll work on command line startups now that I have the virsh nodedev-dumpxml for reference. Is the a way to mark something solved or do I just change the title?

---

### Post by KillerKelvUK on 2016-08-22
> **wbrb said:**
> If I don't use pci-stub and I directly assign the ids to vfio-pci I suppose I don't need to bind the vfio driver to the devices anymore? /dev/vfio/13 already exists after a reboot now.

Correct, by allocating the ids to the vfio-pci driver under /etc/[COLOR=#000000]modprobe.d/vfio.conf the driver loaded at boot then binds to these devices, you can validate this with lspci -v and checking the kernel driver in use.[/COLOR]

Glad you've gotten this to work.

---

