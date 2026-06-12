---
title: "ACS override patch on Ubuntu 16.04"
date: 2016-06-27
forum: Virtualisation
---

### Post by ingenium2 on 2016-06-27
I'm trying to make use of SR-IOV on my network card, and it appears that because Intel didn't implement ACS on the Xeon E3-1245 v5 (Skylake), the network cards I'm trying to assign to a guest are in the same IOMMU group as a PCI Express Root Port:

```
IOMMU group 6        
        00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1)
        07:00.0 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)
        07:00.1 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)

```

When I enable vfs in the igb module, the virtual interfaces also show in group 6. When I try to assign one them to a kvm guest, I get the error:
```
[COLOR=#000000]vfio: error, group 6 is not viable, please ensure all devices within [/COLOR][COLOR=#000000]the iommu_group are bound to their vfio bus driver.[/COLOR]
```

If I assign 07:00.01 and 07:00.1 to vfio-pci, then I lose the virtual interfaces and still get the error since the Root Port at 00:1d.0 isn't bound to vfio.

I believe the solution to this is to use the acs_override kernel patch. However I can't find a link to one that applies for the 4.4 kernel in Ubuntu 16.04. Is it already included? If not, does anyone have a link to one that works? Or is there some other quick or workaround I can use to properly assign this to a VM? I won't be using these cards on any other VMs, so I don't care if there's not proper DMA isolation between guests since there's only 1 guest.

Right now I have regular PCI passthrough working fine, but the DMA copy operations are killing my CPU (maxes out 2-3 cores transferring data at 150 mbps, with the interrupts associated with vfio-msix being the culprit). SR-IOV will eliminate this which is why I want to use it.

---

### Post by MAFoElffen on 2016-06-27
Does this help?
[http://www.zerg.sc/technote/?p=241](http://www.zerg.sc/technote/?p=241)
[http://www.slideshare.net/juet-y/sr-iovdebian10](http://www.slideshare.net/juet-y/sr-iovdebian10)

---

### Post by ingenium2 on 2016-06-27
> **MAFoElffen said:**
> Does this help?
[http://www.zerg.sc/technote/?p=241](http://www.zerg.sc/technote/?p=241)
[http://www.slideshare.net/juet-y/sr-iovdebian10](http://www.slideshare.net/juet-y/sr-iovdebian10)

Thanks, those are basically the guides I followed trying to set it up. However in the slides, you can see they are using a Xeon E5 series CPU, which supports ACS so the IOMMU groups are setup properly (separate IOMMU group per virtual interface). 

The Xeon E3 series (and all Skylake CPUs) do not support ACS, so too many things get lumped into a single IOMMU group preventing it from working properly. There is a patch from the 3.x kernel days that basically forced ACS to work anyway (designed for the Xeon E3v3 and Core i5/i7), albeit at the expense of possibly leaking of DMA access between guests, and apparently "newer kernels" (from posts in 2014) have "quirks to work around this", but I can't find any information about what these quirks are or how to enable them. Some distributions apply the "acs override patch" to their kernels, but I don't believe Ubuntu did as of 14.04, but they may have in 16.04?

---

### Post by MAFoElffen on 2016-06-27
The 3.x patch was talked about here: [http://ubuntuforums.org/showthread.php?t=2278454](http://ubuntuforums.org/showthread.php?t=2278454)

---

### Post by ingenium2 on 2016-06-27
> **MAFoElffen said:**
> The 3.x patch was talked about here: [http://ubuntuforums.org/showthread.php?t=2278454](http://ubuntuforums.org/showthread.php?t=2278454)

Thanks, so hopefully if I apply that patch to the 4.4 kernel in Ubuntu it will work...

RedHat seems to have some quirks to allow it to work in a PCH PCI slot (which is where my card is): [https://bugzilla.redhat.com/show_bug.cgi?id=1113399](https://bugzilla.redhat.com/show_bug.cgi?id=1113399)

---

### Post by MAFoElffen on 2016-06-27
Good luck and keep us posted how it goes for you.

---

### Post by KillerKelvUK on 2016-06-29
Odd, prior to 16.04 I needed to patch the kernel to provide acs override as my IOMMU separation wasn't sufficient to enable GFX passthrough.  However since 16.04 I've not needed to patch anything and my pci devices are cleanly separated out across the groups, I *assumed* the acs patches or their equivalent had been merged upstream prev and I'd simply caught them up, I don't even have the kernel boot parameters anymore?

---

### Post by MAFoElffen on 2016-06-29
So if there, then where is your error
```

vfio: error, group 6 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver.

```
...is saying that something in the group is still bond to the host's kernel, because it is not blacklisted ... or not bound the vfio driver that is being used to pass it thorugh ,,, so is no free to be passed through, right? Which brings up the question if it is committed or missing.

---

### Post by ingenium2 on 2016-06-30
Yes, that error is there. But the issue is that when I enable SR-IOV, it puts the virtual devices in group 6 along with the physical NICs (a single card with 2 ports). If I detach the physical NIC and attach that to vfio, then all the SR-IOV devices disappear. So it seems that the physical NICs need to remain attached, and the virtual NICs should be put into a separate IOMMU group, but they're not, which prevents them from being used.

I also tried to attach all the devices except the Root Port, and I still get that error. You cannot detach the Root Port from the host, or it won't work anymore apparently.

---

### Post by MAFoElffen on 2016-07-01
In what you are trying to do... are you just trying to get more bandwidth? or to dedicate a port to guest?

When you started this thread and I first read it, I was aksing myself why.  There are ways to do both without doing an pci-passthrough. Those ways, at least to me, seems like they effeectively do the same... or am I missing something?

If you want more bandwidth, then bond multiple cards (2 or more) to a bond group device, then set that bond devicebond to a brdge device. 

The other, if you just wanted to bind a NIC to guest, then bind it to a bridge device.

Both ways set a device that is used within your virtual network that can be use by one or more guests. That is your end goal right? Sorry if I missed something what you are trying to do.

Unless your really need to use some internal hardware feature that is on that card... that a guest needs to physically have access to...

---

### Post by ingenium2 on 2016-07-01
> **MAFoElffen said:**
> In what you are trying to do... are you just trying to get more bandwidth? or to dedicate a port to guest?

When you started this thread and I first read it, I was aksing myself why.  There are ways to do both without doing an pci-passthrough. Those ways, at least to me, seems like they effeectively do the same... or am I missing something?


The reason I'm doing this is because traditional PCI passthrough has a significant CPU overhead. There is a DMA copy operation that results in pegging 3 cores at 100% for a 150 mbps transfer. I wouldn't be able to hit single gigabit speeds, let alone bonding 2 interfaces together. If I instead assign a virtual NIC to a guest using SR-IOV, then there is no DMA copy and the overhead is avoided. See [https://www.youtube.com/watch?v=hRHsk8Nycdg](https://www.youtube.com/watch?v=hRHsk8Nycdg)

Using a virtio interface still incurs the CPU penalty. The only way around it that I've been able to see is to get SR-IOV working properly.

---

### Post by MAFoElffen on 2016-07-01
So you are doing what I had asked last:
> 
Unless your really need to use some internal hardware feature that is on that card... that a guest needs to physically have access to...

Which you wanting to use a switching feature on the card. Sort of like the TOE (TCP Offload Engine) hardware feature on my servers... but mine does it whether the internal target is virtualized or not, so I sort of take that for granted.

---

### Post by KillerKelvUK on 2016-07-02
> **ingenium2 said:**
> The reason I'm doing this is because traditional PCI passthrough has a significant CPU overhead. There is a DMA copy operation that results in pegging 3 cores at 100% for a 150 mbps transfer. I wouldn't be able to hit single gigabit speeds, let alone bonding 2 interfaces together. If I instead assign a virtual NIC to a guest using SR-IOV, then there is no DMA copy and the overhead is avoided. See [https://www.youtube.com/watch?v=hRHsk8Nycdg](https://www.youtube.com/watch?v=hRHsk8Nycdg)

Using a virtio interface still incurs the CPU penalty. The only way around it that I've been able to see is to get SR-IOV working properly.

Hey, so thanks for the link...nice little intro to SR-IOV for me.  I've no real use-case here so I can only offer parallel's which maybe of no use so please tell me to shut up...

I have a DVB card (08:00.0) I pass-thru and its IOMMU grouping puts it in the same group (group 19) as a PCI Bridge device so a little like yours.  For me I assign the DVB card to the VFIO driver on boot and thats it, I leave the PCI Bridge well alone.  As a result the DVB card shows the vfio-pci driver in use but the PCI Bridge device shows the pcieport driver in use.

```

sh iommu.sh 
### Group 0 ###
    00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
### Group 1 ###
    00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
    01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
### Group 2 ###
    00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
### Group 3 ###
    00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
### Group 4 ###
    00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
### Group 5 ###
    00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
### Group 6 ###
    00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
### Group 7 ###
    00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
### Group 8 ###
    00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
### Group 9 ###
    00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
### Group 10 ###
    00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
### Group 11 ###
    00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
### Group 12 ###
    00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
### Group 13 ###
    00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
### Group 14 ###
    00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
    00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
    00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
### Group 15 ###
    03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
### Group 16 ###
    04:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
### Group 17 ###
    05:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
    06:00.0 Audio device: Creative Labs SB Recon3D (rev 01)
### Group 18 ###
    05:03.0 PCI bridge: ASMedia Technology Inc. Device 1184
    07:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
### Group 19 ###
    05:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
    08:00.0 Multimedia video controller: Spin Master Ltd. Device 3038 (rev 01)
### Group 20 ###
    05:07.0 PCI bridge: ASMedia Technology Inc. Device 1184
    09:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
### Group 21 ###
    0a:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

```

```

sudo lspci -s 05:07.0 -v
05:07.0 PCI bridge: ASMedia Technology Inc. Device 1184 (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Bus: primary=05, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: ef800000-ef8fffff
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Downstream Port (Slot+), MSI 00
    Capabilities: [c0] Subsystem: ASRock Incorporation Device 1184
    Capabilities: [100] Virtual Channel
    Capabilities: [200] Advanced Error Reporting
    Kernel driver in use: pcieport
    Kernel modules: shpchp


sudo lspci -s 08: -v
08:00.0 Multimedia video controller: Spin Master Ltd. Device 3038 (rev 01)
    Subsystem: DVBSky Device 0550
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at ef900000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/16 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Kernel driver in use: vfio-pci
    Kernel modules: smipcie

```


How does this compare for you?

[ATTACH]269895[/ATTACH] Just sharing the little script I found online to display IOMMU groupings

---

### Post by ingenium2 on 2016-07-02
I applied the ACS override patch found here [https://github.com/zman0900/linux-vfio-aur/blob/master/override_for_missing_acs_capabilities.patch](https://github.com/zman0900/linux-vfio-aur/blob/master/override_for_missing_acs_capabilities.patch), recompiled 4.4.0-28 and installed the resulting debs, and added pcie_acs_override=passthrough to grub (I verified that it was indeed there upon boot), and the IOMMU grouping was exactly the same... So it appears that even with the ACS override patch it doesn't work. Here's what my IOMMU grouping looks like:

```

### Group 0 ###
    00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
### Group 1 ###
    00:02.0 Display controller: Intel Corporation Device 191d (rev 06)
### Group 2 ###
    00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
    00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
### Group 3 ###
    00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
    00:16.1 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #2 (rev 31)
### Group 4 ###
    00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
### Group 5 ###
    00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
    00:1c.1 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
    00:1c.2 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
    00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
    00:1c.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #7 (rev f1)
    01:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
    02:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
    03:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
    04:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
    05:00.0 PCI bridge: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge (rev 03)
    06:00.0 VGA compatible controller: ASPEED Technology, Inc. ASPEED Graphics Family (rev 30)
### Group 6 ###
    00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
    07:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
    07:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
### Group 7 ###
    00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
    00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
    00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)

```

When I enable the virtual ethernet adapters they also appear under group 6, making them useless.

---

### Post by KillerKelvUK on 2016-07-04
Hi please can you post back the output of the following 2 commands.

sudo lspci -s 00:1d.0 -v
sudo lspci -s 07: -v

Also any log files i.e. if you're using libvirt please share the /var/log/libvirt/qemu/*guestname *file/lineouts.

---

### Post by MAFoElffen on 2016-07-04
By your desciption of what you are trying to do... and what it is not doing... isn't this along the lines of what you want to happen?
```

[**pci-bind-vfio**]("https://github.com/andre-richter/vfio-pci-bind")
This script takes a Domain:Bus:Device.Function string of the form "0000:00:00.0" as command line argument and:

1. Unbinds all devices that are in the same iommu group as the supplied device from their current driver (except PCIe bridges).

2. Binds to vfio-pci:
  i. The supplied device.
  ii. All devices that are in the same iommu group.

3. Transfers ownership of the respective iommu group inside /dev/vfio to $SUDO_USER

```

---

### Post by adam1110 on 2016-07-16
> **ingenium2 said:**
> Thanks, those are basically the guides I followed trying to set it up. However in the slides, you can see they are using a Xeon E5 series CPU, which supports ACS so the IOMMU groups are setup properly (separate IOMMU group per virtual interface). 

The Xeon E3 series (and all Skylake CPUs) do not support ACS, so too many things get lumped into a single IOMMU group preventing it from working properly. There is a patch from the 3.x kernel days that basically forced ACS to work anyway (designed for the Xeon E3v3 and Core i5/i7), albeit at the expense of possibly leaking of DMA access between guests, and apparently "newer kernels" (from posts in 2014) have "quirks to work around this", but I can't find any information about what these quirks are or how to enable them. Some distributions apply the "acs override patch" to their kernels, but I don't believe Ubuntu did as of 14.04, but they may have in 16.04?

Sorry for digging up this post, I've port the ACS override patch to 16.04, tested on 4.4.0-31-generic(from official ubuntu git source)
Use 'patch -p1 < override_for_missing_acs_capabilities-kernel.patch' to commit.

Download link - [https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing](https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing)

---

### Post by MAFoElffen on 2016-07-16
> **adam1110 said:**
> Sorry for digging up this post, I've port the ACS override patch to 16.04, tested on 4.4.0-31-generic(from official ubuntu git source)
Use 'patch -p1 < override_for_missing_acs_capabilities-kernel.patch' to commit.

Download link - [https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing](https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing)
No apology needed. The OP hadn't told us that what he was doing had been resolved yet, and what you added may direct him to a solution. 

Thank you for your valuable input. That is what this forum community is all about: Members helping each other by sharing their experience.

---

### Post by iommu on 2016-07-22
> **adam1110 said:**
> Sorry for digging up this post, I've port the ACS override patch to 16.04, tested on 4.4.0-31-generic(from official ubuntu git source)
Use 'patch -p1 < override_for_missing_acs_capabilities-kernel.patch' to commit.

Download link - [https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing](https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing)


Thanks a lot - this saved my day! See [1].

Will you consider submitting this patch to the official ubuntu kernel?

[1] [http://www.pcengines.info/forums/?page=post&id=77FF51E3-8ACA-4B79-BD2C-1380B9B48B5D&fid=DF5ACB70-99C4-4C61-AFA6-4C0E0DB05B2A&cachecommand=bypass&pageindex=2](http://www.pcengines.info/forums/?page=post&id=77FF51E3-8ACA-4B79-BD2C-1380B9B48B5D&fid=DF5ACB70-99C4-4C61-AFA6-4C0E0DB05B2A&cachecommand=bypass&pageindex=2)

---

### Post by ingenium2 on 2016-07-28
It turns out the issue is Skylake. I applied the following patch from 4.7 to the 4.4 kernel in 16.04 and everything was isolated in separate IOMMU groups. No need for the ACS patch. So it should just work in 16.10, assuming it ships with the 4.7 kernel.

[http://www.serverphorums.com/read.php?12,1453397](http://www.serverphorums.com/read.php?12,1453397)

I'll post an actual patch file that applies cleanly to the 4.4 kernel once I get it ready. 

I'm also making some patches to the Intel drivers to allow guests to change their MAC address. Apparently setting 'spoofchk off' doesn't ACTUALLY allow guests to change their MAC address (which is necessary for 802.3ad bonding in a guest), even though it's supposed to. You also need to comment out the check in drivers/net/ethernet/intel/igb/igb_main.c [https://communities.intel.com/thread/99310](https://communities.intel.com/thread/99310) So I guess I'm stuck patching and compiling my own kernel for the foreseeable future.

I'll also note that the high CPU usage on the host is still present, albeit slightly reduced. Doing a speedtest on the guest (150 mbps connection) results in 2/8 CPUs (4 cores, hyperthreaded) pegged at 100% on the host from the qemu process, but the guest itself shows no CPU usage. It could be a kernel bug as well.... [https://www.redhat.com/archives/vfio-users/2016-January/msg00232.html](https://www.redhat.com/archives/vfio-users/2016-January/msg00232.html)

---

### Post by MAFoElffen on 2016-07-30
Still curious to see how this works out for you...

---

### Post by ingenium2 on 2016-07-30
> **MAFoElffen said:**
> Still curious to see how this works out for you...
Everything works now that I've backported the patch from the 4.7 kernel. No ACS override needed.

```

18:13:57 josh@server ~ for iommu_group in $(find /sys/kernel/iommu_groups/ -maxdepth 1 -mindepth 1 -type d); do echo "IOMMU group $(basename "$iommu_group")"; for device in $(ls -1 "$iommu_group"/devices/); do echo -n $'\t'; lspci -nns "$device"; done; done
IOMMU group 0
    00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:1918] (rev 07)
IOMMU group 1
    00:02.0 Display controller [0380]: Intel Corporation Device [8086:191d] (rev 06)
IOMMU group 2
    00:14.0 USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
IOMMU group 3
    00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    00:16.1 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #2 [8086:a13b] (rev 31)
IOMMU group 4
    00:17.0 SATA controller [0106]: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] [8086:a102] (rev 31)
IOMMU group 5
    00:1c.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #1 [8086:a110] (rev f1)
IOMMU group 6
    00:1c.1 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #2 [8086:a111] (rev f1)
IOMMU group 7
    00:1c.2 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #3 [8086:a112] (rev f1)
IOMMU group 8
    00:1c.3 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #4 [8086:a113] (rev f1)
IOMMU group 9
    00:1c.6 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #7 [8086:a116] (rev f1)
IOMMU group 10
    00:1d.0 PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root Port #9 [8086:a118] (rev f1)
IOMMU group 11
    00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a149] (rev 31)
    00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
IOMMU group 12
    01:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
IOMMU group 13
    02:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
IOMMU group 14
    03:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
IOMMU group 15
    04:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
IOMMU group 16
    05:00.0 PCI bridge [0604]: ASPEED Technology, Inc. AST1150 PCI-to-PCI Bridge [1a03:1150] (rev 03)
    06:00.0 VGA compatible controller [0300]: ASPEED Technology, Inc. ASPEED Graphics Family [1a03:2000] (rev 30)
IOMMU group 17
    07:00.0 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)
IOMMU group 18
    07:00.1 Ethernet controller [0200]: Intel Corporation 82576 Gigabit Network Connection [8086:10c9] (rev 01)
IOMMU group 19
    07:10.0 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 20
    07:10.2 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 21
    07:10.4 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 22
    07:10.6 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 23
    07:11.0 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 24
    07:11.2 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 25
    07:11.4 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 26
    07:10.1 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 27
    07:10.3 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 28
    07:10.5 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 29
    07:10.7 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 30
    07:11.1 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 31
    07:11.3 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)
IOMMU group 32
    07:11.5 Ethernet controller [0200]: Intel Corporation 82576 Virtual Function [8086:10ca] (rev 01)

```

I think the qemu kernel CPU usage during network I/O is fake, or at the very least inaccurate. On a speed test htop showed 100% CPU usage on 2/8 CPUs on the host at 150 mbps. I used iperf to do a LAN speed test (across vlans to force it through the VM running vyos) and saw the exact same CPU usage, except it was doing gigabit speeds. So it seems SR-IOV is working correctly, and either htop is showing incorrect CPU usage for qemu, or there is a qemu/kvm bug that causes it to fully utilize 2 CPUs, but it doesn't seem to be impacting actual performance.

---

### Post by MAFoElffen on 2016-07-31
Congratulations! So this is solved now? (I didn't see it marked as that yet)

---

### Post by ingenium2 on 2016-08-02
Here is a patch file that should apply cleanly to the current 4.4 kernel in 16.04: [https://drive.google.com/open?id=0B8hkQwyNH0AIS19iMmRyQ1l6djg](https://drive.google.com/open?id=0B8hkQwyNH0AIS19iMmRyQ1l6djg)

---

### Post by davidknag on 2016-10-23
> **adam1110 said:**
> Sorry for digging up this post, I've port the ACS override patch to 16.04, tested on 4.4.0-31-generic(from official ubuntu git source)
Use 'patch -p1 < override_for_missing_acs_capabilities-kernel.patch' to commit.

Download link - [https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing](https://drive.google.com/file/d/0B2vXTGt0CnmdTVZiS3p1NnVHUzQ/view?usp=sharing)
Is it possible to make a livepatch of the acs override? I'm on haswell, so I've been using the ACS override patch. It would do wonders in automating gpu passthrough
see: [http://chrisarges.net/2015/09/21/livepatch-on-ubuntu.html](http://chrisarges.net/2015/09/21/livepatch-on-ubuntu.html)

---

### Post by davidknag on 2016-10-28
I've made the ACS Override patch work on 16.10 with haswell by patching 4.8.0 with the patch found here: [https://aur.archlinux.org/cgit/aur.git/tree/?h=linux-vfio&id=7d918b60297b5126fd314bb48a793ef19f9a7e76](https://aur.archlinux.org/cgit/aur.git/tree/?h=linux-vfio&id=7d918b60297b5126fd314bb48a793ef19f9a7e76)

I've also hosted it myself in case the git repo changes when future kernel updates are applied on linux-vfio package, here: [http://in4.us/img/acs480.patch](http://in4.us/img/acs480.patch)

I had some issues compiling the source with 4.8.0 even on a full clean install. The bug related is found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1460768](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1460768)

So, full instructions, make sure yakkety sources are in your sources.list, and only run the command as non-root sudoer for the sake of file permissions
```

cd ~
mkdir kernel
cd kernel
apt-get source linux-image-$(uname -r) 
sudo apt-get build-dep linux-image-$(uname -r)

```
Then add the symbolic links detailed in the bug linked above, and then apply the patch and build
```

cd ~/kernel/linux-*
wget http://in4.us/img/acs-480.patch
patch -p1 < acs-480.patch
fakeroot debian/rules clean

```

---

### Post by AzurianArcher on 2017-09-22
I know this is a little late but since this has a high google rank, I now maintain .deb files for the ACSO patched kernel at [https://queuecumber.gitlab.io/linux-acs-override/](https://queuecumber.gitlab.io/linux-acs-override/) they should be built automatically (though a couple of old versions are missing)

---

