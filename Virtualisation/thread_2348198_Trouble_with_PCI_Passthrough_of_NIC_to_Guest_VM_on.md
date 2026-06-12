---
title: "Trouble with PCI Passthrough of NIC to Guest VM on KVM"
date: 2017-01-01
forum: Virtualisation
---

### Post by ads3 on 2017-01-01
I recently acquired an HP ProLiant DL380 G7, and I'm wanting to create a virtualized environment with it. I figure it'll be a neat learning experience, but I've hit a point where I need some help. My intended architecture will look something like this:
[LIST]
[*]The host OS will be Ubuntu Server 16.04 LTS, running KVM (or libvirt, or virsh - to be honest, I'm not sure what the appropriate terminology here is, I'm welcome to corrections). 
[*]My first virtual machine will be a pfSense router. I intend for one of my server's four NICs to be passed through to this VM, effectively exposing it to the outside world. 
[*]The router's 2nd nic will be attached to a vswitch, and other VMs will attach to this vswitch as well, using the pfSense router for DHCP and Internet access. The host will also receive internet access through this vswitch, via a virtual interface. 
[*]A 2nd physical interface on the server will be routed to this vswitch, so that physical hosts can also use the virtualized pfsense router for internet access. 
[*]One virtual machine will run Windows, and will have a dedicated GPU attached to it via pci-passthrough. 
[/LIST]
So, that's the plan. And its coming along quite well. I've verified that guests are able to attach to the vswitch and get an IP address from the dhcp on the pfsense router. But I'm having issues getting one of my NICs passed through to the pfsense router. Currently, its wan interface is NAT'ed through the host, which I feel defeats the purpose of the router. I've been trying to get pcie passthrough working on this one particular nic, and failing. I'd like to ask you all for help with getting this working and with clearing up any misconceptions I've developed along the way. 

**The Problem**
I'm unable to pass my nic "enp3s0f0" through to a KVM virtual machine. When I attempt to start said virtual machine, I receive one of a few handfuls of errors. 

[LIST]
[*]First error: "fio: error, group 14 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver"
[LIST]
[*]I've tried to fix this one by finding all devices in group 14, and binding them to the vfio driver. Group 14 contained all four of my network interface cards and my iLO controller. 
[*]I used this script to perform the binding:
```

#!/bin/bash
modprobe vfio-pci
for dev in "$@"; do
        vendor=$(cat /sys/bus/pci/devices/$dev/vendor)
        device=$(cat /sys/bus/pci/devices/$dev/device)
        if [ -e /sys/bus/pci/devices/$dev/driver ]; then
                echo $dev > /sys/bus/pci/devices/$dev/driver/unbind
        fi
        echo $vendor $device > /sys/bus/pci/drivers/vfio-pci/new_id
       	echo $vendor $device 
done

``` 
[*]This caused my host to loose network connectivity. All my ssh sessions died, and I lost iLO connectivity. (For reference, iLO is sharing my first Ethernet interface. The interface essentially has 2 mac addresses on it. I'm doing it this way instead of using the dedicated iLO port because I was out of interfaces on my switch.) 
[/LIST]
 [*] Next error: "failed to set iommu for container: operation not permitted"
[LIST]
[*]I don't even know where to start with this one.
[/LIST]
[/LIST]
 
First off, I'll establish some sanity checks.
[LIST]
[*]I've ensured that virtualization is on in my bios, including Intel VT-D. I've also added this line to /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on pcie_acs_override=downstream"
```
I'm not entirely sure what pcie_acs_override does, but it was suggested during my googling. Can anyone explain? I *do* like understanding how these things work.
[*]I can verify that iommu is on by running "dmesg | grep -i "iommu" and seeing that iommu is adding devices to groups. I can see where my nic, with device ID 0000:03:00.0 is being added to group 14, along with my other 3 nics and the iLO hardware.
[*]When I run ```
lspci -nnk
```, and I look for all the devices in group 14, I see, "kernel driver in use: vfio-pci" **after** executing the aforementioned script.
[/LIST]

If any more output is needed, please let me know and I'll be happy to provide. I'm sure you can understand how much I'd like to get over this hurdle, especially since I'm wanting to do GPU passthrough in the future.

---

### Post by KillerKelvUK on 2017-01-02
Hey ad3, I can offer some advice on some of the passthru issues you've shared but I just wanted to understand better and maybe challenge a little your logic of passing through a physical NIC to the pfSense router, especially with you already having created vswitches on the other ports.  What's the point if your end result is that the interface has a unique IP address in a subnet of your choosing?  I understand networking technologies but I'm no expert so maybe I have an overly simplistic view of what you are trying to do and if so then I'll happily butt out or if you want to share the detail then I'll happily be educated also :-)  Last one on this, have you considered the consequences of this going wrong i.e. how portable that virtual machine will be if its entire role is hard locked to a physical NIC?

Right onto the rest...so KVM vs. Qemu vs. Libvirt:  So more googling needed hear to cross-reference interpretations but my offer is that KVM provides hardware acceleration capabilities to Qemu.  Qemu in tern is the application creating the virtual machine and the virtual devices you configure within it, Qemu can either take advantage of the capabilities provided by KVM or not but without them it is less performant.  Libvirt is then an administration layer above KVM and Qemu, its a cross-hypervisor tool-set and configuration framework which means that libvirt can be used with KVM but also Xen, VMware and others.  When used it provides tools like virsh, which is a command line application that allows management of virtual machines, these VM's can be on a single host or many.  By comparison virt-manager is GUI application that provides similar capabilities to virsh but whose features list isn't as long.  Libvirt provides a standards based XML language to define the configurations of a virtual machine that is independent from the hypervisor, as such you can define your guest XML and be ignorant as to whether it will be KVM/Qemu or Xen that will run the guest.  Behind the scenes Libvirt will then do the hypervisor specific translations of the guest XML and so in your configuration if you create, run and manage a guest using the libvirt tool-sets you can see the Qemu command that is run to create the virtual machine in the background (ps aux | grep qemu).


> First error: "fio: error, group 14 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver"

Okay so this is saying the the vfio module cannot passthrough your enp3s0f0 NIC as that NIC is not the only device in IOMMU group 14.  For successful PCI passthrough the PCI devices on the host need to be separated out into individual IOMMU groups, on some hosts this happens transparently due to the efforts put into VFIO and linux kernel development but for some hosts (typically enterprise grade severs  <--sucks I know) it doesn't and manual intervention is required.  I've been helping another user in this forum for the past couple of days and I'd like to point you to a specific post in that thread and the section within it near the start that talks about "Ensuring IOMMU is fully enabled" ([https://ubuntuforums.org/showthread.php?t=2348025&p=13589655#post13589655](https://ubuntuforums.org/showthread.php?t=2348025&p=13589655#post13589655)).  Please can you read that section and ensure the instructions are applied to your host and post back the results of the iommu.sh script that's attached to that post?  My suspicion is that your host is not providing IOMMU separation, that script will show us so then we just need to tackle how to try and force it, best case there is an addition kernel parameter, worst case is you need to manually patch and build the linux kernel.  Coincidentally you've already added a kernel boot parameter into grub "pcie_acs_override=downstream" but not understood that this is part of patching the kernel to create and enable this parameter, ergo its not doing anything.  

Absolute worst case is that those NIC interfaces are all classed as being part of a single PCI device, as you've already tried adding all of them into the guest and it worked, albeit breaking your operate model, you may find you cannot technically achieve what you want with the current hardware capabilities.  As a research pointer for you take a look at SR-IOV which is the intended network virtualisation technology for what you are trying to achieve.

---

### Post by ads3 on 2017-01-02
I'll start off with a graphical representation of my end goal, attached "network.jpg". What I'd like to see in the end is, my pfSense router will be "directly attached" to my Internet connection, on which my ISP will provide an IP address via DHCP. Behind my router will be my LAN. My LAN will contain several VMs connected to the router's virtual "inside" interface via a vSwitch. My host running these VMs will also be connected to this virtual network by the bridge interface that represents this vSwitch. Let's say its interface br0. Additionally, one physical interface on the backside of my server will be attached to the vSwitch as an "access port," meaning that if I connect another PC to this interface (or another switch with several other PCs connected to it!), I want it to receive an IP address from the DHCP on my pfSense router vm. That's the end goal. Temporarily, the server is behind my consumer-grade home router, but since I know my ISP just runs a DHCP, I figure that once I have everything set up, transitioning over to my "new" router will be as easy as moving Ethernet cables around.
 
In case you're wondering why I want to do it this way, well, funny story for you! I have a friend that implemented a very, very similar environment using all Microsoft software. This is essentially friendly competition - "Anything your Microsoft software can do, my open source software can do too!" The fun part is, my friend's hardware is nearly identical to mine. He's also using an HP DL380, just a G6 instead of a G7.

Your script confirms that iommu separation isn't going too well. Output is attached. You can see all four of my NICs and my iLO hardware in Group 14. Per your post in the other thread, I've also modified my /etc/modules. It now contains this text:
```
pci_stub
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
kvm
kvm_intel
```
I've also created /etc/modprobe.d/virt-conf.conf per your other post. 



I've also done some more poking around of my own, and I've made a bit of a breakthrough, I think. I was logged onto my host using virt-manager, and after some tinkering, the gui added this to my pfSense router's xml config:
```

    <interface type='bridge'>
      <mac address='52:54:00:e7:72:9c'/>
      <source bridge='br0'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </interface>
    <interface type='direct'>
      <mac address='52:54:00:b4:f3:a8'/>
      <source dev='enp3s0f0' mode='passthrough'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>

```
I see a few things in here I'd like to point out, too. 
[LIST]
[*]The first interface is a bridge interface, and I've confirmed that it works as expected. Expected operation in this case means that when I boot another VM and give it an interface on this same bridge, it gets an IP address from the DHCP on pfSense. Yay! 
[*]I've also confirmed that attaching an Ethernet cable to my host's interface enp3s0f1 to my desktop PC does give my desktop PC an IP in the range my pfSense router serves. I added this interface to the bridge by placing this text in /etc/network/interfaces:
```
iface enp3s0f1 inet manual
auto br0
iface br0 inet dhcp
    hwaddress ether 80:c1:6e:24:05:4e
    bridge_ports enp3s0f1
    bridge_stp off
    bridge_fd 0
``` 
[*]What I don't understand is why the bridge interface references a PCI defice. I looked in lspci, and saw that the device it points to is in group 4: "00:04.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 4 (rev 13)" 
[*]That "direct & passthrough" interface certainly points to the right interface, but my host can still see it in ifconfig. I don't understand why this is. 
[*]This bridge interface br0 DOES have an IP address in the subnet that pfSense serves, but neither my desktop PC nor another VM are able to ping it, ssh to it, etc. 
[*]The pfSense router can't ping the host either, even though it seems to be giving it an IP address. 
[*]Take a look at my host's ifconfig, attached. It seems a little fishy. It can still see the interface that pfSense is using as a WAN interface. I don't think that what I've accomplished here is a "passthrough" in the same sense that I was seeking to achieve. This seems like some kind of software passthrough, as opposed to a hardware (firmware?) one. 
[/LIST]
Being unable to access the host is a bit of a game-killer, since I need to be able to manage my virtual machines. It feels like I'm on the right track, though.

---

### Post by KillerKelvUK on 2017-01-02
Hey, so first off I'm 100% game-on at sticking to your M$ buddy and showing him that open-source is #1!

So I'm still wrapping my head around what you want to achieve and I think I understand you but want to check..

High level simplistic Kelvin type way of understanding it...you want to take your small home DSL/Router/Switch (or similar) device that your ISP provided and pretty much virtualise it using pfSense and like its physical counter part make this the internet gateway, firewall and DHCP server for your local subnet(s).  This sounding like I've understood you?

When you use the word/term vSwitch are you specifically talking about product Open vSwtich or are you just meaning a virtual switch of some description?

Will come back to the above once you've had chance to respond, regards the rest of your post...

So first off regarding the XML you've found for the network devices; these remember are virtual devices pertaining to only the virtual guest you are creating ergo the device references to PCI buses and ports are the virtual device specifications.  If you were to look into the guest you created with the XML you will find a NIC showing itself as an Intel e1000 device located on a PCI bus at slot 4 and it will have a MAC address as per the XML.  The only part of the XML that references a component on your host is the 'source bridge' or 'source device'.  That help clear things up?

The bridge interface you have discovered labelled 'br0' has been created using the linux-bridge binary/package, this package is a dependency when installing libvirt, virt-manager in ubuntu as it is the default network management tooling for libvirt.  Open vSwitch is an alternative to the linux-bridge package and is more feature rich/capable to my knowledge although I've no practical experience with OVS...I think this is where I may have been reading too much into your words maybe e.g. vSwitch?

So your changes to /etc/network/interfaces effectively created a virtual switch located on your host using the linux-bridge package.  The virtual switch, called 'br0' has one of your physical interfaces mapped into it (enp3s0f1) and you've configured it for DHCP so basically its broadcasting looking for an IP address.  So when you spin up your pfSense guest and its has a virtual NIC connected into the same virtual switch you created (br0) then as pfSense has a DHCP server running it recevies the broadcasts your host is sending from br0 and responses accordingly i.e. it gets an IP address.

The reason you can't ping or ssh is because you have two different subnets in use (br0 using a 10.0.0 network and enp3s0f0 using a 192.168.1 network) and I'm guessing your pinging or ssh'ing from a device that has no route from the 192.168.1 network to the 10.0.0.

> Take a look at my host's ifconfig, attached. It seems a little fishy. It can still see the interface that pfSense is using as a WAN interface. I don't think that what I've accomplished here is a "passthrough" in the same sense that I was seeking to achieve. This seems like some kind of software passthrough, as opposed to a hardware (firmware?) one.

So you're right its a software passthrough kinda but I actually think this is closer to what you ultimately need but we can get to that.  On your host you can see the guest virtual NIC's via ifconfig as they are labelled vnetx, x being a numerical value which increments for each concurrent guest you run on the same virtual switch. So look at ifconfig pre and post starting any virtual machines, you'll see what I mean, note however the host doesn't report the guests IP credentials via ifconfig.

---

### Post by ads3 on 2017-01-02
You understand my goal perfectly. :) When I use the term vSwitch, I'm just meaning a generic virtual switch of some kind. It doesn't really matter to me what kind, either. All I care about is exposing "virtual interfaces" on the vSwitch to my guest VMs, my host OS, and any and all devices on the other side of interface enp3s0f1. I'm kinda thinking in terms of the physical hardware I'm representing. A Cisco 24 port switch is just a layer 2 device that connects many devices that share a subnet to each other. Likewise, my vSwitch is supposed to facilitate communication between some VMs and physical hosts.
At this point, I think my biggest source of confusion is my understanding of "passthrough." When I'm using VirtualBox on a Windows host, and I passthrough a flash drive to my guest, that flash drive is no longer visible to the host. I can check my Device Manager, and not see the flash drive. But with the KVM stack, when interface enp3s0f0 is passed through to my pfSense guest, I can still see the interface with ifconfig, and its ipv4 address. The interface is still "visible" to the host. 

I **would **like to PCI passthrough my "wan" interface to my pfSense vm, because when I shut off my pfSense vm, my host suddenly has a public address and is visible to the Internet. (of course, the host is currently behind the home router that I'm wanting to replace, but the end result is the same). But would you agree that such a low-level passthrough is looking impossible with my configuration? Have we established that all four of my network interfaces are essentially on the same pci card, and that passing a single interface through to a vm isn't going to happen?

Another question... Are we looking at PCI, or PCI Express? At this level, are the two terms interchangeable? I know that, with PC hardware, PCI is an old-fashioned parallel expansion interface and PCIe is our modern serial equivalent. The two interfaces are physically incompatible. But the lspci command shows me PCIe devices. My desktop PC's gpu shows up at 03:00.0, and I know for sure it uses a PCIe interface. In the future, I am going to be doing some gpu passthrough to a vm... I initially had a feeling that passing a nic through would be a simpler task.

---

### Post by KillerKelvUK on 2017-01-02
Good news, we're on the right track!

Okay so I've had a quick look at pfSense myself and I think I know where some of your language comes from which helps (I may also explore more with pfSense as well so thanks for bringing this up :popcorn:.)

Regards you're confusion of "passthrough" I don't think you have any...a device that is passed-through to a guest is no longer accessible by the host.  The host will still show some information about the hardware as the host is facilitating the pass-thru to the guest but the actual device control is via the guest.  The example you quote above...

> But with the KVM stack, when interface enp3s0f0 is passed through to my pfSense guest, I can still see the interface with ifconfig, and its ipv4 address. The interface is still "visible" to the host. 

...so this warrants a little more research.  According to [https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-attch-nic-physdev.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-attch-nic-physdev.html) you've used configurations specifically for SR-IOV capable NIC's, is yours cos if so then forget PCI based passthrough SR-IOV is the way to go.

Regards passthrough of the NIC PCI device, looking at your previous IOMMU output they look like separate devices but I'm honestly guessing.  What I can say is that you have zero IOMMU separation and so this would need to be hacked in, I've seen some other users in recent months post here about doing the same for their Xeon based servers to get this work.  So basically you could look into this but if you aren't familiar with building linux binaries then building a linux kernel will not be straight forward for you and finding the right patches for the latest kernel will likely be difficult.  All in all I'd suggest this is more hassle than its worth and we can get to what you want via a slightly different route.

I'd say lets cover off the SR-IOV first and then take your network design from there?

---

### Post by KillerKelvUK on 2017-01-02
Looking promising for SR-IOV...[https://h20195.www2.hpe.com/v2/getpdf.aspx/4AA5-7050ENW.pdf?ver=1.0](https://h20195.www2.hpe.com/v2/getpdf.aspx/4AA5-7050ENW.pdf?ver=1.0)

See page 8, can you follow those instructions to verify SR-IOV capabilities on the NIC's?

---

### Post by ads3 on 2017-01-02
It looks like we're a no go on SR-IOV. According to the white paper you found (Thank you for that, you totally beat me to it!) I should expect to see:
```
Capabilities: [160 v1] **Single Root I/O Virtualization (SR-IOV)**
IOVCap: Migration- Interrupt Message Number: 000
IOVCtl: Enable-Migration-Interrupt-MSE-ARIHierarchy+
IOVSta: Migration-
```
etcetera. 


Instead, I see this. SR-IOV does not seem to be present under any of the Capabilities fields. I'll do some more poking around, though - that white paper you found was for gen 9 and 8 ProLiants, and mine is a gen 7, so maybe there's some more documentation out there that's a bit more specific for my system. Thank you so much for your help thus far!
```

$ sudo lspci -vvv -s  0000:03:00.0
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
        Subsystem: Hewlett-Packard Company NC382i Integrated Multi-port PCI Express Gigabit Server Adapter
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: HP NC382i Multifunction Gigabit Server Adapter
                Read-only fields:
                        [PN] Part number: N/A
                        [EC] Engineering changes: N/A
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 30 33 43
                        [RV] Reserved: checksum good, 37 byte(s) reserved
                End
        Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-
                Vector table: BAR=0 offset=0000c000
                PBA: BAR=0 offset=0000e000
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 4096 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Exit Latency L0s <2us, L1 <2us
                        ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x2, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR-, OBFF Not Supported
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
                         EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
        Capabilities: [100 v1] Device Serial Number 80-c1-6e-ff-fe-24-05-4c
        Capabilities: [110 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UESvrt: DLP- SDES+ TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: bnx2
        Kernel modules: bnx2

```

(I'd also like to point out that at the time this was run, no VMs were running. The host "owned" the interface.)

---

### Post by KillerKelvUK on 2017-01-03
Okay, so bummer on the SR-IOV front...that would have been cool to play with and learn.  I had a bash at planning out the high levels of your networking, see how this looks.  I'll attached the file so you can edit (LibreOffice) if you want to discuss changes etc...

[IMG]https://s23.postimg.org/rglhrks8b/ads3_networking.jpg[/IMG]

---

### Post by ads3 on 2017-01-03
I would like to discuss some changes, yeah. Your solution looks brilliant, but I'm wanting to get rid of the consumer-grade router entirely. My Internet connection is actually a point-to-point interface, essentially - its all layer 2 back to my ISP's router. 
The first issue I see with your implementation is the possibility of exposing my host to the Internet. I only want one thing exposed to the net directly, and that's my router with built in firewall. I know that the bridge interfaces can have an IP placed on them, and that IP is a route to the host. That's something I'd want to avoid, for sure. The "outside" bridge would need to exist with no layer 3 information on it.
Also, I **do** have an almost working environment, which I depict in the 2nd slide in that file. It has a couple of issues that need hashing out, though. 

Ya know, I may just go and buy a used 4 port PCIe Intel NIC off Ebay. :P 

**Your Solution, Edited**
[IMG]https://s24.postimg.org/kik6h6nb9/bridge_Solution.png[/IMG]
[B]

Notes on my Current Environment[/B]
[IMG]https://s24.postimg.org/ydigznhqd/desired_Solution.png[/IMG]

---

### Post by KillerKelvUK on 2017-01-03
How hardened do you want the host, i.e. nothing stopping the host DHCPing NIC1 to get the WAN IP from your ISP but then overriding / manually setting the routing and DNS so that host routes its own traffic via the pfSense guest, just that pfSense wouldn't be in control of the DHCP process to your ISP.  Doing this would also stop you're host having WAN access if the pfSense guest died provided the DNS and routing was hardcoded..is that a big deal?

---

### Post by ads3 on 2017-01-03
I don't feel like it is, no. My end goal is basically just to simulate my host being "in my LAN," "behind my router," just as if it was another PC plugged into a consumer-grade home router's 4 port switch. If the router goes down, the host (and all vms) should loose Internet connectivity. 

Time to break out the "ip route" command, huh?

---

### Post by KillerKelvUK on 2017-01-03
LOL prolly.  I'm gunna have another look at the macvtap and passthrough interface model of libvirt, I've not really delved any further than bridges for my own purposes so I'm certainly no expert but this may have a better route forward (pun intended)...yeah I'll get my coat!

---

### Post by ads3 on 2017-01-03
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-attch-nic-physdev.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-attch-nic-physdev.html)
> This feature attaches a virtual function of a SRIOV capable NIC directly to a VM without losing the migration capability.
Augh! Gotta have SR-IOV. Well if my nics dont support SR-IOV, then why does doing this seem to work? Yeah, buying used Intel NICs is sounding even better now.

**Edit - **just realized something
I'm gonna try something in a few hours once I get physical access to my server again. Currently, /etc/network/interfaces on my host reads:
```
auto enp3s0f0
iface enp3s0f0 inet dhcp
```
If you'll recall, enp3s0f0 is what I want to be my "wan" interface. I'm going to replace this with
```
iface enp3s0f0 manual
``` and see what happens.

---

### Post by KillerKelvUK on 2017-01-03
Yeah naw I thought something was strange...your earlier posts you had an interface described as a macvtap and using passthrough and your details said it was IP functional just not route-able I think so I've recreated it myself.

Basically I had an unused ethernet device and port on my mobo that I disable via the UEFI so I went along and re-enabled it but didn't describe it in my hosts /etc/network/interface script.  However sure enough the 2nd ethernet device and port was visible in 'lspci' and 'ip link show' but nothing in 'ifconfig' which makes sense as I hadn't set it up.  However virt-manager could see the device and so allowed me to map it into an ubuntu-server guest I have as a 2nd interface.  Waddya know, I can bring up that 2nd interface in my guest, tell it to do a dhcp request and sure enough it broadcasts out that interface, hits my lil Asus DSL router which is my DHCP server and gets an address.  The bit you'll like however is that the host doesn't see a jot, see my host ifconfig below...

So br0 for my vm's, this bridge has physical port enp0s25 mapped in and enp3s0 is my previously unused ethernet port that is now passed-thru to my guest...it has an IP of 192.168.1.202 which only the guest reports!  Sounds like what you want right?!

EDIT:  forgot I can ssh to said guest on that IP from other devices on my LAN :D


```

br0       Link encap:Ethernet  HWaddr d0:50:99:43:28:76  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:12167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8259205 (8.2 MB)  TX bytes:1895122 (1.8 MB)


enp0s25   Link encap:Ethernet  HWaddr d0:50:99:43:28:76  
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:147908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213312587 (213.3 MB)  TX bytes:6394916 (6.3 MB)
          Interrupt:20 Memory:efe00000-efe20000 


enp3s0    Link encap:Ethernet  HWaddr 52:54:00:49:98:8c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240042 (240.0 KB)  TX bytes:2664 (2.6 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:131690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:3880171937 (3.8 GB)  TX bytes:3880171937 (3.8 GB)


macvtap0  Link encap:Ethernet  HWaddr 52:54:00:49:98:8c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4674 (4.6 KB)  TX bytes:2664 (2.6 KB)


vnet0     Link encap:Ethernet  HWaddr fe:54:00:33:ea:d4  
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:3720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1873766 (1.8 MB)  TX bytes:1146004 (1.1 MB)


vnet1     Link encap:Ethernet  HWaddr fe:54:00:ed:61:25  
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19433 (19.4 KB)  TX bytes:118080 (118.0 KB)


vnet2     Link encap:Ethernet  HWaddr fe:54:00:1c:c7:e8  
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:71606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4832919 (4.8 MB)  TX bytes:205738769 (205.7 MB)

```

---

### Post by ads3 on 2017-01-03
Yes!! Yes!! That sounds **exactly **like what I want!! Oh, I'm excited now. I don't wanna wait the 7 hours I gotta wait to get to my own box!
Watch forgetting to edit /etc/network/interfaces be the source of my problems.

Now here's a question. When you run "lspci -vvv -s" is IO-SRV listed under your NIC's capabilities? I don't understand why macvtap passthrough still works on my end when I don't have IO-SRV support. I'm not complaining, for sure! I just don't see why it works. XD

---

### Post by KillerKelvUK on 2017-01-03
See that's the odd thing...no my NIC doesn't support SR-IOV.  There are only a couple of reasonable doc sources I've found and both say macvtap with passthrough requires the virtual functions of an SR-IOV capable NIC, I've spent a little time trying to find other ways to technically validate if the nic is SR-IOV but all the references say it should clearly list it as a capability via lspci which as you can see below it aint!

So I thought about other ways to test this i.e. where is the CPU load being applied during a file copy when I use the bridged interface vs. the macvtap interface.  So using the bridge interface copying a 3Gb file with PV takes about 22seconds and on my host it looks like all cores take a small hit even tho the guest is limited to 2 vcpus.  However when I use the macvtap interface to copy a 3Gb file it takes 30 seconds and my host only shows a spike on 2 cpu's to a much bigger degree than the previous test.  So from this I'm taking it that the macvtap is correctly placing the load on the guest as its...passed through!

Considering firing the SR-IOV question into a mailing list unless I can find an answer elsewhere.

```

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
    Subsystem: ASRock Incorporation Motherboard (one of many)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: I/O ports at d000 [size=256]
    Region 2: Memory at efd00000 (64-bit, non-prefetchable) [size=4K]
    Region 4: Memory at e2100000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00478  Data: 0000
    Capabilities: [70] Express (v2) Endpoint, MSI 01
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 4096 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s unlimited, L1 <64us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+, LTR+, OBFF Via message/WAKE#
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR+, OBFF Disabled
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
        Vector table: BAR=4 offset=00000000
        PBA: BAR=4 offset=00000800
    Capabilities: [d0] Vital Product Data
        Unknown small resource type 00, will not decode more.
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170 v1] Latency Tolerance Reporting
        Max snoop latency: 71680ns
        Max no snoop latency: 71680ns
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by KillerKelvUK on 2017-01-03
Its also really odd as the documentation as well as virt-manager says "In most configurations, macvtap does not work for host to guest network communications", so not trying to jinx you but this may have been your problem but for me its working fine...ssh from host to guest, ssh from macbook via wifi to guest.  

*headscratch*

---

### Post by ads3 on 2017-01-03
The question then becomes, what interface is your ssh traffic flowing through? Once I'm able to implement things, I should have an interface in my LAN - interface br0, to be precise.

---

### Post by KillerKelvUK on 2017-01-03
Okay I reconfigured the guest to have only the macvtap nic and nothing altered i.e. host/guest separation still intact and comms from LAN devices to guest still worked.  Thinking about it IP communications should work so I wonder if the documentation is talking about socket based comms specifically between host and guest :-/  I mean to take this point on and answer your prev post about which interface is the ssh traffic flowing through...

macbook puts a ethernet frame on the medium (wifi) that the router receives.
router does a layer 3 look up of the target IP and confirms no further routing required
router drops down to layer 2 and uses arp cache to match MAC address to port and forwards the packet
host nic (whilst has to be the newly enabled nic due to the mac address passthrough) receipts the packet and processes it back up the stack to where-ever the macvtap drivers grabs it and routes it to the guest.
ergo ssh was using the correct interface for newly created macvtap nic...this sound about right?

---

### Post by KillerKelvUK on 2017-01-03
So I think I may understand this better now and its likely documentation hasn't been maintained very well.  If you read here ([http://www.linux-kvm.org/page/10G_NIC_performance:_VFIO_vs_virtio](http://www.linux-kvm.org/page/10G_NIC_performance:_VFIO_vs_virtio)) there is a clear distinction between VFIO networking and Virtio.  VFIO networking requires the nic to support SR-IOV but virtio doesn't use the same tech.

It helped by having a look at the qemu command libvirt was using for the guest...

```

-netdev tap,fd=28,id=hostnet0,vhost=on,vhostfd=32 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:77:f7:58,bus=pci.0,addr=0x3

```

---

### Post by ads3 on 2017-01-03
I see you have the same virtio-net-pci they mention on the link you provided. I checked /var/log/libvirt/qemu/pfSens.log and found that my system automatically selected to use virtio-balloon-pci instead of virtio-net-pci. I found this article ([https://rwmj.wordpress.com/2010/07/17/virtio-balloon/](https://rwmj.wordpress.com/2010/07/17/virtio-balloon/)) on ballooning, and I've seen my aforementioned M$-user-friend's HyperV hypervisor use ballooning on virtual machines in his environment. But I've only seen it apply to main memory - RAM. Have you seen how it applies to NICs or PCI devices in general?

---

### Post by KillerKelvUK on 2017-01-03
Nah, thats just the qemu device parameter to create the guest balloon device that's needed to dynamically alter RAM, does yours look something like...

```

-device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8

```

Maybe better to check a running guest by looking at the process, I always check mine with "ps aux | grep qemu".

---

### Post by KillerKelvUK on 2017-01-03
Been meaning to ask...why pfSense?  Studious hours of research comparing, recommended by those in the know or just the first you've found?

Whilst BSD is close to linux and I like learning it is an overhead having to keep proficient in both if this is the only requirement.  I'd be interested to know if you've discounted others and why?

OpenWRT
VyOS
OPNsense
...lots of others

---

### Post by ads3 on 2017-01-03
Studious minutes of research comparing. :) 
Basically, from what I've seen, pfSense seems to combine ease of use with lots of "power." I know its used in Enterprise-grade environments, and its very well documented - I've even found YouTube tutorials demonstrating some configuration. On top of that, having a web GUI is always nice... my first choice was actually to use Ubuntu Server as a router/firewall, but all management would have been through the cli, which sounds painful for day-to-day stuff. "Oh, my raspberry pi needs port 443 for 5 minutes? Okay! iptables... uh... what comes next?" 
It was also recommended to me by a coworker, so I may be slightly biased towards using it based on word of mouth. ;)

---

### Post by KillerKelvUK on 2017-01-03
> Studious minutes of research comparing. 

LOL

Have you seen/used Webmin before?  Just in case you want to take another look at using Ubuntu Server as the router/firewall, it offers a web based GUI for lots of server packages that you add into Ubuntu server and I think networking and firewalling are amongst those supported

Anyways let us know how you get on with that macvtap-passthru config and where you get to with the whole setup, I'm keen to let you trail-blaze for me hahahaa

---

### Post by ads3 on 2017-01-03
**Issue Resolved.**
Allright, the issue I came here to report has been resolved. Thank you so much for your help, it is absolutely appreciated. :) 

For the sake of documentation, I'll recap what all happened. I was trying to pass a NIC through to a VM - pci passthrough - even though that NIC was not the only device in its PCI group. We found that even though my CPU supports virtualization, my NIC did not. We found a software workaround, though, using virtio. 
According to the libvirt wiki ([https://wiki.libvirt.org/page/Virtio](https://wiki.libvirt.org/page/Virtio)), virtio is similar to the drivers provided by some hypervisors, like vmWare, Hyper-V... 
> Virtio is a virtualization standard for network and disk device drivers  where just the guest's device driver "knows" it is running in a virtual  environment, and cooperates with the hypervisor

To obtain a better understanding of how I resolved this, since I have multiple NICs, let's discuss my /etc/network/interfaces file:
```
# the loopback network interface
auto lo
iface lo inet loopback

# NIC 1, int 1. LAN inside, bridged
iface enp3s0f0 inet manual

# NIC1, int 2. WAN outside, passed through to pfSense
hotplug enp3s0f1
# 'hotplug' keyword prevents 5 minute hang during bootup - "A start job is running for raise network interfaces"
# might be a better way.

# lan bridge interface - host gets internet access through here.
auto br0
iface br0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.1
    dns-search my.cool.domain.name.com
    dns-nameservers 10.0.0.1 8.8.8.8 8.8.4.4
    hwaddress ether 80:c1:6e:24:05:4c    # matches the mac address of enp3s0f0
    bridge_ports enp3s0f0
    bridge_stp off    # I don't feel like spanning tree is necessary, YMMV.
    bridge_fd 0
```
A few things to note. Neither of my physical NICs have any IP assignment. Not even DHCP. The host does not use these NICs, the virtualized environment does. Only br0 has any IP assignment. With the network established, let's look at my router VM, which needs interface enp3s0f0 passed through to it.

I enabled passthrough on my pfSense's WAN interface by modifying my libvirt config like so:
```

    <interface type='direct'>
      <mac address='52:54:00:e3:6c:9c' />
      <source dev='enp3s0f1' mode='passthrough' />
      <model type='virtio' />
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0' />
    </interface>

```
This configuration **resolved **my original issue. Notice that I'm using virtio, and that I've specified device enp3s0f1 to be passed through to the VM. I've confirmed that this VM has Internet access, and that my host has access through interface br0. Other VMs with NICs bridged with br0 also have Internet access through the pfSense router. 


Although not related to my issue, I'll also share the pfSense config for my bridge interface in hopes that someone finds it useful. 
```
    <interface type='bridge'>
      <mac address='52:54:00:49:84:52' />
      <source bridge='br0' />
      <model type='virtio' />
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0' />
    </interface>
```
Next comes a GPU and some more PCI passthrough. :) I'm pretty excited. Thank you so much for your help!

---

### Post by KillerKelvUK on 2017-01-04
Great news and good job!

---

