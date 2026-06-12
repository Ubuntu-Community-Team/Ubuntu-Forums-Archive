---
title: "virtualbox: audio card passthrough?"
date: 2015-08-08
forum: Virtualisation
---

### Post by PabloSenz on 2015-08-08
Host: Ubuntu
VM: Virtualbox
Guest: WinXP


I&#8217;ve got a SoundBlaster AudigyRx card. I&#8217;d like to install its programs & drives from the Audigy Installation CD into my WinXP guest, but the card is not seen from inside VirtualBox and therefore the installation is aborted. Would it work if I attached the PCIe card to VirtualBox, as the VB Manual instructs in Chapter 9? It says I could do it by using a command like:


«VBoxManage modifyvm "VM name" --pciattach 02:00.0@01:05.0»


where &#8220;01:05.0&#8221; is the bus/device/function of the PCI address.


If it *is* possible, how do I find an available PCI address inside the guest?

Thank you for any help!

---

### Post by TheFu on 2015-08-09
[https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough) explains it.  Before attempting this, does the hardware and BIOS meet those 6 requirements?

---

### Post by PabloSenz on 2015-08-09
> **TheFu said:**
> [https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough) explains it.  Before attempting this, does the hardware and BIOS meet those 6 requirements?

Thank you for you answer!
I mentioned Chapter 9 in Virtualbox&#8217;s manual as I wished to avoid people repeating it. But now that you&#8217;ve specifically mentioned the 6 requirements&#8230; I checked and am sure about and the first 4 (indeed, I&#8217;ve had to replace my PCU for an IOMMU-compliant one, which Intel calls &#8216;Vt-d&#8217;), but I can&#8217;t say I have checked the last 2. I assumed that, having the latest version of Ubuntu installed, the Linux kernel requirements would be in place, but I haven&#8217;t really checked them. Do you know how to do it? And if they&#8217;re ok, does it follow (as my first assumption was) that all I need to know is the PCI address in the guest?

---

