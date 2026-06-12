---
title: "IOMMU enabled, no IOMMU groups"
date: 2018-06-24
forum: Virtualisation
---

### Post by lodbro on 2018-06-24
I think my IOMMU or VT-x & VT-d might not be working correctly
Here we go...
I tried to include **all** relevant information on getting a pci passthrough to work so everything is clear
I've been following along with [this]("https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/") guide and [this]("https://www.youtube.com/watch?v=w-hOr44oBAI") video (the video is sort of a walk-through of the Puget guide) to get pci passthrough working with Qemu KVM.

 I enabled IOMMU and when I run:
```
dmesg | grep -i iommu
``` 
I get:
```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic root=UUID=105aec29-984f-465d-9bdb-79899af628d4 ro quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 vt.handoff=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic root=UUID=105aec29-984f-465d-9bdb-79899af628d4 ro quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1 vt.handoff=1
[    0.000000] DMAR: IOMMU enabled
```
So that means that IOMMU is enabled, right? wrong.
I used a command recommended to [someone else with a similiar problem]("https://ubuntuforums.org/showthread.php?t=2348650")
```
dmesg | grep Virtual
```
and I get no terminal output, just a new line
This makes me believe that IOMMU is not actually enabled, I have gone into my bios and enabled the "Intel Virtualization Technology" and it doesn't seem to work

System Specs:
```
i5 3470
8gb ddr3 - another 8gb stick in the mail
Intel DH61CR mobo
GTX 950
```
 
My Grub config file (I grub-update after every change):
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

My /etc/vfio-pci1.cfg file:
```
0000:01:00.0
0000:01:00.1
```
My /etc/modules file:
```

pci_stub
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel 
```

The current relevant output of a lspci -nnk command:
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 950] [10de:1402] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM206 [GeForce GTX 950] [1043:8586]
    Kernel driver in use: pci-stub
    Kernel modules: nvidiafb, nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8586]
    Kernel driver in use: pci-stub
    Kernel modules: snd_hda_intel
02:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
```

If you need me to provide any more information or config files, just ask!
Please help! been pulling my hair out for days over this!

---

### Post by KillerKelvUK on 2018-06-24
You sure that board supports vt-d?  And that its turned on in the UEFI?

---

### Post by lodbro on 2018-06-24
The only option in the bios relating to virtualization it an option under Security labeled 'Intel Virtualization Technology"
The processor supports VT-d and VT-x, so why would the motherboard have such a broad term and not support both?
Here is the Intel ARK page for the mainboard:
[Intel Desktop Board DH61CR]("https://ark.intel.com/products/51857/Intel-Desktop-Board-DH61CR")
I don't even see any options that mention VT-d or VT-x, but it's there in the bios menu.

I'm going to try to and set up a testbench with another of the same CPU and use my GPU on a Lenovo Thinkcentre motherboard and see if I have any luck there.

See if you have any ideas on whether or not this board supports virtualization for real or if it's just a useless part of the bios left over from another board (I believe they reuse this same bios on multiple boards)
Thanks!

---

### Post by KillerKelvUK on 2018-06-24
So your mobo doesn't support vt-d from my read.

[https://www.intel.co.uk/content/www/uk/en/support/articles/000005758/boards-and-kits/desktop-boards.html](https://www.intel.co.uk/content/www/uk/en/support/articles/000005758/boards-and-kits/desktop-boards.html)

---

### Post by lodbro on 2018-06-24
I could never find that, so thank you. I tried to switch my CPU over to this Thinkcentre board but I got no output, it's okay though. I'm going to switch over to a much better suited 8-core a10-5800k with 32 gb of ram if I can manage. This should be much better for virtualization, and it is an APU, providing much better graphical performance to the host

---

