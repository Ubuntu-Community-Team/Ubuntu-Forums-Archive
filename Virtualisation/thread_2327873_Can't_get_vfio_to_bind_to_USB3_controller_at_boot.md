---
title: "Can't get vfio to bind to USB3 controller at boot"
date: 2016-06-15
forum: Virtualisation
---

### Post by John_Throw on 2016-06-15
I'm running Ubuntu 16.04. I have PCI passthrough of a radeon r7 360 to a windows 7 VM working. I've played a game on it, run heaven benchmark, restarted and started a number of times. That all seems fairly solid so far. At boot up lspci -v shows that the radeon card and its associated hdmi audio device both have the vfio-pci as their kernel driver in use. But I can't get a USB3 card in that state no matter what I do! It always lists xhci_hcd.

I added in /etc/modules
vfio
vfio_iommu_type1
vfio_pci
kvm
kvm_intel 

In blacklist.conf I added radeon to the end.

**In /etc/initramfs-tools/modules**
I have 
vfio_pci ids=10de:13c2,10de:0fbb (not actual ids I use but I've triple checked the usb card as the first one)

I remember to run sudo update-initramfs -u after changes to these files and reboot

As an alternative method, I also tried creating files
/etc/modprobe.d/xhci_hcd.conf
With contents
softdep xhci_hcd pre: vfio-pci

This worked at least with radeon removed from blacklist and a similar file for radeon but nothing changed with the USB card.

Some weird things I noticed were that the radeon sound driver bound to vfio-pci even though its driver isn't blacklisted. I believe I needed the blacklist or the softdep to get the video device itself working.

It seems like softdep should work and I don't seem to be doing anything wrong that I can see, but it just doesn't.

I haven't tried blacklisting the xhci_hcd driver since I'd like to keep a separate usb 3.0 card available to the host. I may try that as a test.

I'm also being stubborn here. The USB3.0 card can be added in virt manager and the binding is all taken care of. But I don't really want devices that are attached to my windows guest ever really being used by the host.
I still could probably bind to vfio manually after I guess (haven't tried) but I still think what I'm trying to do should work.

---

### Post by MAFoElffen on 2016-06-15
Here is what I know from your post:

You are running 16.04 on the host. I can assume that you are running qemu or kvm locally.

I do not know if you found the pci address of your usb devices via lspci or via lsusb...

Could you please post the result of lsusb?

---

### Post by KillerKelvUK on 2016-06-16
> **John_Throw said:**
> I'm also being stubborn here. The USB3.0 card can be added in virt manager and the binding is all taken care of. But I don't really want devices that are attached to my windows guest ever really being used by the host.
I still could probably bind to vfio manually after I guess (haven't tried) but I still think what I'm trying to do should work.

FWIW I passthrough my USB3 controller successfully to a guest and use libvirt via virt-manager, the device itself is assigned at boot to the vfio-pci driver as you do also...however every time I stop the guest the controller is re-attached to the host and the devices are use-able.  I didn't think much of this as I don't care about the usb devices as I just *dont use them *on the host.   My suspicion is this is normal behaviour...

---

### Post by John_Throw on 2016-06-21
I apologize I keep forgetting to send the lspci settings. Although I've checked and rechecked those values a number of times.

Yes, I believe things are working "as designed" essentially. I want them to work a bit differently!

I believe the issue is xhci_hcd is a kernel driver and its always loaded before vfio-pci. radeon and snd_hda_intel (not sure that's entirely correct) can be blacklisted or set to softdep for radeon, or simply seem to load later than vfio-pci respectively.

---

### Post by firepol2 on 2016-09-05
Hi John_Throw, did you get it working in the end? I have also a USB controller and added  the id in the pci-stub.conf file together with my GPU ids (vga+audio). When I run dmesg | grep stub I get:

```
[    0.863383] pci-stub: add 10DE:0FBC sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.863390] pci-stub 0000:01:00.1: claimed by stub
[    0.863394] pci-stub: add 10DE:1380 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.863397] pci-stub 0000:01:00.0: claimed by stub
[    0.863399] pci-stub: add 1106:3483 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
```

The last one (1106:3483) is my USB controller. It's added but not claimed and I don't get why... any help appreciated, thx.

---

### Post by John_Throw on 2016-12-03
> **firepol2 said:**
> Hi John_Throw, did you get it working in the end? I have also a USB controller and added  the id in the pci-stub.conf file together with my GPU ids (vga+audio). When I run dmesg | grep stub I get:

```
[    0.863383] pci-stub: add 10DE:0FBC sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.863390] pci-stub 0000:01:00.1: claimed by stub
[    0.863394] pci-stub: add 10DE:1380 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    0.863397] pci-stub 0000:01:00.0: claimed by stub
[    0.863399] pci-stub: add 1106:3483 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
```

The last one (1106:3483) is my USB controller. It's added but not claimed and I don't get why... any help appreciated, thx.

Sorry I didn't get back to you earlier on this.

I'm afraid I never got it working really. I mean, it works because I can still pass through and use the card but its not bound to vfio all the time. 

An issue I finally tracked down today is that the system can't suspend or hibernate after I've started and shut down the VM with the USB3 controller passed through to it because something goes screwy if a keyboard is attached. It just gets stuck at a black screen, power on fans running when trying to suspend or hibernate. If I unplug the keyboard, suspend works.

I've had issues with usb devices not being in the right state like this before.

I'm going to see if I can just find a way to manual unbind it and then bind it to vfio-pci after startup and hope that at least resolves my issues.

---

