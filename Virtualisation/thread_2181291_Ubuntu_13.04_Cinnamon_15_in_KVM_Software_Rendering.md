---
title: "Ubuntu 13.04 /Cinnamon 15 in KVM/ Software Rendering Mode"
date: 2013-10-17
forum: Virtualisation
---

### Post by skrap on 2013-10-17
I am new to KVM but willing to learn.  

I have set up an VM using Linux Mint Cinnamon 15 as my guest.  The problem I am having is the Vm Linux Mint  Cinnamon 15 will only run in "Software Rendering Mode"  The text in the terminal console is unreadable.  The same with pop up menus.

Host Is Ubuntu 13.04 raring x86_64  
AMD Athlon(tm) II X3 450 Processor × 3 
 8 Gig Ram 320 GB Hard Drive  
Graphics Gallium 0.4 on AMD RS780

Happy to supply log files but do not know which to supply.

Any help is appreciated.

---

### Post by TheFu on 2013-10-17
First, the physical hardware means absolutely NOTHING inside the VM.  The VM settings for hardware are more important, assuming the client from which you are accessing the VM isn't having any issues.  Is it?

If you could dump the VM settings and put it here, that would be a big help. I suspect you selected the wrong virtual video card. Cirrus seems to be the only what that works always.

Please wrap the xml in "code" tags like this:```

virsh dumpxml {name of VM}
```

---

### Post by skrap on 2013-10-17
Thanks for your quick reply.

```
wwp@wwp-A780L3B:~$ virsh dumpxml bp1
<domain type='kvm'>
  <name>bp1</name>
  <uuid>16df426d-dc83-1d46-114f-b7cce0078d93</uuid>
  <memory unit='KiB'>1048576</memory>
  <currentMemory unit='KiB'>1048576</currentMemory>
  <vcpu placement='static'>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-1.4'>hvm</type>
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
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/bp1.img'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' target='0' unit='0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' target='0' unit='0'/>
    </disk>
    <controller type='usb' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x2'/>
    </controller>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:30:37:90'/>
      <source network='default'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target type='serial' port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <sound model='ich6'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </sound>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </memballoon>
  </devices>
</domain>
```

---

### Post by TheFu on 2013-10-17
Well, I don't see anything obviously wrong, but ... a few notes.
* What is the client OS?
* Is there a specific reason for using IDE for the main storage?  Why not virtio which is much, much, more efficient? On Windows client VMs, use SATA when possible.
* Is there a reason the VM is not using virtio for the network adapter?  On Windows, use Intel PRO/1000.
* Is your network using the automatic NAT subnet?
* I've never used the ICH6 sound driver.  On other VMs, I do force ICH chipsets to get better performance over older options.

Can't tell, but is the vHDD image file sparse or fully preallocated? Sparse will be slower except on SSDs.

Sorry that I can't tell anything about the graphics.
Do you have the same issue with other, similar, VMs on this same machine?

---

### Post by skrap on 2013-10-17
Thanks again TheFu,

By Client I assume you mean the guest OS and that would be linux mint 15 the host is ubuntu 13.04
I am not familiar with virtio.  I will look into that.   I have an older hard disk that uses a sata adapter for a newer motherboard but that is on the host machine.

How do I check to see if the vHDD is using sparse or is fully preallocated?

I set up the VM with Virtual Machine Manager gui and used the default settings offered.  Perhaps I should re-do that and choose other settings?

The network is using the NAT subnet.

This is the only VM that I currently have set up.  I will set up another using a different OS and see what happens.

Thanks

---

### Post by skrap on 2013-10-17
I set up an additional VM using open SUSE 12.1 and everything seems to be working fine.  That leads me to believe the problem with the other VM is due to Linux Mint 15 OS.  Maybe I should post this in a different area or perhaps on the mint forums.

---

### Post by TheFu on 2013-10-18
> **skrap said:**
> Thanks again TheFu,

By Client I assume you mean the guest OS and that would be linux mint 15 the host is ubuntu 13.04
I am not familiar with virtio.  I will look into that.   I have an older hard disk that uses a sata adapter for a newer motherboard but that is on the host machine.

How do I check to see if the vHDD is using sparse or is fully preallocated?

I set up the VM with Virtual Machine Manager gui and used the default settings offered.  Perhaps I should re-do that and choose other settings?

The network is using the NAT subnet.

This is the only VM that I currently have set up.  I will set up another using a different OS and see what happens.

Thanks

Client - means the machine where you are running virt-manager and/or virsh. That may or may not be the hostOS or some other machine anywhere in the world. Thanks to ssh connections, you can manage VMs securely from anywhere.
ClientOS - is the VM with a client OS
HostOS - is the physical server running the OS with KVM or KVM-Spice.

Clear? If not, I can try again.

I've never used NAT for VMs. I'm easily confused by having too many subnets. Already have a bunch of real subnets here.

vHDD - sparse means the actual file on disk is not the size you set for Max. Terrible performance will happen in that case for spinning HDDs. Of course, with SSDs, sparse or fully-preallocated doesn't matter.

You say that Mint is slow inside a VM - have you turned down all the GUI "cheese"?  I've seen Ubuntu Unity bring a Core i7  to its knees - took 20+ minutes to login because of Unity for an Ubuntu VM clientOS. Turning off Unity - used LXDE - made the system almost as fast as running on the native hardware. I'd expect the same from any DE that is not minimal. Initially, use something extremely light, only them should fancier GUIs be added ... if there are issues.

While not KVM specific, [this article]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") explains some overall settings for virtual machines. KVM has been changing too quickly to keep an article like that current, plus the settings needed for enterprise users are VERY DIFFERENT from what a person at home would use. As usual, there are 100+ different ways to accomplish the same thing.

---

### Post by skrap on 2013-10-19
Thank you TheFu,

You have helped me clear up a few things and I realize I need to learn alot more about KVM.  I am sure your time is needed in more urgent situations.  So I have marked this solved.

Thanks again!

---

### Post by Remten on 2014-09-05
Bumping this thread because I too am experiencing "Software Rending Mode" warnings when trying to run Linux Mint Cinnamon 17 as a guest in kvm.
> Cinnamon is currently running without video hardware acceleration and, as a result, you may observe much higher than normal CPU usage.

There could be a problem with your drivers or some other issue. For the best experience, it is recommended that you only use this mode for troubleshooting purposes.
I don't get this warning if I run a Linux Mint Mate guest or an OpenSUSE guest.
I've turned off desktop effects and windows effects in the guest's internal system settings.

I've also tried to enable acceleration in the kvm settings
```

<video>
   <model type='qxl' ram='65536' vram='65536' heads='1' 7>
   <address type='pci' domain= ...
   <acceleration accel3d='yes' accel2d='yes' />
</video>
```(edited)

but that entry doesn't seem to be supported for qxl. (When I re-define the settings, the acceleration entry gets wiped out.)

---

### Post by TheFu on 2014-09-05
This thread is already marked SOLVED - very few people will look.
acceld3d above is misspelled.

---

