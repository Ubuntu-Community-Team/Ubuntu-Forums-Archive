---
title: "virt-manager not using KVM acceleration in 9.10"
date: 2009-12-07
forum: Virtualisation
---

### Post by Explodinglemur on 2009-12-07
After upgrading my desktop from 9.04 to 9.10 I noticed my WinXP VM was running somewhat slowly, so I checked the command that virt-manager was executing and compared its options against the kvm binary's man page.  It is missing the "-enable-kvm" switch to use KVM acceleration.  What would be the best way to enable this option from virt-manager?  I've checked the VM settings, it does not present an option to enable or disable hardware acceleration, and I can't seem to get virsh to connect to the hypervisor to get a VM config dump.

```
root@desktop:~# virsh connect
Connecting to uri: qemu:///system

root@desktop:~# virsh list
Connecting to uri: qemu:///system
 Id Name                 State
----------------------------------

root@desktop:~# virsh version
Connecting to uri: qemu:///system
Compiled against library: libvir 0.7.0
Using library: libvir 0.7.0
Using API: QEMU 0.7.0
Running hypervisor: QEMU 0.11.0

```

Executed by virt-manager:
```
/usr/bin/kvm -S -M pc-0.11 -m 1024 -smp 1 -name winxp -uuid 6f785608-1ab5-ee85-6953-a2f54df6fb6d -monitor unix:/var/run/libvirt/qemu/winxp.monitor,server,nowait -boot c -drive file=/dev/sdb,if=ide,index=0,boot=on -drive file=/dev/cdrom,if=ide,media=cdrom,index=2 -net nic,macaddr=54:52:00:53:16:89,vlan=0,name=nic.0 -net tap,fd=17,vlan=0,name=tap.0 -net nic,macaddr=54:52:00:0b:f6:66,vlan=1,name=nic.1 -net tap,fd=18,vlan=1,name=tap.1 -serial none -parallel none -usb -usbdevice tablet -vnc 127.0.0.1:0 -k en-us -vga cirrus
```

---

### Post by Explodinglemur on 2009-12-11
Ok, it is unlikely this is virt-manager's issue, as all it's doing is telling libvirt what VM to start.  libvirt has the WinXP VM set up to use /usr/bin/kvm as the emulator, which is a symbolic link to /usr/bin/qemu-system-x86_64.  My assumption is that this is a recent change, and qemu-system-x86_64 requires the -enable-kvm switch to use hardware VM acceleration, while the old kvm binary did not require this.  So, anyone have any ideas?  Are you also seeing the same behavior?

---

### Post by Druke on 2009-12-11
don't you need to add the  --accelerate command when setting things up to make all that work?

---

### Post by Explodinglemur on 2009-12-11
> **Druke said:**
> don't you need to add the  --accelerate command when setting things up to make all that work?

When setting things up where?  I created the VMs through virt-manager, which just passes config info to libvirt (which stores the config data in an XML file).  Checking the manpage for qemu-system-x86_64, "-enable-kvm" is the switch to enable full KVM virtualization support.  I think in previous versions, /usr/bin/kvm was a standalone binary that always used KVM if it was available.  Now /usr/bin/kvm is a symbolic link to qemu-system-x86_64, which needs the "-enable-kvm" option to use KVM acceleration (it doesn't seem to do it automatically).  When I start a VM, I click "Run" in virt-manager, which instructs libvirt to start the VM, which executes /usr/bin/kvm with options as appropriate from the XML file.  It does not seem to know about the "-enable-kvm" option that is needed for the new qemu-system-x86_64 binary for KVM acceleration.

If I'm wrong in the way this is working, please correct me...

---

### Post by Druke on 2009-12-11
ah, I know when using virt-install over command line you can pass --accelerate . I'll post what is different in xmls using or not using --accelerate in a second

btw my source is [https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests)

---

### Post by Explodinglemur on 2009-12-14
It looks like this issue was fixed in libvirt 0.7.4, according to [http://libvirt.org/news.html](http://libvirt.org/news.html)
"Bug fixes: ...qemu-kvm needs -enable-kvm flag for VT optimization (Steve Yarmie)..."

Time to file a bug report in launchpad I suppose.

---

### Post by xOrphenochx on 2009-12-14
Awesome, I had previously upgraded from Jaunty to Karmic on my system previously, I guess the XML files were already set at that point or I never noticed. After redoing my system recently I decided to build a new test environment and noticed how sloooow it was. Sadly what I'm using now, Lucid, still contains 7.2. It really took that many versions before this was noticed?

---

### Post by Explodinglemur on 2009-12-14
Hm.  So the VM you created on a previous version was still running quickly when you upgraded, but a new VM you created was not?

What do your VM XML files contain?  (in /etc/libvirt/qemu)

Mine looks like this, it had been working with hardware acceleration in prior Ubuntu versions, but not in 9.10:

```
<domain type='kvm'>
  <name>winxp</name>
  <uuid>6f785608-1ab5-ee85-6953-a2f54df6fb6d</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='i686' machine='pc-0.11'>hvm</type>
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
      <source file='/dev/sda'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='block' device='cdrom'>
      <source dev='/dev/cdrom'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='54:52:00:53:16:89'/>
      <source bridge='br0'/>
    </interface>
    <interface type='bridge'>
      <mac address='54:52:00:0b:f6:66'/>
      <source bridge='br1'/>
    </interface>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes' listen='127.0.0.1' keymap='en-us'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
```

---

### Post by xOrphenochx on 2009-12-15
Unfortunately I had scratched everything previously, so I don't have the older copies to provide. But I had been using Jaunty for awhile and never noticed a major slowdown after upgrading to Karmic. I really noticed it after going to Lucid when it took an hour or more to install Server 2008 R2 when it normally took 20-30min.

---

### Post by Explodinglemur on 2009-12-15
> **Druke said:**
> ah, I know when using virt-install over command line you can pass --accelerate . I'll post what is different in xmls using or not using --accelerate in a second

I set up a test VM using virt-install with the --accelerate switch, and the XML it created looks exactly the same (as far as emulator used and vcpu type) as my existing WinXP VM.  So, that doesn't seem to be it.  Pretty sure it's just a libvirt thing.

---

### Post by geekshlby on 2009-12-15
Have you checked to see if the VM is using the module?
lsmod | grep kvm

Output while a VM is running:
kvm_amd 41556    4 
kvm         190584  1 kvm_amd

Output while no VMs are running:
kvm_amd 41556    0 
kvm         190584  1 kvm_amd

---

### Post by Explodinglemur on 2009-12-15
> **geekshlby said:**
> Have you checked to see if the VM is using the module?
lsmod | grep kvm

Output while a VM is running:
kvm_amd 41556    4 
kvm         190584  1 kvm_amd

Output while no VMs are running:
kvm_amd 41556    0 
kvm         190584  1 kvm_amd

Hm.  According to that, it is using KVM.

Before starting VM:
kvm_intel              43816  0 
kvm                   162688  1 kvm_intel

After:
kvm_intel              43816  3 
kvm                   162688  1 kvm_intel

Okay, given that, I have no idea why my VM is running so much more slowly now...

---

### Post by jimezam on 2010-01-04
Hello.  I spent the day with the same problem and at the end was indeed the lack of "--accelerate" when I was creating the virtual machine.

You can easily solve this with already created VMs editing its XML specification file under /etc/libvirt/qemu and changing its type from qemu (<domain type='qemu'>) to kvm (<domain type='kvm'>).

Hope it helps.

jimezam.

---

### Post by xOrphenochx on 2010-01-04
> **jimezam said:**
> Hello.  I spent the day with the same problem and at the end was indeed the lack of "--accelerate" when I was creating the virtual machine.

You can easily solve this with already created VMs editing its XML specification file under /etc/libvirt/qemu and changing its type from qemu (<domain type='qemu'>) to kvm (<domain type='kvm'>).

Hope it helps.

jimezam.

Thanks, I'll give that a shot today.

---

### Post by xOrphenochx on 2010-01-04
Well damn, it's already set to KVM. I know somethings up, cause it used to take 20-30min to get a 2008 server up, now its more like 90min.

---

### Post by jimezam on 2010-01-08
Well I got a perfomance boost when I changed from QEMU to KVM with the following lines.

<domain type='qemu'> to <domain type='kvm'>
and
<emulator>/usr/bin/qemu-system-x86_64</emulator> to <emulator>/usr/bin/kvm</emulator>

But I don't use Windows so I ignore especific problems of this platform.

I suggest you to check if you have enabled ACPI on you VM and on your guest OS.  It has bother me sometimes.

Good luck.

jimezam.

---

