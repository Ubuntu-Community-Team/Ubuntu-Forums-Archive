---
title: "Error message using Raspberry PI with KVM"
date: 2022-10-20
forum: Virtualisation
---

### Post by softest2 on 2022-10-20
Hi,

I'm new to KVM and I'm not an expert on Ubuntu/Linux and my native language is not English but I hope what I write will make sense.

I try to run a VM using KVM on a Raspberry Pi 4 with 8 GB RAM and I have stored the files on a M2 drive mounted to /mnt/sda. I first tried [the following guide]("https://www.xmodulo.com/use-kvm-command-line-debian-ubuntu.html") but had to use another xml file so I largely copied from [this source]("https://gist.github.com/plembo/88a4e421020a73e73e3c0206fce2f174").

I have installed KVM and created an xml file (the content is displayed further down in this forum post). When I try to start the server using the command below I get the error message as shown below. I have tried editing the code and searched the Internet but with no luck. Can someone explain what I do wrong?

virsh create UBNT-SVR1.xml

error: Failed to create domain from UBNT-SVR1.
error: internal error: process exited while connecting
to monitor: 2022-10-20T08:52:34.713889Z qemu-system-a
arch64: The -accel and "-machine accel=" options are i
ncompatible

XML file:
```
<domain type='qemu' xmlns:qemu='http://libvirt.org/schemas/domain/qemu/1.0'>
  <name>UBNT-SVR1</name>
  <title>Ubuntu 22.04</title>
  <description>Ubuntu 22.04</description>
  <memory unit='KiB'>1048576</memory>
  <currentMemory unit='KiB'>1048576</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <resource>
    <partition>/machine</partition>
  </resource>
  <os>
    <type arch='aarch64' machine='virt-2.11'>hvm</type>
    <loader readonly='yes' secure='no' type='rom'>/usr/share/AAVMF/AAVMF_CODE.fd</loader>
    <boot dev='cdrom'/>
  </os>
  <features>
    <gic version='2'/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-aarch64</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2' cache='directsync'/>
      <source file='/mnt/sda/VM/UBNT-SVR1.qcow2'/>
      <backingStore/>
      <target dev='vda' bus='virtio'/>
      <alias name='virtio-disk0'/>
      <address type='pci' domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
    </disk>

<disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <source file="/mnt/sda/ISO/ubuntu-22.04.1-preinstalled-server-arm64+raspi.img"/>
      <target dev="hdb" bus='scsi'/>
      <readonly/>
    </disk>

    <controller type='pci' index='0' model='pcie-root'>
      <alias name='pcie.0'/>
    </controller>
    <controller type='pci' index='1' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='1' port='0x8'/>
      <alias name='pci.1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x0' multifunction='on'/>
    </controller>
    <controller type='pci' index='2' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='2' port='0x9'/>
      <alias name='pci.2'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <controller type='pci' index='3' model='dmi-to-pci-bridge'>
      <model name='i82801b11-bridge'/>
      <alias name='pci.3'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </controller>
    <controller type='pci' index='4' model='pci-bridge'>
      <model name='pci-bridge'/>
      <target chassisNr='4'/>
      <alias name='pci.4'/>
      <address type='pci' domain='0x0000' bus='0x03' slot='0x00' function='0x0'/>
    </controller>
    <controller type='pci' index='5' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='5' port='0xa'/>
      <alias name='pci.5'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='6' model='pcie-root-port'>
      <model name='pcie-root-port'/>
      <target chassis='6' port='0xb'/>
      <alias name='pci.6'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x3'/>
    </controller>
    <controller type='usb' index='0' model='qemu-xhci'>
      <alias name='usb'/>
      <address type='pci' domain='0x0000' bus='0x05' slot='0x00' function='0x0'/>
    </controller>
    <interface type='bridge'>
      <mac address='de:ad:be:ef:b0:0b'/>
      <source bridge='virbr0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x06' slot='0x00' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/1'/>
      <target type='system-serial' port='0'>
        <model name='pl011'/>
      </target>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/1'>
      <source path='/dev/pts/1'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <input type='tablet' bus='usb'>
      <alias name='input0'/>
      <address type='usb' bus='0' port='1'/>
    </input>
    <input type='keyboard' bus='usb'>
      <alias name='input1'/>
      <address type='usb' bus='0' port='2'/>
    </input>
    <graphics type='vnc' port='-1' autoport="yes" listen='0.0.0.0'/>
    <video>
      <model type='virtio' vram='131072' heads='1' primary='yes'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x02' slot='0x00' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
  <qemu:commandline>
    <qemu:arg value='-cpu'/>
    <qemu:arg value='host'/>
    <qemu:arg value='-enable-kvm'/>
  </qemu:commandline>
</domain>

```

---

### Post by DuckHook on 2022-10-20
Welcome to the forums, softest2

I'm sorry that my help can be only very limited. While I do use KVM, my experience is confined to Intel/AMD hosts. I have no experience with RPi hosts.

**My first observation** is that you are using the wrong guides/sources. The guide you link to provides general instructions for a i386/amd64 host/guest. But you are trying to install and configure an ARM guest on an ARM host. The same is true of your config file. It comes from a site that assumes a i386/amd64 host/guest.

Try the following guide instead: [https://linuxhint.com/kvm_virtualization_raspberry_pi4/](https://linuxhint.com/kvm_virtualization_raspberry_pi4/)

This guide was written specifically for ARM hosts. Skip down to the part where the author provides instructions for installing Ubuntu server for ARM. This should give you an ARM guest.

Note the following:

If you are running on a RPi host, you can only run an ARM guest. You won't be able to run an i386/amd64 image on a RPi. ARM architecture cannot virtualize CISC HW (yet).

**My second observation** is more general. Although it is amazing that it can be done at all, trying to virtualize a VM guest on a RPi host is asking an awful lot from a very underpowered CPU/GPU. The RPi is basically a toy and virtualization is a demanding, resource&#8209;intensive application. It's like strapping a jet engine on a biplane and asking the resulting hybrid to break the sound barrier. Unless you are just playing around or experimenting, do you really want to rely on such a fragile and undependable platform?

You may wish to try a less demanding technology like containers. Docker or LXD can now give you many of the features that used to be available only in VMs, but at a small fraction of the resources. Such containers might hold up better on an ARM device like RPi.

Note that all of the above advice is based on internet searches. It bears repeating that I do not use VMs in my RPis so I have no personal experience to rely on. Please proceed at your own risk.

---

### Post by MAFoElffen on 2022-10-21
I do KVM on amd64 and arm64. I do KVM on Raspberry Pi4 (8GB). I don't consider a Pi4 as being a "toy". Heck, my smartphone is more powerful than servers I have ran...

I working Ubuntu 22.04 Server Arm64 Guest
```

<domain type="kvm">
  <name>ubuntu22.04</name>
  <uuid>d5c3cb31-4705-496b-8684-a84a7ff1e7b5</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://ubuntu.com/ubuntu/22.04"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit="KiB">4194304</memory>
  <currentMemory unit="KiB">4194304</currentMemory>
  <vcpu placement="static">1</vcpu>
  <os>
    <type arch="aarch64" machine="virt-6.2">hvm</type>
    <loader readonly="yes" type="pflash">/usr/share/AAVMF/AAVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/ubuntu22.04_VARS.fd</nvram>
  </os>
  <features>
    <acpi/>
    <gic version="2"/>
  </features>
  <cpu mode="host-passthrough" check="none"/>
  <clock offset="utc"/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-aarch64</emulator>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2" discard="unmap"/>
      <source file="/home/Public/KVM/images/ubuntu22.04.qcow2"/>
      <target dev="vda" bus="virtio"/>
      <boot order="1"/>
      <address type="pci" domain="0x0000" bus="0x05" slot="0x00" function="0x0"/>
    </disk>
    <disk type="file" device="cdrom">
      <driver name="qemu" type="raw"/>
      <source file="/home/Public/KVM/ISO/ubuntu-22.04.1-live-server-arm64.iso"/>
      <target dev="sda" bus="scsi"/>
      <readonly/>
      <boot order="2"/>
      <address type="drive" controller="0" bus="0" target="0" unit="0"/>
    </disk>
    <controller type="usb" index="0" model="qemu-xhci" ports="15">
      <address type="pci" domain="0x0000" bus="0x02" slot="0x00" function="0x0"/>
    </controller>
    <controller type="scsi" index="0" model="virtio-scsi">
      <address type="pci" domain="0x0000" bus="0x03" slot="0x00" function="0x0"/>
    </controller>
    <controller type="pci" index="0" model="pcie-root"/>
    <controller type="pci" index="1" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="1" port="0x8"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="2" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="2" port="0x9"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x1"/>
    </controller>
    <controller type="pci" index="3" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="3" port="0xa"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x2"/>
    </controller>
    <controller type="pci" index="4" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="4" port="0xb"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x3"/>
    </controller>
    <controller type="pci" index="5" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="5" port="0xc"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x4"/>
    </controller>
    <controller type="pci" index="6" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="6" port="0xd"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x5"/>
    </controller>
    <controller type="pci" index="7" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="7" port="0xe"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x6"/>
    </controller>
    <controller type="pci" index="8" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="8" port="0xf"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x01" function="0x7"/>
    </controller>
    <controller type="pci" index="9" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="9" port="0x10"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x0" multifunction="on"/>
    </controller>
    <controller type="pci" index="10" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="10" port="0x11"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x1"/>
    </controller>
    <controller type="pci" index="11" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="11" port="0x12"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x2"/>
    </controller>
    <controller type="pci" index="12" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="12" port="0x13"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x3"/>
    </controller>
    <controller type="pci" index="13" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="13" port="0x14"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x4"/>
    </controller>
    <controller type="pci" index="14" model="pcie-root-port">
      <model name="pcie-root-port"/>
      <target chassis="14" port="0x15"/>
      <address type="pci" domain="0x0000" bus="0x00" slot="0x02" function="0x5"/>
    </controller>
    <controller type="virtio-serial" index="0">
      <address type="pci" domain="0x0000" bus="0x04" slot="0x00" function="0x0"/>
    </controller>
    <interface type="network">
      <mac address="52:54:00:c9:34:48"/>
      <source network="default"/>
      <model type="virtio"/>
      <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
    </interface>
    <serial type="pty">
      <target type="system-serial" port="0">
        <model name="pl011"/>
      </target>
    </serial>
    <console type="pty">
      <target type="serial" port="0"/>
    </console>
    <channel type="unix">
      <target type="virtio" name="org.qemu.guest_agent.0"/>
      <address type="virtio-serial" controller="0" bus="0" port="1"/>
    </channel>
    <input type="keyboard" bus="usb">
      <address type="usb" bus="0" port="1"/>
    </input>
    <tpm model="tpm-tis">
      <backend type="emulator" version="2.0"/>
    </tpm>
    <graphics type="spice" autoport="yes">
      <listen type="address"/>
      <image compression="off"/>
      <gl enable="no"/>
    </graphics>
    <audio id="1" type="none"/>
    <video>
      <model type="virtio" heads="1" primary="yes"/>
      <address type="pci" domain="0x0000" bus="0x08" slot="0x00" function="0x0"/>
    </video>
    <memballoon model="virtio">
      <address type="pci" domain="0x0000" bus="0x06" slot="0x00" function="0x0"/>
    </memballoon>
    <rng model="virtio">
      <backend model="random">/dev/urandom</backend>
      <address type="pci" domain="0x0000" bus="0x07" slot="0x00" function="0x0"/>
    </rng>
  </devices>
</domain>

```
Note that there are two tricks for AARM64 guests... Arm cannot do VGA, so I add in other ways... And for non-serial input, you have to add a keyboard...

---

### Post by softest2 on 2022-10-21
Thanks both of you for good advice. I will try it and get back with the result after I try it :P

I only plan to use the Rpi for experimenting. I have an actual server for my "real" VM:s running Xenserver but I don't want to experiment with it. I am however impressed with the performance from the Rpi 4 this far.

/Softest2

---

### Post by DuckHook on 2022-10-21
Yes, perhaps I'm not doing the RPi justice calling it a toy. I was trying to highlight its shortcomings for the sake of caution and I was overzealous.

I have four RPi 4s dedicated to various tasks around the house, so they are clearly useful for many things:

[LIST=1]
[*]One acts as a KODI box running LibreElec.
[*]Another has Ubuntu Server installed and is used for non&#8209;critical tasks like file uploading/downloading and torrenting.
[*]Two others run Xubuntu desktop and act as emergency fallback machines in case my main desktop machines die.
[/LIST]
But, as cheap and versatile as they are, they remain brittle, fragile things with structural limitations:

[LIST=1]
[*]USB storage is fickle and unreliable,
[*]SD Card foundation is also fickle and unreliable,
[*]On-board WIFI/BT is weak. It is impossible to enhance either without separate dongles or experienced soldering skills,
[*]The combined CPU/GPU runs up against its limits when put to computationally intensive tasks.
[*]It is inadvisable to use it for server tasks like ZFS or LVM striping/mirroring (from bad firsthand personal experience).
[/LIST]
But since you are using it for experimentation and tinkering, all is good. If you understand its limitations, you won't be using it for mission critical stuff.

---

