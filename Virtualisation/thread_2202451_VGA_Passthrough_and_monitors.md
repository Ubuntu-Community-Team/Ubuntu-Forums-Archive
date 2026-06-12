---
title: "VGA Passthrough and monitors"
date: 2014-01-29
forum: Virtualisation
---

### Post by spupazza on 2014-01-29
Sorry to ask, but I never found an info on this:
I understand that for vga-passthrough I'd need a secondary vga to use, and a cpu and mb that support vt-d/iommu.

What I need to know is if both the vga (the one used by that host and the one passthrough'ed to the guest) need to be attached to the monitor, or just the
one that powers the host has to be attached to the monitor
Can anyone pls clarify this?

---

### Post by TheFu on 2014-01-31
I think 2 monitors are needed, but this sort of passthru is fairly recent and experimental. I've never used it.
Also, it might help if we knew which virtualization was being used.

---

### Post by spupazza on 2014-02-01
Thanks for your reply.
I was thinking about trying Virtualbox first, and if not working with it then try kvm.

---

### Post by TheFu on 2014-02-01
If you are new to virtualization, note that this is "experimental" ... that means unstable.  If you really need it, perhaps VMware Workstation (the commercial version) would be a better choice?
[https://superuser.com/questions/663837/cannot-setup-pci-passthrough-for-display-adapter-in-virtualbox](https://superuser.com/questions/663837/cannot-setup-pci-passthrough-for-display-adapter-in-virtualbox) from November says that it doesn't work.
You've probably already seen this [http://www.virtualbox.org/manual/ch09.html#pcipassthrough](http://www.virtualbox.org/manual/ch09.html#pcipassthrough) too. Be certain when you rebuild the hostOS kernel to enable IOMMU (step 5).   I checked a default kernel for a 12.04 KVM host and it had the three things mentioned in the 2nd link enabled already. That is a good sign.  The machine doesn't have vbox on it or a monitor connected.  It is a pure server. 

 I need to read up on KVM VGA-passthru. Very interesting.

Update: [http://ubuntuforums.org/showthread.php?t=2111175](http://ubuntuforums.org/showthread.php?t=2111175) has a bunhc of interesting comments and links. Mostly for using Xen and ATI cards.  I left Xen a few years ago due to maintenance issues and prefer nVidia. [http://forums.linuxmint.com/viewtopic.php?t=112013&f=42](http://forums.linuxmint.com/viewtopic.php?t=112013&f=42) is also interesting.

---

### Post by spupazza on 2014-02-02
Thanks a lot for your reply.
I read the message you mentioned about the guy who failed to pci-passthrough with virtualbox.
That guy though didn't seem to have read the virtualbox manual: pci-passthrough is supported only with Linux hosts. That guys had WServer 2012 as host, so he could never be successful.

KVM has been proven successful (I'm unsure if it's more or less successful than Xen). The fact is that I prefer Virtualbox (if working) as solution since I use it since many years,
as also I like some of the features that I'm unsure if KVM has it: seamless mode (which I prefer to Unity in vmware) and the way Virtualbox share folders with the host (it's a long story, but basically
I'm using a custom windows 7 image with many features removed -for optimizaztion purpose- and many network features like sharing folders -necessary with other virtualizer to get shared folders working-
are not needed with virtualbox). 
Moreover I use genymotion to virtualize android, and genymotion use necessarily virtualbox.
So virtualbox fits perfectly my needs, and even more so if the pci-passthrough gets working. KVM would be my last resort.

---

### Post by heiko_s on 2014-04-14
> **spupazza said:**
> Sorry to ask, but I never found an info on this:
I understand that for vga-passthrough I'd need a secondary vga to use, and a cpu and mb that support vt-d/iommu.

What I need to know is if both the vga (the one used by that host and the one passthrough'ed to the guest) need to be attached to the monitor, or just the
one that powers the host has to be attached to the monitor
Can anyone pls clarify this?

1. Both VGA cards need to be attached to the screen, or you need 2 screens.

2. VGA passthrough is not that experimental anymore. I'm using it for the past 2 years, with different Linux Mint/Ubuntu releases.

---

### Post by pgreenwood on 2014-04-17
Hello, and thank you for your input -- My plan was to launch a mythbuntu 12.04 frontend 32-bit virsh Guest on my 32-bit AVLinux (Debian) Host. The backend hardware is a Dell E310 P4 with 64-bit Mythbuntu 12.04. The frontend hardware is Dell Vostro 1520; Intel Core Penryn T6670,2.2GHz; 4GB DDR2 800MHZ 2 DIMM; Intel Integrated GMA 4500MHD and single VGA port. Once I get networking working on the VM I planned to then patch the Mythbuntu VM frontend to my TV with a VGA cable. The sense of my research is this is just never going to work on this hardware regardless of which hypervisor I use. Agree?

---

### Post by TheFu on 2014-04-17
No, it won't for a few reasons.
* Wrong CPU (no VT-d)
* Wrong video card (not ATI)

---

### Post by pgreenwood on 2014-04-18
@TheFu, this is my CPU -- [http://ark.intel.com/products/42109/Intel-Core2-Duo-Processor-T6670-2M-Cache-2_20-GHz-800-MHz-FSB](http://ark.intel.com/products/42109/Intel-Core2-Duo-Processor-T6670-2M-Cache-2_20-GHz-800-MHz-FSB). I have used qemu virtualization with it; got sound working; but I'm definitely a noobie in this area. I can see that VGA passthrough is a challenge, if possible at all. But the mobo has two display outs - one for the laptop screen; the other for the VGA port. I "just" want to send VM video output to VGA. Thanks for your input!

---

