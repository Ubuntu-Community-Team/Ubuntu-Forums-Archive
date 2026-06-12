---
title: "Anyone Using SR-IOV for KVM?"
date: 2010-04-02
forum: Virtualisation
---

### Post by nutznboltz on 2010-04-02
One of the issues I have with KVM is that the I/O performance is hampered by having to push I/O through QEMU.  For some time I have known about the AlacrityVM project's efforts to overcome this:
[http://developer.novell.com/wiki/index.php/AlacrityVM](http://developer.novell.com/wiki/index.php/AlacrityVM)

Today I found out that Red Hat is using SR-IOV as a different way to address the KVM I/O performance issue:
[http://fedoraproject.org/wiki/Features/SR-IOV](http://fedoraproject.org/wiki/Features/SR-IOV)

Because SR-IOV requires special hardware it currently only works on a very few NICs.  Kernel 2.6.30 only supported the Intel® 82576 Gigabit Ethernet Controller and kernel 2.6.31 added the Neterion® X3100™ series (Neterion X3110 and Neterion X3120.)  Broadcom makes the BCM57712 which has hardware support for SR-IOV but I have not yet seen evidence that the Linux kernel has a driver to exploit SR-IOV on that NIC.

Is anyone actually using this stuff?

---

### Post by nutznboltz on 2010-04-02
I found the product sheet for the Dual-port Intel® Gigabit ET Multi-Port Server Adapters with the Intel® 82576 Gigabit Ethernet Controller chipset which retails for under $200

[http://edc.intel.com/Link.aspx?id=2372](http://edc.intel.com/Link.aspx?id=2372)

It states:
> PC-SIG SR-IOV implementation (8 virtual functions per port)

Provides an implementation of the PCI-SIG standard for I/O Virtualization. The physical configuration of each port is divided into multiple virtual functions. Each virtual function is assigned to an individual virtual machine directly by bypassing the virtual switch in the Hypervisor, thereby resulting in **near-native performance**. It is also integrated with Intel® VT1 for Directed I/O (VT-d) to provide data protection between virtual machines by assigning separate physical address in the memory to each virtual machine.
(emphasis mine)

---

### Post by ElllisD on 2010-10-28
Just some links on the subject of VT-c that I came across while looking into this- in case someone finds them useful:

[http://download.intel.com/design/network/applnots/321211.pdf](http://download.intel.com/design/network/applnots/321211.pdf)
[http://www.linux-kvm.org/wiki/images/6/6a/KvmForum2008%24kdf2008_7.pdf]("http://www.linux-kvm.org/wiki/images/6/6a/KvmForum2008%24kdf2008_7.pdf")
[http://www.mail-archive.com/kvm@vger.kernel.org/msg27860.html](http://www.mail-archive.com/kvm@vger.kernel.org/msg27860.html)
[http://thread.gmane.org/gmane.linux.kernel.mm/38508](http://thread.gmane.org/gmane.linux.kernel.mm/38508)
[http://fedoraproject.org/wiki/Features/SR-IOV#Completed](http://fedoraproject.org/wiki/Features/SR-IOV#Completed)
[http://www.intel.com/technology/platform-technology/virtualization/VMDq_whitepaper.pdf](http://www.intel.com/technology/platform-technology/virtualization/VMDq_whitepaper.pdf)

These Intel 82598EB Dual 10Gb NICs can be found on eBay relatively cheap, although it still seems steep to me. Pay to play I suppose.
[http://ark.intel.com/Product.aspx?id=36918](http://ark.intel.com/Product.aspx?id=36918)

---

### Post by Nevill.Burn on 2010-10-30
I would suggest the IOGEAR one I've linked below. It does have problems  with NVIDIA chipset so you may need to also buy a PCI card to plug it in  to.

---

### Post by nutznboltz on 2010-11-18
I didn't go looking for Ubuntu documentation for using SR-IOV yet (due to my pessimistic-but-probably-true assumptions that there isn't any *feel free to prove me wrong*.)

Here's the RHEL 6 documentation:

[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization/chap-Para-virtualized_Windows_Drivers_Guide-SR_IOV.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization/chap-Para-virtualized_Windows_Drivers_Guide-SR_IOV.html)

---

