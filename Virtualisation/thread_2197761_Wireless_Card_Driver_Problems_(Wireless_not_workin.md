---
title: "Wireless Card Driver Problems (Wireless not working after install)"
date: 2014-01-05
forum: Virtualisation
---

### Post by florrts on 2014-01-05
Hello, i'm new to this but i've been searching online a lot and can't seem to find a solution. 

I installed Ubuntu (12.04 32 bit) on a Virtual Machine (VMware) and i can't get the wireless connection to work. I can't even find what wireless card i have so i'm pretty lost.
I tried looking for the Network Controller using the lspci command on the terminal but it didn't show up.

lspci :
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB controller: VMware USB2 EHCI Controller
02:05.0 SATA controller: VMware Device 07e0
02:06.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)

i also tried the iwconfig command but nothing came up.

iwconfig :
lo        no wireless extensions.


eth0      no wireless extensions.


eth1      no wireless extensions.

Any help would be greatly appreciated. I have been dealing with this problem for a while and have no idea as to how to proceed. 
Thank you in advance!

Also, i don't know if this might be relevant but i'm on a late 2009 Macbook (Model A1342)

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Virtualisation**.*

Have you got guest additions installed? (The extension pack?) Might help.

Not sure that you'll get a lot of help with this as you are using Windows as a host, not Ubuntu, but you could get lucky. I would have thought that if Windows was online then the VMs would be to. Obviously not.

---

### Post by TheFu on 2014-01-05
TL;DR
However, the physical card inside the physical machine does NOT matter to any virtual machine clientOS. For every clientOS, it is best to select either the virtIO (or Intel PRO/1000 if virtIO isn't available) NIC to be presented to each client.

If you can't see the wifi card from the hostOS ... I can't help. Sorry.

---

### Post by chili555 on 2014-01-05
Please check here: [http://ubuntuforums.org/showthread.php?t=2125663&p=12557827#post12557827](http://ubuntuforums.org/showthread.php?t=2125663&p=12557827#post12557827)

---

### Post by florrts on 2014-01-05
Okay so i looked at the guest additions and all the additional tools were installed, however i started reading up a bit and found that you could bridge your connection to your main operating system one (i don't understand this very well but that's what i understood. apologies if i'm somewhat wrong.)

Basically what i did, in case someone else has this problem, is i went under Virtual Machine, Network Adapter, Network Adapter Settings and i changed the way it was connected to the network and i chose bridged Wi-Fi. My main OS asked me for my password, i wrote it and after that i could get online from my Virtual Machine.

If the problem persists, you might want to have a look at this video that helped me a bit:
[https://www.youtube.com/watch?v=AsSDXznIhGc](https://www.youtube.com/watch?v=AsSDXznIhGc)

Hope it serves as future reference!
Thanks guys!

---

