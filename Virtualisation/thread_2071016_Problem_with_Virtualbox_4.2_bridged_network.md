---
title: "Problem with Virtualbox 4.2 bridged network"
date: 2012-10-14
forum: Virtualisation
---

### Post by TJBJ on 2012-10-14
Hello,

I'm running ubuntu 12.04.1 server on i386 with static network config. I installed virtualbox form the vbox website and the extension pack. I created one vm and setup bridged network. I can ping from the guest to the host and from the host to the vm But the vm can not ping any other client in the network. Has anyone an idea?

VBoxManage list bridgedifs
```

Name:            eth0
GUID:            30687465-0000-4000-8000-00155dfb9a09
DHCP:            Disabled
IPAddress:       192.168.250.38
NetworkMask:     255.255.255.0
IPV6Address:     fe80:0000:0000:0000:0215:5dff:fefb:9a09
IPV6NetworkMaskPrefixLength: 64
HardwareAddress: 00:15:5d:fb:9a:09
MediumType:      Ethernet
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-eth0

```

VBoxManage showvminfo {d6878695-8010-4015-ba67-1c2b48606660}
```

Name:            TEST
Groups:          /
Guest OS:        OpenBSD
UUID:            d6878695-8010-4015-ba67-1c2b48606660
Config file:     /home/vmmanager/VirtualBox VMs/TEST/TEST.vbox
Snapshot folder: /home/vmmanager/VirtualBox VMs/TEST/Snapshots
Log folder:      /home/vmmanager/VirtualBox VMs/TEST/Logs
Hardware UUID:   d6878695-8010-4015-ba67-1c2b48606660
Memory size:     512MB
Page Fusion:     off
VRAM size:       4MB
CPU exec cap:    100%
HPET:            off
Chipset:         piix3
Firmware:        BIOS
Number of CPUs:  1
Synthetic Cpu:   off
CPUID overrides: None
Boot menu mode:  message and menu
Boot Device (1): Floppy
Boot Device (2): DVD
Boot Device (3): HardDisk
Boot Device (4): Not Assigned
ACPI:            on
IOAPIC:          off
PAE:             off
Time offset:     0ms
RTC:             local time
Hardw. virt.ext: off
Hardw. virt.ext exclusive: on
Nested Paging:   off
Large Pages:     off
VT-x VPID:       on
State:           running (since 2012-10-14T13:45:08.881000000)
Monitor count:   1
3D Acceleration: off
2D Video Acceleration: off
Teleporter Enabled: off
Teleporter Port: 0
Teleporter Address:
Teleporter Password:
Tracing Enabled: off
Allow Tracing to Access VM: off
Tracing Configuration:
Autostart Enabled: off
Autostart Delay: 0
Storage Controller Name (0):            IDE Controller
Storage Controller Type (0):            PIIX4
Storage Controller Instance Number (0): 0
Storage Controller Max Port Count (0):  2
Storage Controller Port Count (0):      2
Storage Controller Bootable (0):        on
IDE Controller (0, 0): /home/vmmanager/VirtualBox VMs/TEST/TEST.vhd (UUID: c414468f-8eaf-40c3-bea7-372b4146a5e7)
NIC 1:           MAC: 080027B1A8C0, Attachment: Bridged Interface 'eth0', Cable connected: on, Trace: off (file: none), Type: Am79C973, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: deny, Bandwidth group: none
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
Pointing Device: PS/2 Mouse
Keyboard Device: PS/2 Keyboard
UART 1:          disabled
UART 2:          disabled
LPT 1:           disabled
LPT 2:           disabled
Audio:           disabled
Clipboard Mode:  disabled
Drag'n'drop Mode:  disabled
Video mode:      720x400x0
VRDE:            enabled (Address 0.0.0.0, Ports 3389, MultiConn: off, ReuseSingleConn: off, Authentication type: null)
VRDE port:       3389
Video redirection: disabled
VRDE property: TCP/Ports  = "3389"
VRDE property: TCP/Address = <not set>
VRDE property: VideoChannel/Enabled = <not set>
VRDE property: VideoChannel/Quality = <not set>
VRDE property: VideoChannel/DownscaleProtection = <not set>
VRDE property: Client/DisableDisplay = <not set>
VRDE property: Client/DisableInput = <not set>
VRDE property: Client/DisableAudio = <not set>
VRDE property: Client/DisableUSB = <not set>
VRDE property: Client/DisableClipboard = <not set>
VRDE property: Client/DisableUpstreamAudio = <not set>
VRDE property: Client/DisableRDPDR = <not set>
VRDE property: H3DRedirect/Enabled = <not set>
VRDE property: Security/Method = <not set>
VRDE property: Security/ServerCertificate = <not set>
VRDE property: Security/ServerPrivateKey = <not set>
VRDE property: Security/CACertificate = <not set>
VRDE property: Audio/RateCorrectionMode = <not set>
USB:             disabled
EHCI:            enabled

USB Device Filters:

<none>

Available remote USB devices:

<none>

Currently Attached USB Devices:

<none>

Bandwidth groups:  <none>

Shared folders:  <none>

VRDE Connection:    active
Clients so far:     3
Start time:         2012/10/14 14:22:55 UTC
Sent:               560822 Bytes
Average speed:      -37172 B/s
Sent total:         2359167 Bytes
Received:           23930 Bytes
Speed:              -1586 B/s
Received total:     62010 Bytes
User name:
Domain:
Client name:        localhost
Client IP:          127.0.0.1
Client version:     2601
Encryption:         RDP4

Guest:

Configured memory balloon size:      0 MB
OS type:                             OpenBSD
Additions run level:                 0

Guest Facilities:

No active facilities.

```

sudo iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Thanks!

Alex

---

### Post by TJBJ on 2012-10-15
OK, found the Problem. On the Switch was only one MAC allowed. Bridged works fine now.

---

