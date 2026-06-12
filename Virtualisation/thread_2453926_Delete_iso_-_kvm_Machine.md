---
title: "Delete iso - kvm Machine"
date: 2020-11-19
forum: Virtualisation
---

### Post by Quarkrad on 2020-11-19
After one has installed a kvm machine can you delete the install iso? I read a lot about how to delete the machine but not specially how it boots long term. It doesn’t seem right to boot off the iso long term.

---

### Post by TheFu on 2020-11-19
Sure.  However, I keep the ISO around sorta like a boot-flash-usb device to have the "Try Ubuntu" environment so I don't need to download it again should gparted or a chroot environment be needed to correct boot problems later.  

A 20.04 install into KVM-VM needed this about 2 months after it was first installed.  After patching, the system refused to boot. I never figured out how to fix that specific problem and ended up following my backup-restore process ... which begins by doing a fresh, minimal, install of the OS.  That uses the ISO.

---

### Post by CelticWarrior on 2020-11-19
Typically you boot from the installation media only once to install it.
The ISO can then be removed.

---

### Post by Quarkrad on 2020-11-20
Running 20.04 mate host - installing win10 guest vm.  VM boot ok using settings as per 1 and 2.  1png shows my only boot option is sata1 disk1 and 2png shows this sata disk has a source path of /media/dad/...... i.e. kvm image on my hd.  I then rename my win10 install iso and the vm will not boot - 3png shows the message; which makes sense as the iso is renamed.  If I rename the iso back to its original name the vm boots.  At this point despite the settings in 1png the vm is looking at the iso not the kvm image on my hd.

---

### Post by TheFu on 2020-11-20
Did you already install Windows onto the SATA vHDD?
After the install, libvirt should prompt to remove the ISO media ... which means remove it from the VM settings completely.

If that isn't working, I'd use **virsh edit {name of VM}** and fix the XML so it doesn't point to the iso file anywhere and only refers to the vHDD stuff.
Would also be interesting to know if you used BIOS or UEFI for booting, if that's a choice in Windows?  I've never touched Win10.

---

### Post by Quarkrad on 2020-11-21
Not sure what you mean in first sentence.  Windows is installed on another physical hd that I use when dual booting (if this kvm works I'm hoping to do away with dual booting as I hardly use win10) but is not installed on the ext4 hd that  use for my kvm storage.   libvirt did not prompt to remove the iso media.  I used the command to edit the xml file but there does not appear (to me) to be an entry that points to the boot source (my only source, as shown in the gui is the vm image).

```
<domain type='kvm'>
  <name>win10test2</name>
  <uuid>94c1e91a-4dbb-4b4e-b0ba-211208b81689</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://microsoft.com/win/10"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-4.2'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10test2_VARS.fd</nvram>
    <bootmenu enable='no'/>
  </os>
  <features>
    <acpi/>
    <apic/>

```

---

### Post by Quarkrad on 2020-11-21
Sorry - forgot.  I used UEFI when configuring the vm install.

---

### Post by ajgreeny on 2020-11-21
I can see no reason for that iso file being necessary in order to run the VM, but is it still showing as present in the IDE cd-rom in the console information?

---

### Post by CelticWarrior on 2020-11-21
And if it is and then the file is renamed then it should be no surprise having the error message saying exactly that it can't find the file.

---

### Post by TheFu on 2020-11-21
> **Quarkrad said:**
> Not sure what you mean in first sentence.  Windows is installed on another physical hd that I use when dual booting (if this kvm works I'm hoping to do away with dual booting as I hardly use win10) but is not installed on the ext4 hd that  use for my kvm storage.   libvirt did not prompt to remove the iso media.  I used the command to edit the xml file but there does not appear (to me) to be an entry that points to the boot source (my only source, as shown in the gui is the vm image).

```
<domain type='kvm'>
  <name>win10test2</name>
  <uuid>94c1e91a-4dbb-4b4e-b0ba-211208b81689</uuid>
  <metadata>
    <libosinfo:libosinfo xmlns:libosinfo="http://libosinfo.org/xmlns/libvirt/domain/1.0">
      <libosinfo:os id="http://microsoft.com/win/10"/>
    </libosinfo:libosinfo>
  </metadata>
  <memory unit='KiB'>4194304</memory>
  <currentMemory unit='KiB'>4194304</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-q35-4.2'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/win10test2_VARS.fd</nvram>
    <bootmenu enable='no'/>
  </os>
  <features>
    <acpi/>
    <apic/>

```

I've never seen a libvirt XML file that short. Where are all the devices?  There should be HDDs, audio, optical, Spice + spice control channels and USB ports. Where is all that stuff?   Must be something to do with UEFI.  I've never used UEFI to boot any VM before.  For a long time, the UEFI code in libvirt wasn't so good.  Look there (in the UEFI stuff, somewhere?) for the ISO information.

As others have said, you can't just rename the ISO and not remove it completely from the libvirt XML/setup data. In fact, you shouldn't need to rename it at all, just remove it from the libvirt XML. That should be enough.

---

### Post by Quarkrad on 2020-11-21
I agree with what both of you have said.  This issue seems specific to my windows 10 guest - I have other Ubutnu 20.04 guests and they are fine in that they do not require access to the iso to boot.   I have installed another win10 guest using a slightly different method of install - this time my VM hd is a virtio disk with the appropriate drivers - see 7.png.  And, 6a.jpg shows that I have told the vm there is only one device to boot from - VirtIO Disk 1.  Again, (7.png) the source path of VirtIO Disk 1 is my qcow2 image; not the iso.  If other people have a win10 kvm guest working that does not need the ISO to run, I assume there must be a config path somewhere on my set up that, despite what the gui is saying, is pointing to my iso.

---

### Post by TheFu on 2020-11-21
Does Win10 have a "live Try Windows" environment finally - you know - like Linux boot ISOs have had for 20 yrs?

---

### Post by CelticWarrior on 2020-11-21
> **TheFu said:**
> Does Win10 have a "live Try Windows" environment finally - you know - like Linux boot ISOs have had for 20 yrs?

Last time I checked - a couple of weeks ago - it hadn't.

---

### Post by Quarkrad on 2020-11-21
TheFu gave me a clue in #10 - I installed a new vm using legacy boot but during the install I noticed the two CDROMs - although they were not ticked one pointed to the winiso, because it is used as part of the install, and the other was pointing to the virtio driver iso.  I removed both devices and the vm booted using the qcow2 images rather than the iso.

---

