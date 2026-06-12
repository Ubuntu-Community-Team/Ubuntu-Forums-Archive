---
title: "KVM and virtIO"
date: 2008-07-15
forum: Virtualisation
---

### Post by chrroessner on 2008-07-15
Hi,

I managed to set my KVM guest to use virtio_blk and virtio_net. But what I could not figure out was on how to setup virtio_balloon.

How do I need to configure my XML file that the guest is loading this module automatically and using it?

```
<domain type='kvm'>
  <name>guest3</name>
  <uuid>94d00e35-5bc6-3240-e7c6-950ee5350e99</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>4</vcpu>
  <os>
    <type>hvm</type>
    <boot dev='hd'/>
  </os>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/dev/vg01/lv_guest3-disk'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:3e:74:29:98'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>
```

Thanks for your help in advance.

Regards
Christian

---

### Post by David Cartwright on 2008-07-17
You'll find the background to the issue here:
[http://www.mail-archive.com/libvir-list@redhat.com/msg05743.html](http://www.mail-archive.com/libvir-list@redhat.com/msg05743.html)

List of KVM 64 supported NIC models here:
[http://www.mail-archive.com/libvir-list@redhat.com/msg05746.html](http://www.mail-archive.com/libvir-list@redhat.com/msg05746.html)

A workaround using a script here:
[http://www.mail-archive.com/libvir-list@redhat.com/msg05782.html](http://www.mail-archive.com/libvir-list@redhat.com/msg05782.html)

If you use the script approach, will be interested to hear how you get on.

cheers ... david

---

