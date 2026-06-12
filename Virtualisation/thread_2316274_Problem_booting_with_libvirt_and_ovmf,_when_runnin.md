---
title: "Problem booting with libvirt and ovmf, when running qemu directly works"
date: 2016-03-06
forum: Virtualisation
---

### Post by aserna3 on 2016-03-06
Hello,

I'm trying to do a PCI passthrough using OVMF and libvirt. The general problem is that if I use libvirt+virtmanager, if I create a UEFI VM, booting it just gives me a solid (not blinking) cursor on a black screen, and virt-manager shows CPU being maxed, so I'm assuming it hung. If I do the same thing with qemu directly, it works fine. I'm able to boot into my specified devices and work with it like any other VM.

The guest I'm trying to create

OS: Windows 10 x64
RAM: 8 GB
Storage: LVM partition
PCI device: nvidia 980 ti

My host is running Ubuntu 15.10 x64

Here are the following versions of my VM stack

```
libvirt-bin
Version: 1.2.16-2ubuntu11

virt-manager
Version: 1:1.3.2-0ubuntu1~ppa0


qemu-kvm
Version: 1:2.3+dfsg-5ubuntu9.2


```

OVMF I pulled from [https://www.kraxel.org/repos/jenkins/edk2/](https://www.kraxel.org/repos/jenkins/edk2/)

directories related to OVMF

```
anthony@Galactica:~$ ls -l /usr/share/edk2.git/ovmf-x64/total 15244
-rw-r--r-- 1 root root 1966080 Mar  4 14:14 OVMF_CODE-need-smm.fd
-rw-r--r-- 1 root root 1966080 Mar  4 14:04 OVMF_CODE-pure-efi.fd
-rw-r--r-- 1 root root 1966080 Mar  4 14:08 OVMF_CODE-with-csm.fd
-rw-r--r-- 1 root root 2097152 Mar  4 14:14 OVMF-need-smm.fd
-rw-r--r-- 1 root root 2097152 Mar  4 14:04 OVMF-pure-efi.fd
-rw-r--r-- 1 root root  131072 Mar  4 14:14 OVMF_VARS-need-smm.fd
-rw-r--r-- 1 root root  131072 Mar  6 14:03 OVMF_VARS-pure-efi.fd
-rw-r--r-- 1 root root  131072 Mar  4 14:08 OVMF_VARS-with-csm.fd
-rw-r--r-- 1 root root 2097152 Mar  4 14:08 OVMF-with-csm.fd
-rw-r--r-- 1 root root 3024896 Mar  4 14:14 UefiShell.iso



root@Galactica:~# ls -l /var/lib/libvirt/qemu/nvram/
total 128
-rw------- 1 root root 131072 Mar  6 15:00 win8.1_VARS.fd


```


libvirt XML config (It says win8.1, I was just lazy and didn't change it. It's running win10.

```
<domain type='kvm'>  <name>win8.1</name>
  <uuid>f8686458-2a8e-4f6e-9a68-608d7be35618</uuid>
  <memory unit='KiB'>1048576</memory>
  <currentMemory unit='KiB'>1048576</currentMemory>
  <memoryBacking>
    <hugepages/>
    <nosharepages/>
  </memoryBacking>
  <vcpu placement='static' current='1'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd</loader>
    <nvram template='/usr/share/edk2.git/ovmf-x64/OVMF_VARS-pure-efi.fd'>/var/lib/libvirt/qemu/nvram/win8.1_VARS.fd</nvram>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='off'/>
      <vapic state='off'/>
      <spinlocks state='off'/>
    </hyperv>
    <kvm>
      <hidden state='on'/>
    </kvm>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
    <topology sockets='1' cores='2' threads='2'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='no'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw' cache='none' io='native'/>
      <source dev='/dev/mapper/system-winroot'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </disk>
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
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='virtio-serial' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:43:27:2d'/>
      <source network='default'/>
      <model type='rtl8139'/>
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
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='spice' autoport='yes'>
      <image compression='off'/>
    </graphics>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='qxl' ram='65536' vram='65536' vgamem='16384' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x1532'/>
        <product id='0x0043'/>
      </source>
    </hostdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <redirdev bus='usb' type='spicevmc'>
    </redirdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```


And this is the working qemu command that works as expected

```
#!/bin/bash

cp /usr/share/edk2.git/ovmf-x64/OVMF_VARS-pure-efi.fd /tmp/my_vars.fd
qemu-system-x86_64 \
  -enable-kvm \
  -mem-path /dev/hugepages \
  -m 8192 \
  -cpu host,kvm=off \
  -vga none \
  -device vfio-pci,host=01:00.0,multifunction=on \
  -device vfio-pci,host=01:00.1 \
  -drive if=pflash,format=raw,readonly,file=/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd \
  -drive if=pflash,format=raw,file=/tmp/my_vars.fd \
  -device virtio-scsi-pci,id=scsi \
  -drive file=/dev/mapper/system-winroot,id=disk,format=raw,if=none -device scsi-hd,drive=disk \
  -usb -usbdevice host:2516:0004
```


Does anybody know why I can't get libvirt to work? I'd like to get that working so I can do things like trigger guest shutdowns / suspends when the host wants to shutdown.

---

### Post by KillerKelvUK on 2016-03-08
I'd say your problem is because you've created the libvirt managed guest with 2x GFX cards...one virtual i.e. the QXL one and then your passthrough card.  Your qemu commandline only has the passthrough as you've correctly used '-vga none' here.

---

