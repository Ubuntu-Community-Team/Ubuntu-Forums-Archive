---
title: "w2003serv under qemu"
date: 2009-07-17
forum: Virtualisation
---

### Post by kuda on 2009-07-17
God morning (here in norway now :-).

I have some problem with instalation of win2003serv under qemu. I have used virt-install to privide installation. But after first reboot of win-installer I got an error that "setup can't find cdrom" so that perhaps means cdrom/iso missing. I have tried to load both iso and physical cdrom but without success :-/, trying to google it out. I have created to iso files and need to mount them to finish the installation.

using u8.04.2 x64, kqemu/qemu, and distrokernel    on poweredge r610

Thanx a lot in advance!

k.

command to initializing image:

virt-install --connect qemu:///system --hvm -n wservdmz -r 512 -f wservdmz.qcow2 -s 12 -c /mnt/isos/win2003servcd1.iso --vnc --noautoconsole --os-type windows --os-variant win2k3 -network=bridge:br1 --noacpi

cat /etc/libvirt/qemu/wservdmz.xml

<domain type='qemu'>
  <name>wservdmz</name>
  <uuid>ea1f195d-db38-9cca-7366-77ca60dd8fff</uuid>
  <memory>2048000</memory>
  <currentMemory>2048000</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc'>hvm</type>
    <boot dev='hd'/>
  </os>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/qemu-system-x86_64</emulator>
    <disk type='file' device='disk'>
      <source file='/mnt/images/wservdmz.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='cdrom'>
      <source file='/mnt/isos/win2003serv_r2_x32_cd1.iso '/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:3e:57:da:bb'/>
      <source bridge='br1'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>

and cat from log:
/usr/bin/qemu-system-x86_64 -M pc -no-kqemu -m 2000 -smp 1 -monitor pty -localtime -no-acpi -boot c -hda /mnt/images/wservdmz.qcow2 -net nic,macaddr=00:16:3e:57:da:bb,vlan=0 -net tap,fd=10,script=,vlan=0 -usb -usbdevice tablet -vnc 127.0.0.1:0

---

