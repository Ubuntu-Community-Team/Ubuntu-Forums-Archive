---
title: "K8N-LR second BCM5721 issue"
date: 2008-05-22
forum: Server Platforms
---

### Post by jseifert on 2008-05-22
First off I know little about Linux.

I have been working on this issue for almost 2 weeks now, and can't seem to find an appropriate fix.

The Asus K8N-LR has two onboard BCM5721 gigabit nics.  One of them is detected and configured fine during the install of Dapper.  The second one is not detected at all.  I have the same issue after installing Gutsy and Hardy.

How can I get Dapper to detect the second nic?

lspci output:
```
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:02:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
0000:04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
0000:06:05.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)

```

Maybe I'm searching in the wrong place for a fix.

Any help would be greatly appreciated.

---

### Post by jseifert on 2008-06-01
It's sad that no one here could help me.  Either way I found a fix...Windows 2000 Server, and all is good now.

---

### Post by windependence on 2008-06-02
> **jseifert said:**
> It's sad that no one here could help me.  Either way I found a fix...Windows 2000 Server, and all is good now.

I'm sure we could have easily solved this if you would have given it a chance. I just now saw this post.

Have fun with Windoze.

-Tim

---

