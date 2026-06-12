---
title: "Adding PCI Harware into Virtual Machines"
date: 2016-08-08
forum: Virtualisation
---

### Post by h03ein72 on 2016-08-08
Hey guys,

I have a problem with adding of pci hardware to vmware, there is no option to do that.

[IMG]http://hosseinvahabi.ir/vmware.png[/IMG]

 I red something about [COLOR=#242729][FONT=Arial]vSphere or [/FONT][/COLOR]VMDirectPath I/O on VMware. meantime my pc doesn't support vt-d and my current installed operating system is windows 7 32 Bit. PLEASE :cry:, give me one way to add this type of hardware. I really disappointed to run windows with virtual machine in my old system. And in the end doesn't matter what virtual machine you suggest, give me something that work!

Thank You.

---

### Post by QIII on 2016-08-08
Moved to Virtualisation.

---

### Post by MAFoElffen on 2016-08-09
I see those options in Settings > Add new hardware as Grayed Out at the moment...

So after you installed your Windows 7 VM Guest, did you start it up and install VMware Tools? After that, then shutdown the VM Guest > Settings >  Add Hardware... Still Grey Out?

---

### Post by h03ein72 on 2016-08-14
Hello, thanks for reply. I installed the vmware tools and I don't care about add hardware in vmware. I want to add my pci hardware and there is no option to add DVB card to my virtual windows 7 (in device manager - nothing apear as a pci card). Thank You.

---

### Post by KillerKelvUK on 2016-08-14
Hi, you've said you PC doesn't support vt-d, this is a mandatory requirement for PCI passthrough to work.

---

