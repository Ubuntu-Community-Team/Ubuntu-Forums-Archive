---
title: "Slow network performance for single Windows VM with libvirt"
date: 2020-02-07
forum: Virtualisation
---

### Post by csdonat on 2020-02-07
Hi Everyone,

I've been struggling to figure out why my Windows 10 VM has slow network performance. The host box is a dedicated server with decent network connectivity (gigabit connection at a server farm). The host box has Ubuntu 18.04.4 LTS and runs one Windows VM only, on which I get 2MBit/sec max download speed. I've searched high and low for possible configuration options (different virtual network interfaces, different network setup), but nothing seems to improve the situation. I'd appreciate any ideas. Below my configuration files:

windows-vm.xml

```

<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>windows-vm</name>
  <uuid>d401c81e-67e4-4cc9-b5a8-a5d7f66d3cc8</uuid>
  <memory unit='KiB'>29360128</memory>
  <currentMemory unit='KiB'>29360128</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-2.11'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
    <hap state='on'/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='host-passthrough' check='none'>
    <topology sockets='1' cores='4' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='hypervclock' present='yes'/>
    <timer name='rtc' tickpolicy='catchup' track='guest'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native' discard='unmap'/>
      <source file='/dev/vg0/img-001'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <controller type='usb' index='0' model='piix3-uhci'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <interface type='bridge'>
      <mac address='52:54:00:0d:32:12'/>
      <source bridge='virbr0'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'>
      <listen type='address'/>
    </graphics>
    <video>
      <model type='vga' vram='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='none'/>
  </devices>
  <qemu:commandline>
    <qemu:env name='TZ' value='Europe/Berlin'/>
  </qemu:commandline>
</domain>

```

network.xml

```
<network>
  <name>default</name>
  <uuid>b891433a-625a-11e3-ac4d-270222b9750c</uuid>
  <forward mode='nat'>
    <nat>
      <port start='1024' end='65535'/>
    </nat>
  </forward>
  <bridge name='virbr0' stp='on' delay='0'/>
  <mac address='52:54:00:67:c7:1c'/>
  <domain name='...'/>
  <dns>
    <host ip='...'>
      <hostname>vm-host</hostname>
    </host>
  </dns>
  <ip address='192.168.0.1' netmask='255.255.255.0'>
    <dhcp>
      <host mac='52:54:00:0d:32:12' name='windows-vm...' ip='192.168.0.212'/>
    </dhcp>
  </ip>
</network>
```

---

### Post by TheFu on 2020-02-07
Back in 2010, the pre-generated bridges for QEMU/KVM always had performance issues.  I learned to always manually create a bridge outside the VM/libvirt control and point the VMs at it.  After changing to the manually created bridges, performance has been native speed. As proof:
```
$ iperf3 -s
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 172.22.22.13, port 37276
[  5] local 172.22.22.11 port 5201 connected to 172.22.22.13 port 37278
[ ID] Interval           Transfer     Bandwidth
[  5]   0.00-1.00   sec   101 MBytes   850 Mbits/sec                  
[  5]   1.00-2.00   sec   109 MBytes   912 Mbits/sec                  
[  5]   2.00-3.00   sec   110 MBytes   925 Mbits/sec                  
[  5]   3.00-4.00   sec   109 MBytes   916 Mbits/sec  
```
The "server" is a KVM VM using a bridge with an Intel i211 NIC. The hostOS is 16.04 and uses the old ifupdown methods to configure bridges. The client is a laptop going through a cheap USB3-to-GigE adaptor.  There are 2 cheap GigE switches between the client and server.  I have found that Realtek (r8169) and Marvell (skge) NICs don't work as well as Intel (e1000e or igb) . YMMV.

I have no idea how to accomplish that with **netplan** which is deployed on 18.04. Sorry.  I can google, however:
[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)
It seems complete and reasonable.

Also, you can install the virtio drivers from Redhat inside the Windows VM to gain access to virtio drivers for both storage and networking.  While these are a tiny bit better (for certain values of "better"), there are hassles if you ever need Windows _safe mode_ to recover from Windows boot problems.  You'll need to remember to manually add in the virtio drivers for the network or disks to work - or remember to change the VM settings back to SATA/SCSI and/or the PRO/1000 e1000 NIC driver.  I always forget.  Others might forget too.  I don't plan to ever install another Windows VM again, so this won't come up for me.  Only have 2 things left that need Windows still. Just replaced the 3rd win-only need with a Linux solution.

Linux VMs can use virtio for both storage and networking without any of the driver issues from a *Safe Boot* environment.

---

### Post by csdonat on 2020-02-12
Thanks, TheFu! It will take a bit of time to evaluate your proposal but I'll definitely try it. I'll get back here with the results.

---

