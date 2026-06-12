---
title: "Where does KVM store a VMs disk image? (backup, copy, etc)"
date: 2010-07-16
forum: Virtualisation
---

### Post by thornomad on 2010-07-16
Hello - am a new user of kvm (previously of vmware) and am running Ubuntu Server 10.04.  I built a few VMs with the *vmbuilder* command (succesfully) but I am a little confused as to where, exactly, the virtual machine actually lives on my machine.

Here is an example:

```
$ virsh -c qemu:///system list --all
 Id Name                 State
----------------------------------
  6 ubuntu-media         running
  7 ubuntu-web           running

$ virsh -c qemu:///system dumpxml ubuntu-media
<domain type='kvm' id='6'>
  <name>ubuntu-media</name>
  <uuid>31c0206c-9a44-59db-70e6-8dfc003c2c24</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>destroy</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <source file='/home/.vm/ubuntu-kvm/tmpY8Tawt.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:b9:0c:e6'/>
      <source bridge='br0'/>
      <target dev='vnet1'/>
      <model type='virtio'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5901' autoport='yes' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
  <seclabel type='dynamic' model='apparmor'>
    <label>libvirt-31c0206c-9a44-59db-70e6-8dfc003c2c24</label>
    <imagelabel>libvirt-31c0206c-9a44-59db-70e6-8dfc003c2c24</imagelabel>
  </seclabel>
</domain>

$ ls -a /home/.vm/ubuntu-kvm/
.  ..  run.sh  tmpQLM7Vu.qcow2

```

The xml is referencing a "disk" that doesn't actually exist on my hard drive ... I am trying to understand how I can move or backup this VM but not sure what's going on.

Where is the disk image hiding?  How can I back it up (or move it) ? Could someone explain it to me?

Really appreciate your help.

Damon

---

### Post by sh1ny on 2010-07-16
```
<source file='/home/.vm/ubuntu-kvm/tmpY8Tawt.qcow2'/>
```

This is where your disk image is. You can just copy the file around :)

---

### Post by thornomad on 2010-07-16
> **sh1ny said:**
> ```
<source file='/home/.vm/ubuntu-kvm/tmpY8Tawt.qcow2'/>
```

This is where your disk image is. You can just copy the file around :)

That's what I would have thought!  But if you look at the end there, that file doesn't seem to exist:

```
$ ls -a /home/.vm/ubuntu-kvm/
.  ..  run.sh  tmpQLM7Vu.qcow2
```

---

### Post by kemra on 2010-07-16
On my machine a default install stores the images in:

```
/var/lib/libvirt/images

danny@iacon:~$ ls -l /var/lib/libvirt/images
total 8388728
-rw------- 1 root root 8589934592 2010-07-16 19:45 Appliance_Tester.img
```

---

