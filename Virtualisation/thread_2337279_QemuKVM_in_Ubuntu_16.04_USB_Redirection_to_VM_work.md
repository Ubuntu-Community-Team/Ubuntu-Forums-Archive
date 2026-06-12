---
title: "Qemu/KVM in Ubuntu 16.04: USB Redirection to VM works sometimes"
date: 2016-09-16
forum: Virtualisation
---

### Post by daedra-86 on 2016-09-16
Hello everybody!
I had a problem of strange behavior forwarding USB wireless mouse +  keyboard (generally, any USB device) to the Windows 10 virtual machine  (forwarding VGA works fine using vfio-pci).
I will try to describe.
In the virtual machine settings (virt-manager) have already forwarding USB mouse + keyboard.
Launch VM, but the USB mouse + keyboard do not work.
When running the machine is removed from the configuration USB mouse + keyboard, and then re-connect - does not work.
Disconnected from the host USB mouse + keyboard, connect to a  different slot, then I am forwarding to the VM USB mouse + keyboard  works!
Help to make so that the USB mouse + keyboard are forwarding VM immediately when switched on.
Can here to throw any log files, settings, and command-line startup VM (some say).
P.S. Sorry for bad English. Such as those can not be found on the Internet.

My VM xml file:
```
<domain type='kvm'>
  <name>daedra-vm</name>
  <uuid>b233f286-c032-4aea-8e72-2d8f17b950aa</uuid>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-wily'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/daedra-vm_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <kvm>
      <hidden state='on'/>
    </kvm>
    <vmport state='off'/>
  </features>
  <cpu mode='host-model'>
    <model fallback='allow'/>
    <topology sockets='1' cores='4' threads='1'/>
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
      <source file='/home/daedra86/Vhd/daedra-vm.img'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </disk>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:df:bc:0e'/>
      <source network='default'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x046d'/>
        <product id='0xc52b'/>
      </source>
      <address type='usb' bus='0' port='1'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

lsusb output
```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 093a:2622 Pixart Imaging, Inc. Webcam Genius
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by KillerKelvUK on 2016-09-16
Hey daedra-86, welcome :-)

Please can you post the contents of the libvirt/qemu log file located at '/var/log/libvirt/qemu/daedra-vm'.  If you could please provide a clean log file which is newly created under the scenario you describe in your original post.

Also, are you aware of projects such as [http://symless.com/synergy/](http://symless.com/synergy/) which allow you to share your hosts keyboard and mouse seemlessly with your virtual machine's...I suggest it as a potential alternative to need to pass through the USB devices themselves.

---

### Post by daedra-86 on 2016-09-16
/var/log/libvirt/qemu/daedra-vm.log:
```
2016-09-16 21:33:26.863+0000: starting up libvirt version: 2.1.0, package: 1ubuntu3~ppa0 (Jacob Zimmermann <ppa@jzimm.net> Wed, 24 Aug 2016 08:34:10 +1000), qemu version: 2.6.1 (Debian 1:2.6.1+dfsg-0~16.04), hostname: daedra-pc
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name guest=daedra-vm,debug-threads=on -S -object secret,id=masterKey0,format=raw,file=/var/lib/libvirt/qemu/domain-16-daedra-vm/master-key.aes -machine pc-i440fx-wily,accel=kvm,usb=off,vmport=off -cpu Haswell,+vme,+ds,+acpi,+ss,+ht,+tm,+pbe,+dtes64,+monitor,+ds_cpl,+vmx,+smx,+est,+tm2,+xtpr,+pdcm,+osxsave,+f16c,+rdrand,+arat,+tsc_adjust,+xsaveopt,+pdpe1gb,+abm,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/daedra-vm_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -realtime mlock=off -smp 4,sockets=1,cores=4,threads=1 -uuid b233f286-c032-4aea-8e72-2d8f17b950aa -display none -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-16-daedra-vm/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -drive file=/home/daedra86/Vhd/daedra-vm.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x3,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -netdev tap,fd=27,id=hostnet0,vhost=on,vhostfd=29 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:df:bc:0e,bus=pci.0,addr=0x2 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x5 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x6 -device usb-host,hostbus=3,hostaddr=3,id=hostdev2,bus=usb.0,port=1 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 -msg timestamp=on
```

There are several problems with Synergy, keyboard layout, Scroll Lock and a heightened sensitivity with mouse in WoW. I need to server synergy was guest.

---

### Post by KillerKelvUK on 2016-09-17
Did you test this before upgrading qemu and libvirt using Jacob's PPA?

Any error messages anywhere else?

What happens when you try and start the guest without the keyboard & mouse actually connected to the host?

---

### Post by daedra-86 on 2016-09-18
I'm purged libvirt from Jacob's PPA and install from ubuntu rep (did not help):
```
2016-09-17 12:26:51.409+0000: starting up libvirt version: 1.3.1, package: 1ubuntu10.1 (dann frazier <dannf@ubuntu.com> Fri, 03 Jun 2016 14:41:21 -0600), qemu version: 2.6.1 (Debian 1:2.6.1+dfsg-0~16.04), hostname: daedra-pc
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name daedra-vm -S -machine pc-i440fx-wily,accel=kvm,usb=off,vmport=off -cpu Haswell,+abm,+pdpe1gb,+rdrand,+f16c,+osxsave,+pdcm,+xtpr,+tm2,+est,+smx,+vmx,+ds_cpl,+monitor,+dtes64,+pbe,+tm,+ht,+ss,+acpi,+ds,+vme,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/daedra-vm_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -realtime mlock=off -smp 4,sockets=1,cores=4,threads=1 -uuid b233f286-c032-4aea-8e72-2d8f17b950aa -nographic -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-daedra-vm/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device ich9-usb-ehci1,id=usb,bus=pci.0,addr=0x8.0x7 -device ich9-usb-uhci1,masterbus=usb.0,firstport=0,bus=pci.0,multifunction=on,addr=0x8 -device ich9-usb-uhci2,masterbus=usb.0,firstport=2,bus=pci.0,addr=0x8.0x1 -device ich9-usb-uhci3,masterbus=usb.0,firstport=4,bus=pci.0,addr=0x8.0x2 -drive file=/home/daedra86/Vhd/daedra-vm.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x3,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:df:bc:0e,bus=pci.0,addr=0x2 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x5 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x6 -device usb-host,hostbus=3,hostaddr=3,id=hostdev2 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 -msg timestamp=on
```
start the guest without the keyboard & mouse actually connected to the host:
```
2016-09-17 12:29:14.769+0000: starting up libvirt version: 1.3.1, package: 1ubuntu10.1 (dann frazier <dannf@ubuntu.com> Fri, 03 Jun 2016 14:41:21 -0600), qemu version: 2.6.1 (Debian 1:2.6.1+dfsg-0~16.04), hostname: daedra-pc
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm-spice -name daedra-vm -S -machine pc-i440fx-wily,accel=kvm,usb=off,vmport=off -cpu Haswell,+abm,+pdpe1gb,+rdrand,+f16c,+osxsave,+pdcm,+xtpr,+tm2,+est,+smx,+vmx,+ds_cpl,+monitor,+dtes64,+pbe,+tm,+ht,+ss,+acpi,+ds,+vme,kvm=off -drive file=/usr/share/OVMF/OVMF_CODE.fd,if=pflash,format=raw,unit=0,readonly=on -drive file=/var/lib/libvirt/qemu/nvram/daedra-vm_VARS.fd,if=pflash,format=raw,unit=1 -m 8192 -realtime mlock=off -smp 4,sockets=1,cores=4,threads=1 -uuid b233f286-c032-4aea-8e72-2d8f17b950aa -nographic -no-user-config -nodefaults -chardev socket,id=charmonitor,path=/var/lib/libvirt/qemu/domain-daedra-vm/monitor.sock,server,nowait -mon chardev=charmonitor,id=monitor,mode=control -rtc base=localtime,driftfix=slew -global kvm-pit.lost_tick_policy=discard -no-hpet -no-shutdown -global PIIX4_PM.disable_s3=1 -global PIIX4_PM.disable_s4=1 -boot strict=on -device piix3-usb-uhci,id=usb,bus=pci.0,addr=0x1.0x2 -drive file=/home/daedra86/Vhd/daedra-vm.img,format=raw,if=none,id=drive-virtio-disk0 -device virtio-blk-pci,scsi=off,bus=pci.0,addr=0x3,drive=drive-virtio-disk0,id=virtio-disk0,bootindex=1 -netdev tap,fd=26,id=hostnet0,vhost=on,vhostfd=28 -device virtio-net-pci,netdev=hostnet0,id=net0,mac=52:54:00:df:bc:0e,bus=pci.0,addr=0x2 -device vfio-pci,host=01:00.0,id=hostdev0,bus=pci.0,addr=0x5 -device vfio-pci,host=01:00.1,id=hostdev1,bus=pci.0,addr=0x6 -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x7 -msg timestamp=on
```

---

### Post by KillerKelvUK on 2016-09-18
> **daedra-86 said:**
> I'm purged libvirt from Jacob's PPA and install from ubuntu rep (did not help)

Really, no issues purging the PPA?  I had a bad time of that recently.

> start the guest without the keyboard & mouse actually connected to the host

Was the guest still configured with the USB devices to passthrough even though they weren't physically connected to the host?  Would have expected libvirt to error here?

---

### Post by daedra-86 on 2016-09-18
> **KillerKelvUK said:**
> Really, no issues purging the PPA?  I had a bad time of that recently.

When "apt remove", I could not new install libvirt-bin package. After I use "apt purge", new install was successfully.


> **KillerKelvUK said:**
> Was the guest still configured with the USB  devices to passthrough even though they weren't physically connected to  the host?  Would have expected libvirt to error here?

I misunderstood the question.


After switching from ubuntu 15.10 At 16.04 everything worked. After the  switching from KDE to Gnome, too, it was normal. But I can not remember  exactly, after the upgrade to Win8.1 Win10 before or after one of the  "apt upgrade",not forwarding device to the guest.
Even I think to reinstall Ubuntu and reconfigure the virtual machine.

---

### Post by KillerKelvUK on 2016-09-18
Do you use/run apparmor?  This can cause problems with usb passthrough, any 'DENIED' messages in dmesg output?

---

### Post by daedra-86 on 2016-09-19
dmesg log> when i USB pass to guest:
```
[24788.297881] audit: type=1400 audit(1474307220.147:211): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" pid=19945 comm="apparmor_parser"
[24788.306981] audit: type=1400 audit(1474307220.159:212): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa//qemu_bridge_helper" pid=19945 comm="apparmor_parser"
[24788.310101] audit: type=1400 audit(1474307220.159:213): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:1" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310149] audit: type=1400 audit(1474307220.159:214): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:129" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310190] audit: type=1400 audit(1474307220.159:215): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:257" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310229] audit: type=1400 audit(1474307220.159:216): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:258" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310267] audit: type=1400 audit(1474307220.159:217): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:0" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310304] audit: type=1400 audit(1474307220.159:218): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:128" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310362] audit: type=1400 audit(1474307220.159:219): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:256" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0
[24788.310403] audit: type=1400 audit(1474307220.159:220): apparmor="DENIED" operation="open" profile="libvirt-b233f286-c032-4aea-8e72-2d8f17b950aa" name="/run/udev/data/c189:384" pid=19908 comm="qemu-system-x86" requested_mask="r" denied_mask="r" fsuid=119 ouid=0

```

How to fix? Disable apparmor?

---

### Post by KillerKelvUK on 2016-09-19
I personally disable and remove apparmor but others have had successes in modifying the apparmor profiles to *fix* the issues.  You could temporarily test by disabling the service a boot time and re-enable when ready ```
update-rc.d apparmor disable
```.  If you want to amend the profile then you'll need to google around or start a new thread in the appropriate forum section (I've not really delved into this in much detail)

---

### Post by daedra-86 on 2016-09-20
It helped.
Strange but this message "DENIED" was not in  virt-manager from Jacob's PPA. And disable apparmor did not change anything.
And what is fraught apparmor disable?

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791/comments/14](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1515791/comments/14) - It seems that this decision. Later I check. This can someone help.

---

### Post by KillerKelvUK on 2016-09-20
=d>good news

---

### Post by daedra-86 on 2016-09-21
Problem solved. Topic can be closed. Thank you.

---

