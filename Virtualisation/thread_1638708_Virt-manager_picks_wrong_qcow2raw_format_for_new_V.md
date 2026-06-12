---
title: "Virt-manager picks wrong qcow2/raw format for new VMs (No bootable device.)"
date: 2010-12-06
forum: Virtualisation
---

### Post by donh3 on 2010-12-06
OS: Kubuntu 10.04
Virt-manager 0.8.2 using libvirt and qemu/kvm

Problem:
I recently loaded a qcow2 virtual hard drive image into a new virtual machine that I created with with virt-manager.  I couldn't get the vm to boot event thought it was fine before I detached the hard drive image.

The error I received from the virt-manager console:
```
Booting from Hard Disk...
Boot failed: not a bootable disk

No bootable device.
```Leaving this displayed on the console and checking the command run:
```
ps aux | grep kvm
```Results in:
```
/usr/bin/kvm -S -M pc-0.12 -enable-kvm -m 768 -smp 1 -name Win7_x64-Dell -uuid 771259fa-01f7-ecea-f9e8-4c0576498354 -chardev socket,id=monitor,path=/home/localadmin/.libvirt/qemu/lib/Win7_x64-Dell.monitor,server,nowait -monitor chardev:monitor -localtime -boot c -drive if=ide,media=cdrom,index=2,format=raw -drive file=/storage/vmimages/Windows7_x64-01/qcow2-60GB_HDD1.img,if=ide,index=0,boot=on,format=**[COLOR=Red]raw[/COLOR]** -net nic,macaddr=52:54:00:6e:11:67,vlan=0,model=e1000,name=e1000.0 -net user,vlan=0,name=user.0 -chardev pty,id=serial0 -serial chardev:serial0 -parallel none -usb -usbdevice tablet -vnc 127.0.0.1:0 -vga cirrus -soundhw es1370

```**Solution:**
It appears that virt-manager does not read the hard drive image format of a pre-existing image when creating a new virtual machine and instead chooses the "raw" format.  Since virt-manager seems to store it's setting internally, you cannot just edit the ~/.libvirt/qemu/VMNameHere.xml file. 

You must export the libvirt vm settings to xml, fix the hard drive image formatting, and import the vm settings back into libvirt.

Get vm name:
```
virsh -c qemu:///session list --all
```If your vm is in the system account instead of your user account replace qemu:///session with qemu:///system

Export vm settings:
```
virsh -c qemu:///session dumpxml VMName > ~/Desktop/VMName.xml
```Update the hard drive format in the xml file:
```
From   
<devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='**[COLOR=Red]raw[/COLOR]**'/>
      <source file='/storage/vmimages/Windows7_x64-01/qcow2-60GB_HDD1.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
To
<devices>
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='[COLOR=Red]**qcow2**[/COLOR]'/>
      <source file='/storage/vmimages/Windows7_x64-01/qcow2-60GB_HDD1.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
```Remove old vm settings in virt-manager:
Open virt-manager and delete the problem vm but make sure to leave the hard drive image

Import in the fixed xml file:
```
virsh -c qemu:///session define ~/Desktop/VMName.xml
```The vm will automatically appear in virt-manager.
The vm should now work fine.


Other notes:
This qcow2/raw issue occurs to every hard drive image I load into a vm using virt-manager and so I must edit and reimport the xml each time.

You might be able to shutdown libvirt-bin and qemu-kvm services, edit the ~/.libvirt/qemu/VMNameHere.xml file and reboot as a shorter method but I didn't verify this works.

Hopefully this will save some several hours of searching.

---

### Post by Aquinus on 2011-01-04
Excellent guide. Hits the problem right on the nose.
Works on clean Ubuntu Server 10.04 LTS 64-Bit install.
Thank you.

---

### Post by flabdablet on 2011-01-11
Just struck this issue after updating my Debian Squeeze kvm hosting box. All my Windows VMs started fine, but my Debian utility VM failed to boot. Thinking I was dealing with a corrupted qcow2 file, I tried booting it with a CD image and using disk fixing tools - which, given that KVM was actually treating the qcow2 as a raw disk image, buggered it completely :-(

This is absolutely not a Windows guests vs Linux guests thing - it just so happened that my Windows VMs were all using raw image files, and the Debian VM was the only one running off a qcow2.

The XML file that originally defined my Debian VM included this disk section:

```
    <disk type='file' device='disk'>
      <source file='/home/vdc/0/hd/utility-vda.qcow2'/>
      <target dev='hda' bus='virtio'/>
    </disk>
```

With the previous version of libvirt, doing a **virsh dumpxml** on it revealed that libvirt had added an <address> tag, like this:

```
    <disk type='file' device='disk'>
      <source file='/home/vdc/0/hd/utility-vda.qcow2'/>
      <target dev='hda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
```

And the first time I started it up after upgrading libvirt0 to 0.8.3-5, libvirt added a new <driver> tag, like this:

```
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/vdc/0/hd/utility-vda.qcow2'/>
      <target dev='hda' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
```

...and got the format wrong. I surely wasn't expecting that!

Libvirt always used to guess the type correctly; it never used to *need* to be told what format the disk image was in. It got it right for all my Windows VMs by pure luck, lulling me into a false sense of security, which induced me to screw up my qcow2-based Debian VM. Grrrrr. 

Backups are, of course, a Good Thing; and after restoring the screwed qcow2 from a recent backup, all I had to do to make everything work was change **type='raw'** to **type='qcow2'** using **virsh edit**. This has the same effect as the **virsh dumpxml** - edit xml file - delete vm - **virsh define** sequence recommended by donh3, and is easier and less error-prone.

Do the **virsh edit** twice to make sure your edits have been accepted as you expected, since libvirt does sometimes make silent changes (usually additions) to what you've asked it for.

Also, you can avoid needing to supply the -c option on every virsh command by adding a line like
```
export VIRSH_DEFAULT_CONNECT_URI="qemu:///system"
``` or ```
export VIRSH_DEFAULT_CONNECT_URI="qemu:///session"
``` to your ~/.profile login script.

---

### Post by William IK on 2013-02-25
I had similar issues as this.

I installed KVM on Ubuntu 12.04, and created an Ubuntu VM. I managed to restart the machine any number of times. But then I added a third HDD, and the entry to the first was removed from the vm-name.xml file.

I have to edit the file to add the image again. Then I had to problems booting up.

---

### Post by overdrank on 2013-02-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

