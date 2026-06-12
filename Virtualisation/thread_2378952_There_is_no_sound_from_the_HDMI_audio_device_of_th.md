---
title: "There is no sound from the HDMI audio device of the RADEON RX-480 in the GPU passthro"
date: 2017-11-29
forum: Virtualisation
---

### Post by masato-d on 2017-11-29
I have built a GPU passthrough environment with ubuntu 17.10, but when assigning more than 8 GB of memory to the virtual machine, the sound does not sound from the HDMI audio device of AMD RADEON RX-480.
If the amount of memory allocated to the virtual machine is 4GB or less, a sound is heard.
If you replace the OVMF package with Ubuntu 16.04 and add a USB controller to the passthrough device, even if 4GB or more memory is allocated, the HDMI audio device normally sounds.
Even in OVMF of Ubuntu 16.04, if you do not passthrough the USB controller, the HDMI audio device does not sound unless the memory to allocate is 4GB or less.
On Windows 10, although the HDMI audio device is in a normal operation state, no sound is heard.

```
lspci
----------------------------
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] (rev c7)
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aaf0
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 Ethernet controller: Broadcom Limited NetLink BCM57781 Gigabit Ethernet PCIe (rev 10)
06:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
07:00.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
08:01.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
08:02.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
08:03.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
0a:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
0b:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
0c:00.0 Multimedia controller: ViXS Systems, Inc. XCode II Series
0c:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
----------------------------
-----------------------------
ii  ipxe-qemu                                      1.0.0+git-20161027.b991c67+really20150424.a25a16d-1ubuntu2 all          PXE boot firmware - ROM images for qemu
ii  qemu-block-extra:amd64                         1:2.10+dfsg-0ubuntu3                                       amd64        extra block backend modules for qemu-system and qemu-utils
ii  qemu-kvm                                       1:2.10+dfsg-0ubuntu3                                       amd64        QEMU Full virtualization
ii  qemu-system-common                             1:2.10+dfsg-0ubuntu3                                       amd64        QEMU full system emulation binaries (common files)
ii  qemu-system-x86                                1:2.10+dfsg-0ubuntu3                                       amd64        QEMU full system emulation binaries (x86)
ii  qemu-utils                                     1:2.10+dfsg-0ubuntu3                                       amd64        QEMU utilities
ii  gir1.2-libvirt-glib-1.0:amd64                  1.0.0-1                                                    amd64        GObject introspection files for the libvirt-glib library
ii  libgovirt-common                               0.3.4-2                                                    all          GObject-based library to access oVirt REST API (common files)
ii  libgovirt2:amd64                               0.3.4-2                                                    amd64        GObject-based library to access oVirt REST API
ii  libvirt-bin                                    3.6.0-1ubuntu6                                             amd64        programs for the libvirt library
ii  libvirt-clients                                3.6.0-1ubuntu6                                             amd64        Programs for the libvirt library
ii  libvirt-daemon                                 3.6.0-1ubuntu6                                             amd64        Virtualization daemon
ii  libvirt-daemon-system                          3.6.0-1ubuntu6                                             amd64        Libvirt daemon configuration files
ii  libvirt-glib-1.0-0:amd64                       1.0.0-1                                                    amd64        libvirt GLib and GObject mapping library
ii  libvirt0:amd64                                 3.6.0-1ubuntu6                                             amd64        library for interfacing with different virtualization systems
ii  open-vm-tools                                  2:10.1.10-3                                                amd64        Open VMware Tools for virtual machines hosted on VMware (CLI)
ii  ovmf                                           0~20170911.5dfba97c-1ubuntu0.1                             all          UEFI firmware for 64-bit x86 virtual machines
ii  python-libvirt                                 3.5.0-1build1                                              amd64        libvirt Python bindings
ii  ubuntu-virt-server                             1.4                                                        all          Common packages necessary for hosting virtual machines
ii  virt-manager                                   1:1.4.0-5ubuntu2                                           all          desktop application for managing virtual machines
ii  virt-viewer                                    6.0-1                                                      amd64        Displaying the graphical console of a virtual machine
ii  virtinst                                       1:1.4.0-5ubuntu2                                           all          Programs to create and clone virtual machines
-----------------------------
&#20206;&#24819;&#12510;&#12471;&#12531;&#35373;&#23450;
-----------------------------
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh edit KVMPC02
or other application using the libvirt API.
-->
<domain type='kvm' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>KVMPC02</name>
  <uuid>cd981219-ec93-43f2-8a5a-0135e420d33d</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-2.10'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE_1604.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/KVMPC02_VARS.fd</nvram>
    <bootmenu enable='yes'/>
    <smbios mode='host'/>
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
      <vendor_id state='on' value='123456789abc'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='custom' match='exact' check='partial'>
    <model fallback='allow'>IvyBridge</model>
    <topology sockets='1' cores='4' threads='1'/>
    <feature policy='disable' name='vmx'/>
    <feature policy='disable' name='fma'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
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
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native' discard='unmap'/>
      <source dev='/dev/mapper/vg_yoshi_kvm02-lv_kvmpc02'/>
      <target dev='sda' bus='scsi'/>
      <boot order='1'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hda' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <controller type='scsi' index='0' model='virtio-scsi'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </controller>
    <controller type='usb' index='0' model='ich9-ehci1'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x7'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci1'>
      <master startport='0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0' multifunction='on'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci2'>
      <master startport='2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x1'/>
    </controller>
    <controller type='usb' index='0' model='ich9-uhci3'>
      <master startport='4'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x2'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:26:67:e5'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <channel type='spicevmc'>
      <target type='virtio' name='com.redhat.spice.0'/>
      <address type='virtio-serial' controller='0' bus='0' port='1'/>
    </channel>
    <input type='tablet' bus='usb'>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <listen type='address'/>
      <image compression='off'/>
    </graphics>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1' primary='yes'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
      </source>
      <rom bar='on'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x02' slot='0x00' function='0x1'/>
      </source>
      <rom bar='off'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x00' slot='0x14' function='0x0'/>
      </source>
      <rom bar='off'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x00' slot='0x1d' function='0x0'/>
      </source>
      <rom bar='off'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:env name='QEMU_PA_SAMPLES' value='1024'/>
    <qemu:env name='QEMU_AUDIO_DRV' value='pa'/>
    <qemu:env name='QEMU_PA_SERVER' value='/run/user/1000/pulse/native'/>
  </qemu:commandline>
</domain>
-----------------------------
```

---

