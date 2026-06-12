---
title: "Ubuntu 16.04 KVM physical USB devices not passing to guest"
date: 2016-04-29
forum: Virtualisation
---

### Post by carter3 on 2016-04-29
Hello! I've recently got GPU passthrough working on my machine, the only problem being the physical usb devices don't want to move from the host to the Windows 10 guest. Pretty silly problem if you ask me, seeing as how the GPU passthrough should've been the hard part... :P. Specs probably aren't important at this point, but for the sake of being thorough here they are. I am using Qemu 2.5.0, all the latest everything (fresh install of the latest version of Ubuntu)

Specs:
Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz (does have VT-d and everything, I did get VGA working after all)
Host GPU: NVidia GTX 560
Guest GPU: GTX 760
MOBO: Gygabite H77

Here's my devices and XML file:
```

:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1532:011b Razer USA, Ltd 
Bus 001 Device 006: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 005: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Bus 001 Device 003: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:0a4d Logitech, Inc. G430 Surround Sound Gaming Headset
Bus 003 Device 004: ID 1532:0037 Razer USA, Ltd 
Bus 003 Device 003: ID 046d:c21e Logitech, Inc. F510 Gamepad [XInput Mode]
Bus 003 Device 002: ID 03f0:2c24 Hewlett-Packard Logitech M-UAL-96 Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
<domain type='kvm'>
  <name>Windows-10</name>
  <uuid>48f2d114-f560-41ba-ba9e-1d2e0a7c20ab</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>3</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/Windows-10_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <kvm>
      <hidden state='on'/>
    </kvm>
  </features>
  <cpu mode='custom' match='exact'>
    <model fallback='allow'>IvyBridge</model>
  </cpu>
  <clock offset='localtime'>
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
      <driver name='qemu' type='raw'/>
      <source file='/home/carter/windows-10.img'/>
      <target dev='vda' bus='virtio'/>
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
    <interface type='network'>
      <mac address='52:54:00:50:cc:06'/>
      <source network='default'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x07' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x07' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='no'>
      <source>
        <vendor id='0x03f0'/>
        <product id='0x2c24'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x1532'/>
        <product id='0x011b'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc21e'/>
      </source>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </memballoon>
  </devices>
</domain> 
```

I've tried all my USB devices at various ports, USB 2.0 and USB 3.0 and they all stay on the host, completely usable but on the wrong system. There have been no errors while attempting to connect them (I usually just use virt-manager unless I absolutely have to use XML). I've googled around and no one seems to have any problem like this, very confusing. This leads me to believe it's a very simple problem, On one hand I hope it is so that it's an easy fix, but on the other I hope it isn't so I don't feel silly for missing it haha. Anyone have any ideas?

Edit: I should also mention that I've tried this with other vm's as well with other operating systems, all of which have the same problem.

---

### Post by MAFoElffen on 2016-05-01
From what I seen in your xml file looks good (see below):
```

  <devices>
     ...
    [COLOR=#ff0000]<!-- Start virtual usb controller -->[/COLOR]
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
    [COLOR=#ff0000]<!-- End virtual usb controller -->
[/COLOR]    [COLOR=#ff0000]<!-- Start Host USB Controller -->[/COLOR]
    <hostdev mode='subsystem' type='usb' managed='no'>
      <source>
        [COLOR=#FF0000]<!-- [/COLOR][COLOR=#ff0000]ID 03f0:2c24 Hewlett-Packard Logitech M-UAL-96 Mouse[/COLOR][COLOR=#FF0000], format of ID is VendorID:ProductID, hostbus=3, hostaadr=2 -->[/COLOR]
        <vendor id='0x03f0'/>
        <product id='0x2c24'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        [COLOR=#FF0000]<!--[/COLOR][COLOR=#ff0000] ID 1532:0037 Razer USA, Ltd, f[/COLOR][COLOR=#FF0000]ormat of ID is VendorID:ProductID, hostbus=1, hostaddr=4 -->[/COLOR]
        <vendor id='0x1532'/>
        <product id='0x011b'/>
      </source>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        [COLOR=#ff0000]<!-- ID 046d:c21e Logitech, Inc. F510 Gamepad [XInput Mode], format of ID is VendorID:ProductID, hostbus=3, hostaddr=3  -->[/COLOR]
        <vendor id='0x046d'/>
        <product id='0xc21e'/>
      </source>
    </hostdev>
    [COLOR=#ff0000]<!-- End host usb Controller -->[/COLOR]
    ...
  </devices>

```
I looked at one of mine, and I have the tag as
```

    <hostdev mode='subsystem' type='usb'>
      ...
    </hostdev>

```
I don't use the [COLOR=#ff0000]managed="yes"[/COLOR] attribute in the hostdev tag. Maybe try it without that?

---

### Post by jairuncaloth2 on 2016-05-01
Hi guys, I'm experiencing the same issue.
I tried removing managed='yes' from the XML but this just results in it being set to managed='no' automatically once I save it.

I wonder if this is a permissions issue. I'm seeing the following in dmesg when I start the VM but I can't say for sure if it's related.

```

[48885.356447] audit: type=1400 audit(1462129859.203:166): apparmor="DENIED" operation="open" profile="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" name="/run/udev/data/c189:1" pid=4301 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[48885.356490] audit: type=1400 audit(1462129859.203:167): apparmor="DENIED" operation="open" profile="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" name="/run/udev/data/c189:129" pid=4301 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[48885.356527] audit: type=1400 audit(1462129859.203:168): apparmor="DENIED" operation="open" profile="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" name="/run/udev/data/c189:257" pid=4301 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[48885.356562] audit: type=1400 audit(1462129859.203:169): apparmor="DENIED" operation="open" profile="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" name="/run/udev/data/c189:258" pid=4301 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[48885.356595] audit: type=1400 audit(1462129859.203:170): apparmor="DENIED" operation="open" profile="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" name="/run/udev/data/c189:259" pid=4301 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[48915.695077] audit: type=1400 audit(1462129889.543:193): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-d41a2364-a38a-46c3-b37a-ff1b07f9ec00" pid=4317 comm="apparmor_parser"

```

---

### Post by gavi2 on 2016-05-01
I am having the very same issue on a brand new installation of Ubuntu 16.04.0
The GPU pass-through works very well with SkyLake, Windows 10 and NVIDIA.
 All the updates for Win 10 went well.
virtIO NIC and virtIO disk work well and the guest is very stable without any crash.

I expected passing USB devices to Win10 to be the easier part.

I tried several types of devices and none work.

on a USB key (which has been disconnected from host), for example, I am getting:

```
[36537.582588] audit: type=1400 audit(1462133017.910:170): apparmor="STATUS" operation="profile_load" profile="unconfined" name="<name>" pid=11915 comm="apparmor_parser"
[36537.582701] audit: type=1400 audit(1462133017.910:171): apparmor="STATUS" operation="profile_load" profile="unconfined" name="<name>//qemu_bridge_helper" pid=11915 comm="apparmor_parser"
[36537.667024] device vnet0 entered promiscuous mode
[36537.691027] br2: port 2(vnet0) entered listening state
[36537.691061] br2: port 2(vnet0) entered listening state
[36537.860238] audit: type=1400 audit(1462133018.190:172): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="<name>" pid=11969 comm="apparmor_parser"
[36537.882908] audit: type=1400 audit(1462133018.214:173): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="<name>//qemu_bridge_helper" pid=11969 comm="apparmor_parser"
[36538.414965] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x1e@0x258
[36538.414973] vfio_ecap_init: 0000:01:00.0 hiding ecap 0x19@0x900
[36538.432527] audit: type=1400 audit(1462133018.762:174): apparmor="DENIED" operation="open" profile="<name>" name="/run/udev/data/c189:1" pid=11995 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=121 ouid=0
[36538.432564] audit: type=1400 audit(1462133018.762:175): apparmor="DENIED" operation="open" profile="<name>" name="/run/udev/data/c189:2" pid=11995 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=121 ouid=0
[36538.432598] audit: type=1400 audit(1462133018.762:176): apparmor="DENIED" operation="open" profile="<name>" name="/run/udev/data/c189:129" pid=11995 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=121 ouid=0
[36538.432632] audit: type=1400 audit(1462133018.762:177): apparmor="DENIED" operation="open" profile="<name>" name="/run/udev/data/c189:3" pid=11995 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=121 ouid=0
[36538.432666] audit: type=1400 audit(1462133018.762:178): apparmor="DENIED" operation="open" profile="<name>" name="/run/udev/data/c189:0" pid=11995 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=121 ouid=0

```


  virt-manager creates this command:
```
qemu-system-x86_64 -enable-kvm -name win10pt -S -machine pc-i440fx-wily,accel=kvm,usb=off -cpu Broadwell,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win7pt_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -mem-prealloc -mem-path /dev/hugepages/libvirt/qemu -realtime mlock=off -smp 4,maxcpus=8,sockets=1,cores=4,threads=2 -uuid <name> -nographic -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-win10pt/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot menu=off,strict=on -device nec-usb-xhci,id=usb,bus=pci.0,addr=0x2 -drive file=/media/usr/LinuxStorage/VMs/Images/win7pt.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x7,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -netdev tap,fd=27,id=hostnet0,vhost=on,vhostfd=29 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=<mymac>,bus=pci.0,addr=0x3 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x9 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0xa -device usb-host,hostbus=2,hostaddr=2,id=hostdev2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x8 -msg timestamp=on
```

and in particular it tells qemu to use the USB in:
```
-device usb-host,hostbus=2,hostaddr=2
```

lsusb :
```
Bus 002 Device 002: ID 125f:312a A-DATA Technology Co., Ltd. Superior S102
```

so the virt-manager setting was passed on well:
```
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x125f'/>
        <product id='0x312a'/>
      </source>
    </hostdev>
```

One thing that, to me, looks strange in the command line is:
```
-machine pc-i440fx-wily,accel=kvm,usb=off
```
the ```
,usb=off
``` is it implicated?

Or what could be the problem?

---

### Post by jairuncaloth2 on 2016-05-01
Ah, this appears to be covered in the Ubuntu wiki 
[https://help.ubuntu.com/community/KVM/Managing#Adding_USB_Device_Pass-through](https://help.ubuntu.com/community/KVM/Managing#Adding_USB_Device_Pass-through)
I will test and report back

My /etc/apparmor.d/abstractions/libvirt-qemu already contains this:

```

176   # for usb access
177   /dev/bus/usb/ r,
178   /etc/udev/udev.conf r,
179   /sys/bus/ r,
180   /sys/class/ r,

```

Tried adding this, but no luck
```

/sys/devices/*/*/usb[0-9]*/** r,
/dev/bus/usb/*/[0-9]* rw,

```

---

### Post by gavi2 on 2016-05-01
> **jairuncaloth2 said:**
> Ah, this appears to be covered in the Ubuntu wiki 
[https://help.ubuntu.com/community/KVM/Managing#Adding_USB_Device_Pass-through](https://help.ubuntu.com/community/KVM/Managing#Adding_USB_Device_Pass-through)


I am new to qemu kvm. I am reading from the linked page and I am very surprised:
**Adding USB Device Pass-through** 
**Limitations**
 > USB protocol 1.1 only

All the devices I need to pass are USB3.0 or USB2.0

I read in another forum that maybe it has to do with my 
```
-i440fx
```
parameter? Should we use ```
-M q35
``` instead? But I read also that Q35 can make Windows update crash, so maybe it is not appropriete for a Windows guest?

---

### Post by KillerKelvUK on 2016-05-02
Hey, Q35 chipset with Windows is fine, been running this for a long time now and yes I use 2.0 and 3.0 so all is good there.  Have in the last week flattened my 15.10 install and completed a clean install of 16.04 although I habitually remove apparmor (well I disable the service starting)...looking through this thread its plagued my apparmor 'DENIED'.  I know there are plenty of good reasons to keep aa in place however I've never been able to get the profiles into a place where its not bitchin about storage locations or complaining about USB devices so after loosing hours & days at the problem I just got rid of it.

---

### Post by gavi2 on 2016-05-02
> **KillerKelvUK said:**
> Hey, Q35 chipset with Windows is fine, been running this for a long time now and yes I use 2.0 and 3.0 so all is good there.  Have in the last week flattened my 15.10 install and completed a clean install of 16.04 although I habitually remove apparmor (well I disable the service starting)...looking through this thread its plagued my apparmor 'DENIED'.  I know there are plenty of good reasons to keep aa in place however I've never been able to get the profiles into a place where its not bitchin about storage locations or complaining about USB devices so after loosing hours & days at the problem I just got rid of it.

Thank you ! you solved the issue, for me at least.
I am glad to hear that there should be no issues passing USB2 and USB3.

I changed the machine type to Q35. Windows10 seems to still work perfectly with NVIDIA passthrough, as you kindly suggested.

I disabled apparmor to try to get the USB working in guest.
```
sudo /etc/init.d/apparmor stop
```

After the command above, I would still get the apparmor DENIED messages.
So I also did:
```
[COLOR=#c20cb9]**sudo**[/COLOR] update-rc.d [COLOR=#660033]-f[/COLOR] apparmor remove
```

Still dmesg would show apparmor DENIED messages when running the VM.

After a reboot,
I then tried once more to pass a USB 3.0 device, a simple 15GB USB key (device ejected from the host immediately after plugging it in the USB).

Virt-Manager generates this:
```
qemu-system-x86_64 -enable-kvm -name win10ptQ35 -S -machine pc-q35-2.5,accel=kvm,usb=off -cpu Broadwell,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/win10ptQ35_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -mem-prealloc -mem-path /dev/hugepages/libvirt/qemu -realtime mlock=off -smp 4,maxcpus=8,sockets=1,cores=4,threads=2 -uuid <myuid> -nographic -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-win10ptQ35/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global ICH9-LPC.disable_s3=1 -global ICH9-LPC.disable_s4=1 -boot strict=on -device i82801b11-bridge,id=pci.1,bus=pcie.0,addr=0x1e -device pci-bridge,chassis_nr=2,id=pci.2,bus=pci.1,addr=0x1 -device nec-usb-xhci,id=usb,bus=pci.2,addr=0x2 -drive file=/media/usr/LinuxStorage/VMs/Images/win7pt.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.2,addr=0x3,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=<myMAC>,bus=pci.2,addr=0x1 -device usb-host,hostbus=2,hostaddr=2,id=hostdev0 -device vfio-pci,host=01:00.0,id=hostdev1,bus=pci.2,addr=0x5 -device vfio-pci,host=01:00.1,id=hostdev2,bus=pci.2,addr=0x6 -device virtio-balloon-pci,id=balloon0,bus=pci.2,addr=0x4 -msg timestamp=on

```

Now the USB Key works! 

So thanks a LOT: indeed, the problem was apparmor.

---

### Post by KillerKelvUK on 2016-05-03
Glad this sorted it for you.

Please remember to mark the thread a solved, saves the admin's time to focus on the necessary tasks.

Thanks

---

