---
title: "Questions and issues with passthrough on 14.04"
date: 2014-09-28
forum: Virtualisation
---

### Post by froyomuffin on 2014-09-28
Hello,

I'm currently trying to get vfio working kvm on 14.04 and I'm having some issues. My questions come in two parts. Before anything, I don't have much experience working with drivers/modules in linux so I would appreciate it if someone could validate/correct my understanding thus of the system so far. Then, I'll list what I've done to troubleshoot and the symptoms of the problem I'm having. If it doesn't solve my issue, hopefully it'll help someone else.

First, here's what I gather so far. There several ways of doing passthrough in QEMU. The most recent and efficient is via VFIO which uses IOMMU (VT-D for Intel). An older method is via pci-assign. Now, hardware can only be used by one driver/module at a time and, as such, we must prevent anything from taking the GPU/PCI so that it may be bound by vfio-pci. The version or nature of the driver (nouveau vs nvidia for instance) doesn't matter as we will let the guest handle it. The only thing that matters is that the driver does not bind our device of interest. So, the general procedure to setting up VFIO passthrough would be:
[INDENT]1. IOMMU needs to be enabled
2. The appropriate modules must be loaded on boot
3. Drivers/modules for the GPU must not bind the hardware.
This is done in one of two ways. Either you blacklist the module (assuming it wasn't compiled with the kernel) or you prematurely bind the hardware to pci-stub. The latter appears to be a better solution as modules/drivers are shared if you have multiple GPUs from the same manufacturer so you can't really blacklist a driver that may be used by the host (i.e, you're using two GPUs from the same manufacturer and one of them is used for passthrough and the other for the host).
4. Bind vfio-pci to the devices you wish to passthrough
5. Load the appropriate device in qemu by selecting vfio-pci as device and giving it the pci #.

[/INDENT]

Now, here's what I've done:
Relevant specs:[INDENT]Intel 4430[/INDENT]
[INDENT]AsRock B85M-ITX[/INDENT]
[INDENT]evga GTX750 Ti[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Kernel 3.16[/INDENT]
[INDENT]QEMU 2.0 or latest from git[/INDENT]
[INDENT]SeaBios 1.7.4 or 1.7.5

[/INDENT]
And the steps:[INDENT]Bios:[/INDENT]
[INDENT]Set Vt-d to enable[/INDENT]
[INDENT]Set Primary GPU to onboard[/INDENT]
[INDENT]
[/INDENT]
[INDENT]1. Enabled IOMMU via /etc/default/grub:[/INDENT]
```
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"[/INDENT]

```[INDENT]then [/INDENT]
```
[INDENT]sudo update-grub[/INDENT]

```[INDENT]2. Added relevant modules to /etc/modules[/INDENT]
```
[INDENT]pci_stub[/INDENT]
[INDENT]vfio[/INDENT]
[INDENT]vfio_iommu_type1[/INDENT]
[INDENT]vfio_pci[/INDENT]
[INDENT]kvm[/INDENT]
[INDENT]kvm_intel[/INDENT]

```[INDENT]3. Blacklisted the native drivers via /etc/modprobe.d/blacklist.conf[/INDENT]
```
[INDENT]blacklist nouveau[/INDENT]
[INDENT]blacklist nvidia[/INDENT]

```[INDENT]Bind the devices to pci_stub on boot (just in case) in /etc/initramfs-tools/modules[/INDENT]
```
[INDENT]pci-stub ids=10de:1380,10de:0fbc[/INDENT]

```[INDENT]then[/INDENT]
```
[INDENT]sudo update-initramfs -u[/INDENT]

```[INDENT]4. Bound vfio to the devices via:[/INDENT]
```
[INDENT]#!/bin/bash[/INDENT]
[INDENT]DEVLIST="0000:01:00.0 0000:01:00.1"[/INDENT]
[INDENT]for dev in $DEVLIST[/INDENT]
[INDENT]do[/INDENT]
[INDENT]        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)[/INDENT]
[INDENT]        device=$(cat /sys/bus/pci/devices/$dev/device)[/INDENT]
[INDENT]        if [ -e /sys/bus/pci/devices/$dev/driver ][/INDENT]
[INDENT]        then[/INDENT]
[INDENT]                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind[/INDENT]
[INDENT]        fi[/INDENT]
[INDENT]        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id[/INDENT]
[INDENT]done[/INDENT]
[INDENT]
[/INDENT]
[INDENT]modprobe vfio-pci[/INDENT]

```[INDENT]5. Starting QEMU[/INDENT]
```
[INDENT]#!/bin/bash[/INDENT]
[INDENT]sudo qemu-system-x86_64 -enable-kvm -M q35 -m 2048 -cpu host \[/INDENT]
[INDENT]-smp 4,sockets=1,cores=4,threads=1 \[/INDENT]
[INDENT]-bios /usr/share/qemu/bios.bin -vga cirrus \[/INDENT]
[INDENT]-device ioh3420,bus=pcie.0,addr=1c.0,multifunction=on,port=1,chassis=1,id=root.1 \[/INDENT]
[INDENT]-device vfio-pci,host=01:00.0,bus=root.1,addr=00.0,multifunction=on,x-vga=on \[/INDENT]
[INDENT]-device vfio-pci,host=01:00.1,bus=root.1,addr=00.1 \[/INDENT]
[INDENT]-drive file=./W764.qcow2,id=disk,format=qcow2 -device ide-hd,bus=ide.0,drive=disk \[/INDENT]
[INDENT]-drive file=./W764.iso,id=isocd -device ide-cd,bus=ide.1,drive=isocd \[/INDENT]
[INDENT]-boot menu=on[/INDENT]

```

After rebooting, I see that the audio and video devices for my GPU are bound by pci_stub. After the bind script, both devices are bound by vfio-pci. This is checked via lspci.
If I leave -vga cirrus on, I get a code 12 after installing drivers in Windows. If I set -vga to none, I get no video output from the GPU. Now, I'm wondering now if it's a limitation of the mobo or the gpu.


Any ideas anyone?


Thanks :D

---

### Post by froyomuffin on 2014-12-14
Mm anyone?

---

### Post by TheFu on 2014-12-14
Doing passthru for video cards is harder than doing it for most other PCI cards like HBAs or NICs.
If u r trying to do video card passthru, there is another thread here with specific video cards that are known to work for Windows guest VMs.

Sorry that I'm not any help - most  of my VM servers don't have a video card connected.

---

### Post by froyomuffin on 2015-01-20
Thanks for the reply :)

---

### Post by pepsifx357 on 2015-01-23
I've got a 560 Ti that I'm trying to pass right now.  I'm stuck at a Code 43 error.

It probably won't help but here's my post with my startup script:

[http://ubuntuforums.org/showthread.php?t=2262188]("http://ubuntuforums.org/showthread.php?t=2262188")

---

### Post by froyomuffin on 2015-02-13
[FONT=arial][COLOR=#3F4549]Sorry for late reply. I got it working in the end. I switched to Arch since but the solutions should be applicable to Ubuntu. All problems were solved after reading the following guide many many times:[/COLOR]
[COLOR=#3F4549]https://bbs.archlinux.org/viewtopic.php?id=162768[/COLOR]

[COLOR=#3F4549]What I ran into and the solutions:[/COLOR]
[COLOR=#3F4549]1. Black screen/no output/code 12:[/COLOR]
[COLOR=#3F4549]May happen due to kernel being too old, missing the ACS override patch or missing the i915 VGA arbiter fixes. It's also important to be doing primary passthrough (i.e. no video except directly from the graphics card). In the latest kernels (at least on 3.18+), I did not need the ACS override patch and did not need to use the arbiter fixes as I used OVMF. I would recommend using OVMF to anyone as the ACS override patch breaks DRI and cripples the graphics on the host (software rendering). [/COLOR]

[COLOR=#3F4549]2. Code 43:[/COLOR]
[COLOR=#3F4549]Bonus issue here after I got the passthrough working. This is likely caused by a "bug" nVidia introduced. If the drivers detect that the OS is virtualized, they fubar. It's known and nVidia won't fix it. Interestingly, this "bug" is not present on their quadro line cards that have passthrough supported officially. To work around that, you need to hide the virtualization from the OS (which, I understand prevents it from some optimizations :C). You do this with -cpu [type],[/COLOR]**kvm=off**. Good document here: [http://www.linux-kvm.org/wiki/images/b/b3/01x09b-VFIOandYou-small.pdf](http://www.linux-kvm.org/wiki/images/b/b3/01x09b-VFIOandYou-small.pdf) [/FONT]

---

