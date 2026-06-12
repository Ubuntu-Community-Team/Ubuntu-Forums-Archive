---
title: "Problem with pci passthrough since upgrade to kernel 3.19"
date: 2015-08-11
forum: Virtualisation
---

### Post by badger3 on 2015-08-11
I have a machine running Ubuntu 14.04.3 LTS which I use as a media server. The machine has a DVB-S tuner which I've been successfully passing through to a KVM VM using IOMMU.

I recently installed kernel 3.19 which I want to upgrade to as it better supports BTRFS raid 6, which I intend to use. 

Since upgrading to kernel 3.19 (it was on 3.13 before) I am unable to pass the tuner card through to the VM. If I boot any 3.13 kernel via grub, passthrough works and the VM can access the card. If I boot 3.19 it doesn't. This is repeatable behaviour with no other changes made. The kernel command line I'm using to boot the images is identical. 

Can anyone shed any light on why passthrough has stopped working for me under kernel 3.19? I've attached some potentially relevant info below. 

I installed the 3.19 kernel by apt-getting the following packages:
```

# dpkg -l | grep vivid
ii  linux-generic-lts-vivid                               3.19.0.25.12                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-generic-lts-vivid                       3.19.0.25.12                                        amd64        Generic Linux kernel headers
ii  linux-image-generic-lts-vivid                         3.19.0.25.12                                        amd64        Generic Linux kernel image

``` 

The error I get starting the VM under 3.19 is as follows:
```

# virsh start satellite
error: Failed to start domain satellite
error: internal error: process exited while connecting to monitor: qemu-system-x86_64: -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x7: vfio: error, group 1 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver.
qemu-system-x86_64: -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x7: vfio: failed to get group 1
qemu-system-x86_64: -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x7: Device initialization failed.
qemu-system-x86_64: -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x7: Device 'vfio-pci' could not be initialized

```


I checked the IOMMU groups as follows and it does indeed appear that I'm not passing the entire group through. The device I'm trying to pass through is "01:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 02)".

Here's the info on the groups and pci devices:

```

$ lspci
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C222 Series Chipset Family Server Essential SKU LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Chipset Family Thermal Management Controller (rev 05)
01:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 02)
02:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2308 PCI-Express Fusion-MPT SAS-2 (rev 05)
03:00.0 PCI bridge: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 03)
04:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 30)
05:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
06:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)


# lspci -n
00:00.0 0600: 8086:0c08 (rev 06)
00:01.0 0604: 8086:0c01 (rev 06)
00:01.1 0604: 8086:0c05 (rev 06)
00:14.0 0c03: 8086:8c31 (rev 05)
00:1a.0 0c03: 8086:8c2d (rev 05)
00:1c.0 0604: 8086:8c10 (rev d5)
00:1c.2 0604: 8086:8c14 (rev d5)
00:1c.3 0604: 8086:8c16 (rev d5)
00:1d.0 0c03: 8086:8c26 (rev 05)
00:1f.0 0601: 8086:8c52 (rev 05)
00:1f.2 0106: 8086:8c02 (rev 05)
00:1f.3 0c05: 8086:8c22 (rev 05)
00:1f.6 1180: 8086:8c24 (rev 05)
01:00.0 0480: 1131:7160 (rev 02)
02:00.0 0107: 1000:0086 (rev 05)
03:00.0 0604: 1a03:1150 (rev 03)
04:00.0 0300: 1a03:2000 (rev 30)
05:00.0 0200: 8086:1533 (rev 03)
06:00.0 0200: 8086:1533 (rev 03)


/sys/kernel/iommu_groups# find . -type l
./0/devices/0000:00:00.0
./1/devices/0000:00:01.0
./1/devices/0000:00:01.1
./1/devices/0000:01:00.0
./1/devices/0000:02:00.0
./2/devices/0000:00:14.0
./3/devices/0000:00:1a.0
./4/devices/0000:00:1c.0
./5/devices/0000:00:1c.2
./6/devices/0000:00:1c.3
./7/devices/0000:00:1d.0
./8/devices/0000:00:1f.0
./8/devices/0000:00:1f.2
./8/devices/0000:00:1f.3
./8/devices/0000:00:1f.6
./9/devices/0000:03:00.0
./9/devices/0000:04:00.0
./10/devices/0000:05:00.0
./11/devices/0000:06:00.0

```

From what I understand, this means the tuner card is in the same group as the Serial Attached SCSI controller and I need this to remain under the host's control. Under kernel 3.13 I had the SAS controller working from the host and the tuner card working from a VM so I know this can work! 

I've tried enabling unsafe interrupts via the kernel command line which didn't resolve the problem.

I tried re-binding pci-stub to the device and that didn't help either: 

```

# modprobe pci-stub
# lsmod | grep kvm
kvm_intel             151552  10 
kvm                   479232  1 kvm_intel
# lsmod | grep stub
pci_stub               16384  0 


# echo "1131 7160" > /sys/bus/pci/drivers/pci-stub/new_id 
# echo 0000:01:00.0 > /sys/bus/pci/devices/0000:01:00.0/driver/unbind
# echo 0000:01:00.0 > /sys/bus/pci/drivers/pci-stub/bind
# readlink  /sys/bus/pci/devices/0000\:01\:00.0/driver
../../../../bus/pci/drivers/pci-stub

```

---

### Post by redger on 2015-08-14
Yep,
looks like you're right. Interesting it previously worked ... maybe a quirk previously applied now gone ?

You'll need the ACS Override patch. Better still use a USB tuner, then you won't have these problems (maybe unhelpful :) )

fwiw I run Mythtv server in an unprivileged LXC container. It works really well, none of the overhead of a full hardware VM and for internal use security is pretty good. There were a few setup tricks but very worthwhile. I also run a full hardware VM with vga passthrough on an intel i5 server ... it all works really well. In  total I run 3 unprivileged LXC containers permanently (myth server, safe browsing, software development playground) plus 3 fully virtualised guests occasionally - one of which is Windows with VGA passthrough. All this runs on an unpatched Trusty 14.04 build

My point is, that you can increase the throughput and stability using a mix of virtualisation technologies. Perhaps you could consider running the media server in a VM, and you won't need to patch the kernel either :)
Note that you can also lock down container CPU, ram and storage using cgroups. My containers all locked down to cpus 1-3 ie. excluding 0

---

