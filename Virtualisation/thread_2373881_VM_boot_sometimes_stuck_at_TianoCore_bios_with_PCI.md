---
title: "VM boot sometimes stuck at TianoCore bios with PCI passthrough"
date: 2017-10-10
forum: Virtualisation
---

### Post by mogliii on 2017-10-10
Hi,

I have a problem with my virtual machine running on a 16.04 host. Hardware is ASRock Z97 Extreme 6. For the VM, I have a pcie USB 3 card from Buffalo
```
02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)

```

Sometimes, my VM gets stuck on the Tiano Core Bios logo at 50% CPU, and does not proceed even after several hours. Sometimes the VM boots up nicely. I have assigned the graphics card to pci-stub, but not the USB card.

After looking at the problem in more detail, I noticed that when the VM does not work, after GRUB there is a 15 seconds wait before the Ubuntu logo shows up. In case the VM works, boot is immediate. I then recorded the dmesg output for both cases and found the following for the non working state: (0000:0c:00.0 is the on-board USB)

```
[    2.087926] usb 3-9.3: new full-speed USB device number 5 using xhci_hcd
[    2.192449] usb 3-9.3: New USB device found, idVendor=0557, idProduct=8021
[    2.192451] usb 3-9.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.192525] usb 3-9.3: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    2.192858] hub 3-9.3:1.0: USB hub found
[    2.192998] hub 3-9.3:1.0: 4 ports detected
[    2.463960] usb 3-9.3.1: new full-speed USB device number 6 using xhci_hcd
[    2.573275] usb 3-9.3.1: New USB device found, idVendor=04b4, idProduct=120d
[    2.573277] usb 3-9.3.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.573278] usb 3-9.3.1: Product: Convertible 2 TKL
[    2.573355] usb 3-9.3.1: ep 0x83 - rounding interval to 32 microframes, ep desc says 40 microframes
[   18.195435] xhci_hcd 0000:02:00.0: can't setup: -110
[   18.195446] clocksource: Switched to clocksource tsc
[   18.195447] xhci_hcd 0000:02:00.0: USB bus 5 deregistered
[   18.195487] xhci_hcd 0000:02:00.0: init 0000:02:00.0 fail, -110
[   18.195491] xhci_hcd: probe of 0000:02:00.0 failed with error -110
[   18.195532] xhci_hcd 0000:0c:00.0: xHCI Host Controller
[   18.195535] xhci_hcd 0000:0c:00.0: new USB bus registered, assigned bus number 5
```

In case the VM works, the order of the dmesg is different, but except for the "fail, -110", all messages are present:

```
[    2.110125] usb 5-3.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.110127] usb 5-3.1: Product: Convertible 2 TKL
[    2.110250] usb 5-3.1: ep 0x83 - rounding interval to 32 microframes, ep desc says 40 microframes
[    2.128259] input: Convertible 2 TKL as /devices/pci0000:00/0000:00:01.1/0000:02:00.0/usb5/5-3/5-3.1/5-3.1:1.0/0003:04B4:120D.0004/input/input10
[    2.182754] hid-generic 0003:04B4:120D.0004: input,hidraw3: USB HID v1.11 Keyboard [Convertible 2 TKL] on usb-0000:02:00.0-3.1/input0
[    2.203120] usb 3-9.3: New USB device found, idVendor=0557, idProduct=8021
[    2.203122] usb 3-9.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.203203] input: Convertible 2 TKL as /devices/pci0000:00/0000:00:01.1/0000:02:00.0/usb5/5-3/5-3.1/5-3.1:1.1/0003:04B4:120D.0005/input/input11
[    2.203218] usb 3-9.3: ep 0x81 - rounding interval to 1024 microframes, ep desc says 2040 microframes
[    2.203583] hub 3-9.3:1.0: USB hub found
[    2.203740] hub 3-9.3:1.0: 4 ports detected
[    2.258683] hid-generic 0003:04B4:120D.0005: input,hidraw4: USB HID v1.11 Device [Convertible 2 TKL] on usb-0000:02:00.0-3.1/input1
[    2.270212] input: Convertible 2 TKL as /devices/pci0000:00/0000:00:01.1/0000:02:00.0/usb5/5-3/5-3.1/5-3.1:1.2/0003:04B4:120D.0006/input/input12
[    2.270489] hid-generic 0003:04B4:120D.0006: input,hidraw5: USB HID v1.10 Mouse [Convertible 2 TKL] on usb-0000:02:00.0-3.1/input2
[    2.370573] ata10: SATA link down (SStatus 0 SControl 300)
[    2.407614] pci-stub: add 10DE:0FBC sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.407624] pci-stub 0000:01:00.1: claimed by stub
[    2.407628] pci-stub: add 10DE:1380 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.407632] pci-stub 0000:01:00.0: claimed by stub
[    2.409899] md: linear personality registered for level -1
[    2.411605] md: multipath personality registered for level -4
[    2.413112] md: raid0 personality registered for level 0
[    2.414899] md: raid1 personality registered for level 1
[    2.482532] raid6: sse2x1   gen() 10825 MB/s
[    2.550514] raid6: sse2x1   xor()  8416 MB/s
[    2.618527] raid6: sse2x2   gen() 13772 MB/s
[    2.686508] raid6: sse2x2   xor()  9265 MB/s
[    2.754506] raid6: sse2x4   gen() 15936 MB/s
[    2.822510] raid6: sse2x4   xor() 10916 MB/s
[    2.890507] raid6: avx2x1   gen() 19997 MB/s
[    2.958507] raid6: avx2x2   gen() 23484 MB/s
[    3.026505] raid6: avx2x4   gen() 26990 MB/s
[    3.026505] raid6: using algorithm avx2x4 gen() 26990 MB/s
[    3.026506] raid6: using avx2x2 recovery algorithm
[    3.026513] clocksource: Switched to clocksource tsc
[    3.027547] scsi 10:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0272 PQ: 0 ANSI: 0
[    3.027635] xor: automatically using best checksumming function:
[    3.028042] sd 10:0:0:0: Attached scsi generic sg1 type 0
[    3.029342] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[    3.066516]    avx       : 32708.000 MB/sec
[    3.067368] async_tx: api initialized (async)
```

I doubt, however, that it is due to the USB card. This particular motherboard, with a different but identical VGA adapter and a different but identical USB card did also have hickups to start the VM. Another motherboard (also asrock but different model) worked with both sets of peripherals and cards. Anything I can do in software?

---

### Post by KillerKelvUK on 2017-10-10
Hey, I've the same motherboard but am running 17.04 on the host.  What is your grub configuration?  Using "iommu=pt" stabilised/removed a lot of PCI issues for me (ignore the ipv6 as you like, that's just me being overly security conscious)...

```

[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on iommu=pt intremap=no_x2apic_optout ipv6.disable=1"[/COLOR]
[/FONT]
```

---

### Post by mogliii on 2017-10-17
Hi,

I have 
```
intel_iommu=on iommu=pt pci-stub.ids=10de:0fbc,10de:1380 hugepages=2048i pcie_acs_override=downstream
``` in my grub and I am using the ACS override patch (because I have a NVME SSD.

I'm not sure why I have i attached to hugepages, but it seems to work.

Any other idea?

---

### Post by KillerKelvUK on 2017-10-17
Have you considered moving away from pci-stub to assigning the devices to the vfio-pci driver at host boot time?  Its a cleaner solution to pci-stub as it removes the step of the host changing the PCI module from pci-stub to vfio-pci prior to starting the guest.  I understood this module change was troublesome for some hardware hence directly assigning to vfio-pci is the newer *standard*.

---

### Post by mogliii on 2017-10-19
Hi,

I did not know its possible without pci-stub. I setup the configuration more than a year ago and it was a pain, so never touch a working system ^^

Today, I removed the USB3 PCIe card and switched to the onboard 0b:00.0 USB controller and passing it to the VM. The VM starts now everytime directly. For now I will keep it like this. For some reason my mb does not go well with that particular usb card... another ASRock (Z87) works fine with that particular card/model.

---

### Post by mogliii on 2017-10-19
Sorry for this follow up question: But how would I assign the USB3 PCIe card to vfio-pci? Or is this only for VGA adapters?
Maybe then I can still use the card and it won't get stuck? I don't need those usb ports when the VM is off.

---

### Post by KillerKelvUK on 2017-10-20
Same as any other PCI device however USB controllers in my experience always get caught by their respective/proper kernel device module and so never show as using vfio-pci/pci-stub, they do however reassign i.e. vfio-pci takes over once the guest is started.

I also had no end of problems with USB3 cards and passthrough, RMA one as it just locked up the host on guest start.  Inatek was the problem child, their support advised they recommended against split OS usage i.e. the card didn't like switching from a linux OS to a Windows OS.  I settled on using an AUKEY one, although I had issues with that until I crafted around the problems with the grub line I shared previous.

---

### Post by mogliii on 2017-10-24
Now working with the USB3 card.

What had happened: I was looking through all usb ports, both on the back panel and on the board. But except for the two ports next to the lower ethernet jack, ALL! ports are connected to the same USB controller (ASMedia). So I had a choice of either passing 2 ports to the VM, or keeping two for the host. Both not satisfactory. Also, using a USB hub for the guest was not an option because my KVM did not work with it.

So I desperation I tried the USB3 PCIe card in a different PCIe port (the top most one, above the VGA adapter). And strangely enough the hosts and guests boot well without the previous hickups ?!? While happy, It leaves me unhappy as I don't know the exact reason. I had previously tried the USB card in the lower PCIex1 and one of the other PCIex16 slots.

---

