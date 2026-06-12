---
title: "I can't access Apache from Host"
date: 2015-02-06
forum: Virtualisation
---

### Post by peter1897 on 2015-02-06
I have Ubuntu server installed on virtualbox and i installed apache and i am trying to connect to apache server from my host which is Windows 7 but i always get connection timed out message.

This is the output from ifconfig:

```
root@ubuntu:/etc/network# ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:41:f6:9b
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe41:f69b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72837 (72.8 KB)  TX bytes:57992 (57.9 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1274 (1.2 KB)  TX bytes:1274 (1.2 KB)
```

When i enter 10.0.2.15 in the browser it show that the connection is timed out. My Network settings on the virtual machine are for NAT and i acrivated a second adapter for host-only network.

This is the ip configuration from my host machine:

```
C:\Program Files\Oracle\VirtualBox>ipconfig

Windows IP Configuration


Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::983d:f052:5d0e:24c9%12
   IPv4 Address. . . . . . . . . . . : 192.168.31.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.31.1

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter VirtualBox Host-Only Network:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::f921:96ef:cb4b:84e%16
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :

Tunnel adapter isatap.{2E9CECF1-0D1B-437E-B42F-8C5BEAA2C455}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.{10BC156E-311E-426D-A6E7-5F480BB42227}:

   Media State . . . . . . . . . . . : Media disconnected
```

This is the information for the virtual machine:

```
C:\Program Files\Oracle\VirtualBox>vboxmanage showvminfo Ubuntu
Name:            Ubuntu
Groups:          /
Guest OS:        Ubuntu (32 bit)
UUID:            a547e5f8-cc93-45a8-86f1-a3b7e780a631
Config file:     E:\VM\Ubuntu\Ubuntu.vbox
Snapshot folder: E:\VM\Ubuntu\Snapshots
Log folder:      E:\VM\Ubuntu\Logs
Hardware UUID:   a547e5f8-cc93-45a8-86f1-a3b7e780a631
Memory size:     512MB
Page Fusion:     off
VRAM size:       12MB
CPU exec cap:    100%
HPET:            off
Chipset:         piix3
Firmware:        BIOS
Number of CPUs:  1
PAE:             on
Long Mode:       off
Synthetic CPU:   off
CPUID overrides: None
Boot menu mode:  message and menu
Boot Device (1): Floppy
Boot Device (2): DVD
Boot Device (3): HardDisk
Boot Device (4): Not Assigned
ACPI:            on
IOAPIC:          off
Time offset:     0ms
RTC:             UTC
Hardw. virt.ext: on
Nested Paging:   on
Large Pages:     off
VT-x VPID:       on
VT-x unr. exec.: on
State:           running (since 2015-02-06T20:58:29.631000000)
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
Default Frontend:
Storage Controller Name (0):            IDE
Storage Controller Type (0):            PIIX4
Storage Controller Instance Number (0): 0
Storage Controller Max Port Count (0):  2
Storage Controller Port Count (0):      2
Storage Controller Bootable (0):        on
Storage Controller Name (1):            SATA
Storage Controller Type (1):            IntelAhci
Storage Controller Instance Number (1): 0
Storage Controller Max Port Count (1):  30
Storage Controller Port Count (1):      1
Storage Controller Bootable (1):        on
IDE (1, 0): C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso (UUID: 2a06092f-8761-46ad-aef0-7c78670bc6c0)
SATA (0, 0): E:\VM\Ubuntu\Ubuntu.vdi (UUID: 6abd5543-f8c7-4bf3-af43-37a6edc4d03e)
NIC 1:           MAC: 08002741F69B, Attachment: NAT, Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: allow-vms, Bandwidth group: none
NIC 1 Settings:  MTU: 0, Socket (send: 64, receive: 64), TCP Window (send:64, receive: 64)
NIC 1 Rule(0):   name = ssh, protocol = tcp, host ip = , host port = 3022, guest ip = , guest port = 22
NIC 2:           MAC: 08002779942E, Attachment: Host-only Interface 'VirtualBox Host-Only Ethernet Adapter', Cable connected: on, Trace: off (file: none), Type: 82540EM, Reported speed: 0 Mbps, Boot priority: 0, Promisc Policy: allow-vms, Bandwidth group: none
NIC 3:           disabled
NIC 4:           disabled
NIC 5:           disabled
NIC 6:           disabled
NIC 7:           disabled
NIC 8:           disabled
Pointing Device: USB Tablet
Keyboard Device: PS/2 Keyboard
UART 1:          disabled
UART 2:          disabled
LPT 1:           disabled
LPT 2:           disabled
Audio:           enabled (Driver: DSOUND, Controller: AC97)
Clipboard Mode:  Bidirectional
Drag'n'drop Mode: disabled
Session type:    GUI/Qt
Video mode:      640x480x0 at 0,0
VRDE:            disabled
USB:             enabled
EHCI:            enabled

USB Device Filters:

<none>

Available remote USB devices:

<none>

Currently Attached USB Devices:

<none>

Bandwidth groups:  <none>

Shared folders:

Name: 'Shared', Host path: 'D:\Shared' (machine mapping), writable

VRDE Connection:    not active
Clients so far:     0

Video capturing:    not active
Capture screens:    0
Capture file:       E:\VM\Ubuntu\Ubuntu.webm
Capture dimensions: 1024x768
Capture rate:       512 kbps
Capture FPS:        25

Guest:

Configured memory balloon size:      0 MB
OS type:                             Linux26
Additions run level:                 2
Additions version:                   4.3.20 r96996
```

And this is from netstat:

```
root@ubuntu:/etc/network# netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0    152 10.0.2.15:ssh           10.0.2.2:56092          ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  5      [ ]         DGRAM                    3395     /dev/log
unix  2      [ ]         DGRAM                    2613     @/org/kernel/udev/udevd
unix  3      [ ]         STREAM     CONNECTED     4118
unix  3      [ ]         STREAM     CONNECTED     4117
unix  2      [ ]         DGRAM                    4065
unix  2      [ ]         DGRAM                    3456
unix  2      [ ]         DGRAM                    3406
unix  3      [ ]         DGRAM                    2650
unix  3      [ ]         DGRAM                    2649
unix  3      [ ]         STREAM     CONNECTED     2597     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     2596

```

I hope someone can help me make this work.

---

### Post by TheFu on 2015-02-06
The easiest solution is to use bridged networking, not NAT for the guest network. If you must use NAT, then you'll need to forward the port manually.  [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html) explains the different options.

---

### Post by peter1897 on 2015-02-07
I tried bridged networking but it didn't work. I think i have to be physically connected to a network for the bridged networking to work and i am connected wirelessly to my router.

---

### Post by TheFu on 2015-02-07
Your VM doesn't know anything about the physical adapter used.
Back when I used virtualbox, it was possible to connect VMs through the wifi adpater of the hostOS. Just make certain the wifi adapter is selected and connected on the network tab in the VM settings.

Page 31 of this list [http://blog.jdpfu.com/ALE/ALE-NW/Ubuntu-12.04-x32-install.pdf](http://blog.jdpfu.com/ALE/ALE-NW/Ubuntu-12.04-x32-install.pdf) shows the "bridged" and "name" settings. The name should be for your physical wireless adapter in the machine. Not the "enabled" checkbox at the top and the "cable connected" checkbox at the bottom.  Also - for the VM, either use virtio drivers or the Intel PRO/1000. The VM doesn't know anything about the real NIC.

For other virtualbox peformance tuning .... [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)  Note that ICH is faster than piix3 chipsets. I'd change that ASAP.

---

### Post by peter1897 on 2015-02-07
I found what was the problem. I had to add a second network interface on ubuntu server because it has only one. Now i can connect to apache from host and ubuntu can connect to internet.

---

### Post by TheFu on 2015-02-07
> **peter1897 said:**
> I found what was the problem. I had to add a second network interface on ubuntu server because it has only one. Now i can connect to apache from host and ubuntu can connect to internet.

Glad you found a workaround, but I'm positive the 2nd card is NOT necessary, at least for normal networking. In fact, bridges can be shared by at least 10 VMs, perhaps more regardless of the host networking; wifi/wired doesn't matter.

---

