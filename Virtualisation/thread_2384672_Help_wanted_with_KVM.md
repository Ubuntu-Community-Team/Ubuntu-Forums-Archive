---
title: "Help wanted with KVM"
date: 2018-02-10
forum: Virtualisation
---

### Post by vasa1 on 2018-02-10
I got QEMU/KVM going but I fear I haven't set things up optimally. Starting the guest system, Xubuntu 16.04, takes (subjectively) longer with KVM than starting Kubuntu 18.04 with VBox. Once the KVM's up and running things are fine (and RAM usage, FWIW, appears lower).

My host is Kubuntu 16.04.

inxi -Fxz reports:```
System:    Host: aes-Inspiron-15-3567 Kernel: 4.13.0-32-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: KDE Plasma 5.8.8 (Qt 5.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Inspiron 15-3567
           Mobo: Dell model: 0FGN4M v: A00 Bios: Dell v: 01.07.00 date: 04/07/2017
CPU:       Dual core Intel Core i3-6006U (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7968
           clock speeds: max: 2000 MHz 1: 2000 MHz 2: 2000 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2)
           GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 01:00.0
           IF: wlp1s0 state: up mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 001-006
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1500.3GB (10.1% used) ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
           ID-2: USB /dev/sdb model: External_USB_3.0 size: 500.1GB
Partition: ID-1: / size: 443G used: 134G (32%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 8.31GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 192 Uptime: 39 min Memory: 2866.6/7846.9MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```


I don't know of a succinct way to report the status of my KVM. If there's a convenient CLI route to do so, I can provide the information.

For now, here's the *inxi* output from the guest:```
vasa1@xubu-kvm:~$ inxi -Fxz
System:    Host: xubu-kvm Kernel: 4.13.0-32-generic x86_64 (64 bit gcc: 5.4.0) Desktop: Xfce 4.12.3 (Gtk 2.24.28)
           Distro: Ubuntu 16.04 xenial
Machine:   System: QEMU product: Standard PC (i440FX + PIIX 1996) v: pc-i440fx-xenial
           Mobo: N/A model: N/A Bios: Sea v: Ubuntu-1.8.2-1ubuntu1 date: 04/01/2014
CPU:       Single core Intel Core (Broadwell no TSX) (-UP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3) bmips: 3984 speed: 1992 MHz (max)
Graphics:  Card: Red Hat QXL paravirtual graphic card bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1280x720@59.97hz
           GLX Renderer: llvmpipe (LLVM 5.0, 256 bits) GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:04.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
Network:   Card: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139cp v: 1.3 port: c000 bus-ID: 00:03.0
           IF: ens3 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 42.9GB (18.8% used) ID-1: /dev/sda model: QEMU_HARDDISK size: 42.9GB
Partition: ID-1: / size: 36G used: 4.2G (13%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.76GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 129 Uptime: 35 min Memory: 300.4/3441.2MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 
vasa1@xubu-kvm:~$

```

Could it be because I allowed the default storage to be in **/var** (*/var/lib/libvirt/images/generic.qcow2*) rather in my home folder?

---

### Post by TheFu on 2018-02-10
Wrong network driver - use virtio.  Why limit the throughput to 100Mbps?  

Use virtio for storage too.

On spinning disks, always pre-allocate the entire disk amount desired. Using sparse allocations will be slow, unless on SSD storage.

Use SPICE and QXL for video, if there is a desktop. If there isn't a desktop, use cirrus and ssh into the system.  ssh is native speed. 

I've had better luck using Intel motherboard emulation.

768p screen resolution - ouch.

```
virsh dumpxml {vmname}
```

KVM is mainly designed for server VMs.  If you want desktop-on-desktop, there aren't many good choices especially when using an iGPU.  Intel is working on native GPU passthru, but that code isn't ready for general use.  [https://01.org/igvt-g](https://01.org/igvt-g) has more details.  A key item is this: > GVT-g only supports remote display not local display by this release.  Hummm. I need to try this, since I only run my desktop VM from a remote LAN system.

---

### Post by vasa1 on 2018-02-10
Here's my xml output:```
$ virsh dumpxml generic
<domain type='kvm' id='2'>
  <name>generic</name>
  <uuid>82bec98f-5f3f-4def-8e16-082315b12d99</uuid>
  <memory unit='KiB'>3670016</memory>
  <currentMemory unit='KiB'>3670016</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>Broadwell-noTSX</model>
  </cpu>
  <clock offset='utc'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/generic.qcow2'/>
      <backingStore/>
      <target dev='hda' bus='ide'/>
      <shareable/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <backingStore/>
      <target dev='hdb' bus='ide'/>
      <readonly/>
      <alias name='ide0-0-1'/>
      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    </disk>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <alias name='usb'/>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <alias name='usb'/>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <alias name='usb'/>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <controller type='ide' index='0'>
      <alias name='ide'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <alias name='virtio-serial0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'>
      <alias name='pci.0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:aa:dd:55'/>
      <source network='default' bridge='virbr0'/>
      <target dev='vnet0'/>
      <model type='rtl8139'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/2'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/2'>
      <source path='/dev/pts/2'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0' state='connected'/>
      <alias name='channel0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' port='5900' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <alias name='sound0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir0'/>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
      <alias name='redir1'/>
    </redirdev>
    <memballoon model='virtio'>
      <stats period='5'/>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor' relabel='yes'>
    <label>libvirt-82bec98f-5f3f-4def-8e16-082315b12d99</label>
    <imagelabel>libvirt-82bec98f-5f3f-4def-8e16-082315b12d99</imagelabel>
  </seclabel>
</domain>
$ 
```

---

### Post by TheFu on 2018-02-10
Looks like you didn't change anything, as suggested.

---

### Post by vasa1 on 2018-02-10
No, I haven't changed anything from after reading your post. I still have to figure out when/how to change things.

I don't mind editing xml files. I've done it a lot with Openbox config files, menu.xml and rc.xml.

Just to be clear, the xml dump was taken from the host without any guest running.

---

### Post by TheFu on 2018-02-10
The suggested changes can be made through virt-manager (a GUI).  
Or
you can change them via **virsh edit {vmname}**.  But I would use virt-manager.
The storage parts (virtio + preallocating storage) should provide about 30% performance improvement.  
The virtio network will provide a 900% improvement for all networking.

Changing from sparse to pre-allocated storage is done through qemu-img, but I'd do all the other things first and give it a week. QCOW2 has a bunch of nice features which are very handy.

---

### Post by vasa1 on 2018-02-10
Maybe I should mention what I did so far.

After checking with
*egrep -c '(vmx|svm)' /proc/cpuinfo* which returned "2"
and
*kvm-ok* which returned "INFO: /dev/kvm exists" and "KVM acceleration can be used"

In the host machine, I installed
*qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils* and whatever dependencies were mentioned
*virt-manager* and whatever dependencies were mentioned

In both the host and guest, I installed *spice-vdagent*. I'm guessing only installing in the guest is needed.

I made some changes from what I could understand in the "Add Hardware" area. The output of the newest *virsh dumpxml generic* is here: [http://paste.ubuntu.com/=4VHKpMDdKF/](http://paste.ubuntu.com/=4VHKpMDdKF/)

---

### Post by TheFu on 2018-02-10
We all start out doing the same things you've done. It takes time to learn.  There are many, many, many, youtube videos about running KVM and tuning performance.  [http://blog.jdpfu.com/2012/07/30/improving-kvm-performance](http://blog.jdpfu.com/2012/07/30/improving-kvm-performance) is my simple guide.

Using ubuntu-vm-builder is non-trivial.  I've never gotten it working in an acceptable way. The Ubuntu How-To for KVM is doing it the hard way.  IMHO, it is for old-school setups from 2010-ish, before virt-manager was good.

I'm seeing 2 IDE devices and 1 virtio.  If it is storage for the VM and not Windows, then it needs to be virtio.  IDE will suck performance in a special way.   /var/lib/libvirt/images/generic.qcow2 - is still connected as IDE (slow).

Added 2 more NICs with virtio, but didn't remove the slow one? All should be virtio, assuming you don't just keep 1, connected to the bridge that you manually create using brctl.  Again, with Windows, you'll need to use the Intel PRO/1000 driver until you get virtio drivers installed into the guest.

Putting VM storage in your HOME isn't a great idea for a number of reasons.  The KVM solution is meant for servers, things you want started at boot, regardless of whether any user is logged in or not.

Does libvirtd have access to the files, always, when it is in your HOME?  If you use HOME directory encryption and have the VM set to start at boot up, it will fail. There are other reasons.  KVM doesn't run under your userid. It runs with kvm/libvirtd system accounts. Best not to place files owned by those into your HOME.  Type-1 hypervisors should be managed differently from type-2 ones.

---

### Post by vasa1 on 2018-02-10
> **TheFu said:**
> ...
I'm seeing 2 IDE devices and 1 virtio.  If it is storage for the VM and not Windows, then it needs to be virtio.  IDE will suck performance in a special way.   /var/lib/libvirt/images/generic.qcow2 - is still connected as IDE (slow).

Added 2 more NICs with virtio, but didn't remove the slow one? All should be virtio, assuming you don't just keep 1, connected to the bridge that you manually create using brctl.  Again, with Windows, you'll need to use the Intel PRO/1000 driver until you get virtio drivers installed into the guest.

I hope I got at least one more right this time! [http://paste.ubuntu.com/=QqCQgXcF7v/](http://paste.ubuntu.com/=QqCQgXcF7v/)

No Windows usage for me, now or in the future ...

> **TheFu said:**
> Putting VM storage in your HOME isn't a great idea for a number of reasons.  The KVM solution is meant for servers, things you want started at boot, regardless of whether any user is logged in or not.

Does libvirtd have access to the files, always, when it is in your HOME?  If you use HOME directory encryption and have the VM set to start at boot up, it will fail. There are other reasons.  KVM doesn't run under your userid. It runs with kvm/libvirtd system accounts. Best not to place files owned by those into your HOME.  Type-1 hypervisors should be managed differently from type-2 ones.

Re. VM storage at HOME, I don't use encryption and don't need to have the VM running at boot up. On the other hand, I don't have any immediate reason to have VM storage @ home.

---

### Post by TheFu on 2018-02-11
```
      <source file='/home/vasa1/kvm-pool/xubu16'/>
      <source file='/var/lib/libvirt/images/generic.qcow2'/>
      <source file='/var/lib/libvirt/images/generic-1.qcow2'/>
```

What's up with those?  Do you want 3 separate disks connected?

Still have 3 NICs too.

```
      <mac address='52:54:00:aa:dd:55'/>
      <mac address='52:54:00:df:be:f5'/>
      <mac address='52:54:00:c8:c5:c3'/>

``` All connected to the same "default" network/bridge/whatever.  I can't tell.

virt-manager will let you delete those things, pretty easily.

There are times when having multiple disks is handy, but I usually prefer to use partition. inside a single disk for most things. The only exception is Windows data stuff for media center recordings ... or where I've run out of inodes on a web server because it has 500K tiny ruby or perl files in /var/www/. ;)

For the multiple NIC stuff, there are lots and lots of reasons for those, but usually each would be connected to a specific physical NIC using VT-d passthru.  That's the only way to run a router, IMHO, assuming you can't have a physical device (which I prefer 10,000x more).

---

### Post by vasa1 on 2018-02-11
Well, I kept making what I thought were the changes I should until I got "no bootable device" :)

So I started afresh and will not rush things this time.

---

### Post by vasa1 on 2018-02-12
Things are much better now. I'm not sure what I've managed to implement from your suggestions. I think part of the problem was that, unlike VBox, there aren't pretty visuals accompanying the start up!

Here's my latest xml dump and a screenshot of my desktop.
```
     1	<domain type='kvm'>
     2	  <name>generic</name>
     3	  <uuid>1287a0af-4647-49fa-b0ff-820d7af1c620</uuid>
     4	  <memory unit='KiB'>4194304</memory>
     5	  <currentMemory unit='KiB'>4194304</currentMemory>
     6	  <vcpu placement='static'>1</vcpu>
     7	  <os>
     8	    <type arch='x86_64' machine='pc-i440fx-xenial'>hvm</type>
     9	    <boot dev='hd'/>
    10	  </os>
    11	  <features>
    12	    <acpi/>
    13	    <apic/>
    14	  </features>
    15	  <cpu mode='custom' match='exact'>
    16	    <model fallback='allow'>Broadwell-noTSX</model>
    17	  </cpu>
    18	  <clock offset='utc'>
    19	    <timer name='rtc' tickpolicy='catchup'/>
    20	    <timer name='pit' tickpolicy='delay'/>
    21	    <timer name='hpet' present='no'/>
    22	  </clock>
    23	  <on_poweroff>destroy</on_poweroff>
    24	  <on_reboot>restart</on_reboot>
    25	  <on_crash>restart</on_crash>
    26	  <pm>
    27	    <suspend-to-mem enabled='no'/>
    28	    <suspend-to-disk enabled='no'/>
    29	  </pm>
    30	  <devices>
    31	    <emulator>/usr/bin/kvm-spice</emulator>
    32	    <disk type='file' device='disk'>
    33	      <driver name='qemu' type='qcow2'/>
    34	      <source file='/var/lib/libvirt/images/generic.qcow2'/>
    35	      <target dev='vda' bus='virtio'/>
    36	      <shareable/>
    37	      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    38	    </disk>
    39	    <disk type='file' device='cdrom'>
    40	      <driver name='qemu' type='raw'/>
    41	      <target dev='hdb' bus='ide'/>
    42	      <readonly/>
    43	      <shareable/>
    44	      <address type='drive' controller='0' bus='0' target='0' unit='1'/>
    45	    </disk>
    46	    <controller type='usb' index='0' model='ich9-ehci1'>
    47	      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    48	    </controller>
    49	    <controller type='usb' index='0' model='ich9-uhci1'>
    50	      <master startport='0'/>
    51	      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    52	    </controller>
    53	    <controller type='usb' index='0' model='ich9-uhci2'>
    54	      <master startport='2'/>
    55	      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    56	    </controller>
    57	    <controller type='usb' index='0' model='ich9-uhci3'>
    58	      <master startport='4'/>
    59	      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    60	    </controller>
    61	    <controller type='pci' index='0' model='pci-root'/>
    62	    <controller type='ide' index='0'>
    63	      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    64	    </controller>
    65	    <controller type='virtio-serial' index='0'>
    66	      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    67	    </controller>
    68	    <interface type='network'>
    69	      <mac address='52:54:00:e8:86:f6'/>
    70	      <source network='default'/>
    71	      <model type='rtl8139'/>
    72	      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    73	    </interface>
    74	    <serial type='pty'>
    75	      <target port='0'/>
    76	    </serial>
    77	    <console type='pty'>
    78	      <target type='serial' port='0'/>
    79	    </console>
    80	    <channel type='spicevmc'>
    81	      <target type='virtio' name='com.redhat.spice.0'/>
    82	      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    83	    </channel>
    84	    <input type='mouse' bus='ps2'/>
    85	    <input type='keyboard' bus='ps2'/>
    86	    <graphics type='spice' autoport='yes'>
    87	      <image compression='off'/>
    88	    </graphics>
    89	    <sound model='ich6'>
    90	      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    91	    </sound>
    92	    <video>
    93	      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
    94	      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    95	    </video>
    96	    <redirdev bus='usb' type='spicevmc'>
    97	    </redirdev>
    98	    <redirdev bus='usb' type='spicevmc'>
    99	    </redirdev>
   100	    <memballoon model='virtio'>
   101	      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
   102	    </memballoon>
   103	  </devices>
   104	</domain>
```

---

### Post by TheFu on 2018-02-12
The network isn't virtio. It is using a simulated 10/100 NIC. Not good.
I don't understand the "pretty visuals" command. Sorry. Doesn't seem any different to me.

---

### Post by vasa1 on 2018-02-12
> **TheFu said:**
> The network isn't virtio. It is using a simulated 10/100 NIC. Not good.
I don't understand the "pretty visuals" command. Sorry. Doesn't seem any different to me.
Can you tell me specifically where to change the network?

---

### Post by TheFu on 2018-02-12
> **vasa1 said:**
> Can you tell me specifically where to change the network?

NIC --> Device model .... just like in virtualbox.

---

### Post by vasa1 on 2018-02-12
I tried a couple of times:

> Operation not supported: cannot modify network device model from rtl8139 to virtio

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/addhardware.py", line 801, in change_config_helper
    define_func(devobj=devobj, do_hotplug=True, **define_args)
  File "/usr/share/virt-manager/virtManager/domain.py", line 823, in define_network
    self.hotplug(device=editdev)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1081, in hotplug
    self._update_device(device)
  File "/usr/share/virt-manager/virtManager/domain.py", line 1034, in _update_device
    self._backend.updateDeviceFlags(xml, flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 2746, in updateDeviceFlags
    if ret == -1: raise libvirtError ('virDomainUpdateDeviceFlags() failed', dom=self)
libvirtError: Operation not supported: cannot modify network device model from rtl8139 to virtio

But finally, it seems to have gone through: [http://paste.ubuntu.com/=6QCPQC95bc/](http://paste.ubuntu.com/=6QCPQC95bc/). I hope!

---

### Post by TheFu on 2018-02-12
You cannot change settings when the machine is running.
I find it best to make the desired settings **BEFORE** installing the OS. If you do, there isn't anything hard, provided the OS handles virtio.  All mainstream Linux does, IME. If you can't get virtio, use Intel PRO/1000 (e1000) as the type.

I spent 5 hrs trying to fix a Win7 install yesterday that was using virtio for networking and disk. If I'd remembered the virtio, the fix would have been 10 minutes.  I had to change to SATA so the built-in Windows tools (boot DVD) could work to repair things, then switch back to virtio BEFORE booting the repaired install, since that is the storage controller being used inside the OS.  My last backup of the virtual disk was corrupted too.  Never figured out how that happened.  I'm guessing "bit rot", since that install has been in-use on the same physical disk for 5+ yrs.  The disk it runs on is 7.7 yrs old and not showing any issues at all. Zero problem sectors. Zero seek errors. Zero read errors. Zero CRC error counts. The only things with non-zero values on the disk are temperatures, spin-up, spin-down, and hours of use.   The point is that certain virtual machine configs are complicated in strange situations.

The other point is that whether it is virtualbox or virt-manager or Xen or Vmware-whatever, the defaults usually suck for performance.

---

### Post by TheFu on 2018-02-13
New post about GVT support coming to mainstream linux in a few months!  [https://www.phoronix.com/scan.php?page=news_item&px=Intel-GVT-Almost-Baked](https://www.phoronix.com/scan.php?page=news_item&px=Intel-GVT-Almost-Baked)  Very good news for VM users on Intel.

---

