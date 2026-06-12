---
title: "Virtualized guest doesn't boot after host upgrade from 12.04 to 14.04"
date: 2014-09-21
forum: Virtualisation
---

### Post by rationalstorm on 2014-09-21
Upgraded the guest OS, and the host OS both from 12.04 LTS to 14.04 LTS. Guest will boot and display as running in virsh, but is not accessible. I read this bit later in the release notes (which I should have read first, rather than relying on the usually hassle-free release upgrade. 

> [h=3]Ubuntu 14.04 LTS includes Qemu 2.0.0. Due to incompatibilities in the emulated hardware, KVM virtual machines created on 12.04 cannot be live migrated to 14.04 LTS. Likewise, virtual machine snapshots from 12.04 cannot be restored on 14.04 LTS. Memory snapshots can be restored, and virtual machines created on 13.10 can be migrated to 14.04 LTS.[/h]

So how screwed am I? I'm probably not the first with this problem, but I couldn't first a thread on this either. I guess I will have to bin the old VM configuration and create a brand new VM from scratch and import the disk? Any best practices for this situation?

---

### Post by TheFu on 2014-09-22
For Windows, you need to run **sysprep** **before** the migration from inside the Windows system first, then migrate it.  sysprep is not always supported - depends on the Windows license and how many times you may have done it previously.

I've never had any huge issues with migrating Linux VMs - just the normal udev rules stuff.

---

### Post by rationalstorm on 2014-09-22
Thanks TheFu, there was no Windows system involved. Just a 12.04 host and a 12.04 guest, both upgraded to 14.04. I fixed it just now and will quickly describe the solution for the benefit of others. The most crucial bit is to change the machine type from

>  <type arch='x86_64' machine='pc-0.11'>hvm</type>

to

> <type arch='x86_64' machine='pc-i440fx-1.7'>hvm</type>

in the VMs XML descriptor and recreate the VM. After this the VM essentially runs. In my case it only booted to grub and I had to sort out another issue with grub, by first manually loading the kernel from within grub (via VNC) and booting and then reinstalling grub, but this might not even be necessary for others and the change in the XML might be enough to boot again.

---

### Post by TheFu on 2014-09-22
Ah ... for linux migrations, I've also had to remove a 2nd ptty from the XML.
The machine type error is easy to see and fix - there's a clear error from virsh output at VM startup (create) time.  Keep the same MAC addresses for the NICs to avoid udev from creating a new ethernet device inside the guestOS.

For Windows, the errors are less clear, hence why I'd assumed that. It stopped me from migrating my last VM on a 10.04 box to 14.04 for about a year (couldn't get it to work on 12.04 either, hence the extra time).

Anyway - happy you got it working.

Please mark this thread as [SOLVED] ...

---

### Post by rationalstorm on 2014-09-23
Where did you see that clear error for the machine type TheFu? The console output or some log file? I wish I would have had an error as a starting point. In my case the VM appeared to start ok and displayed as "running" in 'virsh list' but were in fact not up and not accessible via ssh, serial console or vnc.

---

### Post by TheFu on 2014-09-23
It has been a long time now, but the errors were in my face - either on the console or in the logs, not anywhere unexpected.  The error I saw said the VM (Windows) didn't support the virtual machine model.  That took me directly to the HVM line and then to the manpage which explained.

---

### Post by heiko_s on 2014-09-26
Just to get this right, are you saying that - under KVM - a host upgrade can break a VM? In particular a Windows VM? After all, Windows should run as a fully virtualised guest.

I'm running a Windows VM for over 2 years on Xen and have updated the host multiple times, including changes of toolstack (only once had an issue that was quickly solved). If a hypervisor upgrade (or other virtualisation solution) would render my VM inoperable I'd rather avoid that solution (=problem). I just like to clarify.

---

### Post by TheFu on 2014-09-26
I've had Xen host refuse to boot on Ubuntu between 4-6 times a year due to kernel updates, not even OS changes.

That meant that no VMs could be booted under Xen.  This was in the 2008 to 2011 timeframe. In 2011, I was running Xen, KVM, ESXi, and Virtualbox - today I run just KVM.  On a current system, I've never had issues with KVM except once - when trying to migrate a Windows guestVM from 10.04 to either 12.04 or 14.04 (took a few years for me to get were I HAD to move it).  During that period, KVM with Linux guestVMs has never failed me current, reboot, kernel update, migration.  They always came up or migrated or updated. The stability and performance has been rock solid.

This is all my personal experience so it isn't necessarily what others have experienced or even typical. Perhaps I was doing something wrong?  I've only been on UNIX and Linux since '93. There were a few things that I preferred about Xen. Can't think of them now, sorry.  I just know that overall, for my needs, KVM works better.  I am not doing video passthru or any VT-d stuff.

The migration of Windows issue was just that - a Windows issue. It saw a different motherboard and refused to boot. That is standard for Microsoft stuff, just the way it is.  The final answer for that issue was **sysprep**.  Of course, not every Windows install can use sysprep and not every Windows install can be reinstalled.  During re-registration, Microsoft forced me to dial into a phone number and get a new, extremely long, code.

---

### Post by sgeir_gisson on 2014-11-19
I'm having the same problem, do-release-upgrade will upgrade my virtual Ubuntu 12.04 guest system to 14.04, but the upgraded system will not boot. No error messages will show in the console and I'm not seeing any error messages in the kvm log files  either! 
The solution you are proposing does not solve my issue. Im using KVM on a fresh install of Ubuntu Server 14.04 LTS and am in the process of migrating several Ubuntu 12.04 virtuals from VMware Server to KVM.
Any ideas?

---

### Post by Doug S on 2014-11-19
Hi and welcome to Ubuntu forums,

show us one of your .xml files from /etc/libvirt/qemu. In particular, this area:```
  <os>
    <type arch='x86_64' [COLOR=#ff0000]machine='pc-i440fx-1.7[/COLOR]'>hvm</type>
    <boot dev='hd'/>
  </os>
```as I recall there were some potential issues there as 12.04 created VM guests defaulted to <type arch='x86_64' machine='pc-1.0'>hvm</type>, which no longer worked.
Disclaimer: My memory about this is a little fuzzy.

---

### Post by sgeir_gisson on 2014-11-20
Here is the KVM xml for the virtual machine in question. I have reverted to a working copy of the virtual machine in 12.04 until I see a viable solution.

<domain type='kvm'>
  <name>saxc2_ubuntu</name>
  <uuid>16bfc653-32d7-8564-0dcd-250be51c4447</uuid>
  <description>Ubuntu 12.04</description>
  <memory unit='KiB'>3145728</memory>
  <currentMemory unit='KiB'>3145728</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>
    <boot dev='hd'/>
  </os>
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
  <clock offset='utc'/>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/kvm/VirtualMachines/saxc2_ubuntu/saxc2-ubuntu.qcow2'/>
      <target dev='vda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='pci' index='0' model='pci-root'/>
    <interface type='bridge'>
      <mac address='52:54:00:8a:71:00'/>
      <source bridge='br3'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
   <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </memballoon>
  </devices>
</domain>

---

### Post by Doug S on 2014-11-21
The differences in our xml files are minor, except that I have never used qcow.> **sgeir_gisson said:**
> <description>Ubuntu 12.04</description>I do not have such a line.> **sgeir_gisson said:**
> <type arch='x86_64' machine='pc-i440fx-trusty'>hvm</type>I just use pc-i440fx-1.7, as mentioned before (and maybe they map to the same thing, I don't know).> **sgeir_gisson said:**
> <driver name='qemu' type='qcow2'/>
      <source file='/kvm/VirtualMachines/saxc2_ubuntu/saxc2-ubuntu.qcow2'/>I have never used qcow. I have this:```
      <driver name='qemu' type='raw'/>
      <source file='/media/newhd/desk_dev.img'/>
```> **sgeir_gisson said:**
> <graphics type='vnc' port='-1' autoport='yes'/>I have this:```
    <graphics type='vnc' port='-1' autoport='yes' listen='0.0.0.0'>
      <listen type='address' address='0.0.0.0'/>
    </graphics>
```> **sgeir_gisson said:**
> <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>Myself, I have never been able to make cirrus work. I use this:```
    <video>
      <model type='vmvga' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
```

---

### Post by Doug S on 2014-11-22
As a test, I converted one of my VM .img (raw) files to qcow2. I also changed the machine and added the description line. It still worked fine.

---

