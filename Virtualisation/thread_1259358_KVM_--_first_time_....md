---
title: "KVM -- first time ..."
date: 2009-09-06
forum: Virtualisation
---

### Post by cwmoser on 2009-09-06
I was running VMWare Player and Server and thought I would give KVM a go.

I have a VMware image I converted for use with KVM.

I have already converted my VMware disks from 2GB to single image, removed VMware tools, and tested that the image works under VMware.


I have successfully run these to make them work with KVM:

[FONT="Courier New"]$ vmware2libvirt -f ./WinXP_KVM.vmx > WinXP_KVM.xml[/FONT]


[FONT="Courier New"]#  virsh -c qemu:///system define WinXP_KVM.xml[/FONT]


But now, how do you start a KVM VM?
I tried this:  $ kvm  ./WinXP_KVM.xml

and a QEMU window pops up with the error:
[B][INDENT]Booting from Hard Disk ...
Boot failed: not a bootable disk
FATAL:  No bootable device[/INDENT][/B]

Any help is appreciated.

Carl

---

### Post by cwmoser on 2009-09-06
When I go to virt-manager, right click on my VM and select Open, the Run button is grayed out.  The Hardware tab shows the Disk hda is my WinXP_KVM.wmdk file.  Looks like I ready to rock n roll but I need do something silly simple.

Also made sure that by BIOS has "AMD Virtualization" enabled.

Carl

---

### Post by cwmoser on 2009-09-06
When I go to virt-manager, right click on my VM and select Open, the Run button is grayed out.  The Hardware tab shows the Disk hda is my WinXP_KVM.wmdk file.  Looks like I ready to rock n roll but I need do something silly simple.

Carl

---

### Post by cwmoser on 2009-09-06
Update, I tried it this way:

$  kvm  ./WinXP_KVM-flat.vmdk  <-- the 16GB VM file

and now it attempts to boot but I get the proverbial "Blue Screen of Death" and the VM reboots into the boot menu.  I tried Safe Mode but still get the Blue Screen of Death.

The Blue Screen scrolls by so fast and I can't stop it - "A problem has been detected adn Windows has shut down to prevent damage to your computer ..."


Any ideas?

Carl

---

### Post by bodhi.zazen on 2009-09-06
Converting an image is not foolproof.

Windows is problematic in that it will detect a hardware change and it is probably easier to do a fresh install of windows rather then convert your vmware image.

---

### Post by cwmoser on 2009-09-07
I tried to do a repair install of Win XP under KVM.

My VM booted from the WinXP installation CDROM but just as soon as the setup showed "Starting Windows", the VM stopped with Guest not running.

Then I selected boot HD from the boot menu and same thing.

I could go back to VMware player and the VM would boot up just fine.

Makes me think that because I could not even do a repair install that there is something mis-configured with my copy of KVM or there is something quirky about KVM.  Is there something in the XML file that needs tweaking?

Any ideas?

Thanks

Carl

---

### Post by cwmoser on 2009-09-07
Here is my XML file -- does it look correct?

<domain type='kvm'>
  <name>KVM: Win XP Professional - Carl Moser</name>
  <uuid>5fdc8640-dc8a-4204-963e-f2c830c3af53</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc'>hvm</type>
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
      <source file='/home/vmware/Virtual Machines/WinXP-KVM/WinXP_KVM.vmdk'/>
      <target dev='hda'/>
    </disk>
    <interface type='network'>
      <mac address='00:0c:29:29:1b:7a'/>
      <source network='default'/>
    </interface>
    <input type='mouse' bus='ps2'/> 
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>

---

### Post by veloce on 2009-09-07
I with Bodhi on this one.  You're spending a lot of time trying to get a converted windows disk working and when you do you'll continue to have problems with it.  

I did manage to get a windows machine transferred over (I found a howto somewhere and I remember there a few archane things you had to do - including one in windows before starting).  When I got it over I had nothing but trouble - *all* the virtual hardware is different. I ended up giving up on the vm and re-installing (which is why I didn't save any links to the howto!).

---

### Post by mitchd123 on 2009-09-13
There's a good article here:

[http://ian.blenke.com/vmware/vmdk/xen/hvm/qemu](http://ian.blenke.com/vmware/vmdk/xen/hvm/qemu)

I don't use virt.  I have another post which shows my startup files: 
[http://ubuntuforums.org/showthread.php?t=1259217&highlight=kvm+windows](http://ubuntuforums.org/showthread.php?t=1259217&highlight=kvm+windows)

---

### Post by lhotari on 2010-05-05
I had this UNMOUNTABLE_BOOT_VOLUME problem after upgrading from jaunty to lucid. 
Check the /var/log/libvirt/qemu/domainid.log file for errors.
In my case I there was an error "Write failed". This was fixed after I did these changes to the disk image:
```

chown root:root disk.img
chmod 755 disk.img

```
For some reason the same image worked in Ubuntu 9.04 (Jaunty).

I also installed the kvm-pxe package since there were errors pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin" too (this was unrelated to the problem).

---

