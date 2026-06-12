---
title: "Ubuntu 9.04 KVM Windows Server 2008 2 vcpu - reboot results in blue screen"
date: 2009-09-04
forum: Server Platforms
---

### Post by yatesco on 2009-09-04
Hi,

Er, title says it all, but let me repeat..

I am running KVM on Ubuntu 9.04 server edition and I have successfully installed Windows Server 2008 (2GB RAM, 2 vCPU) without issue.

Until I reboot - and then I get a blue screen with STOP 0x000007f.

If I reduce the number of virtual CPUs to 1, the problem goes away.  The 2008 server however is running tomcat and SQLServer 2008 and is supposed to emulate the client's environment (which is a physical server with single dual core CPU).

Any ideas?  Google hasn't turned up much :(

Many thanks,

Col

---

### Post by Vegan on 2009-09-04
I see that error a lot with Windows on certain machines. This is because the BIOS is buggy.

---

### Post by yatesco on 2009-09-21
Apologies for dumping this, but this is really holding me back :(

Does anyone have any ideas on how to prevent this?  I really need to have a windows 2008 virtual machine with more than one cpu using kvm and ubuntu 9.04.

---

### Post by rickyjones on 2009-09-21
> **yatesco said:**
> Apologies for dumping this, but this is really holding me back :(

Does anyone have any ideas on how to prevent this?  I really need to have a windows 2008 virtual machine with more than one cpu using kvm and ubuntu 9.04.

I'm not familiar with using KVM but have you considered a different virtualization product? That could be the issue. 

Thanks,
Richard

---

### Post by yatesco on 2009-09-22
Hi Richard,

I need to stick with kvm, or rather *really really* want to stick with kvm as it is the backbone of our virtualisation infrastructure.  All our scripts to backup and patch etc. are based on kvm.  Also, from what I remember installing two different virtualisation technologies on the same physical machine is a quick way into a world of pain.

Thanks for the suggestion though.  I have considered purchasing another physical box on which I could install VMware, but I really don't want to do that.

Col

---

### Post by rickyjones on 2009-09-22
> **yatesco said:**
> Hi Richard,

I need to stick with kvm, or rather *really really* want to stick with kvm as it is the backbone of our virtualisation infrastructure.  All our scripts to backup and patch etc. are based on kvm.  Also, from what I remember installing two different virtualisation technologies on the same physical machine is a quick way into a world of pain.

Thanks for the suggestion though.  I have considered purchasing another physical box on which I could install VMware, but I really don't want to do that.

Col

Understandable. How is KVM configured for use with Server 2008? What configuration options are being used for this virtual machine?

Thanks,
Richard

---

### Post by yatesco on 2009-09-24
I am using libvirt for everything.  The VM itself was created using virt-manager.

Here is the (/etc/libvirt/qemu/xyz.xml) XML file:

```

<domain type='kvm'>
  <name>XXX</name>
  <uuid>XXX</uuid>
  <memory>2097152</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='localtime'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='block' device='disk'>
      <source dev='/dev/fileserver/XXX'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='network'>
      <mac address='XXX'/>
      <source network='default'/>
    </interface>
    <interface type='bridge'>
      <mac address='XXX'/>
      <source bridge='br0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/15'/>
      <target port='0'/>
    </serial>
    <console type='pty' tty='/dev/pts/15'>
      <source path='/dev/pts/15'/>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
  </devices>
</domain>

```

---

### Post by yatesco on 2009-09-24
Ah, this appears to be a known problem: [https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/341979](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/341979)

Does anyone have any experience with running Karmic's version of kvm on Jaunty?  I am loath to do this as it is a production box, but this might be a way out.

Col

---

