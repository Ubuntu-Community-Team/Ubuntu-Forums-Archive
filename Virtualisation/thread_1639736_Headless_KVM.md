---
title: "Headless KVM"
date: 2010-12-07
forum: Virtualisation
---

### Post by jwkite on 2010-12-07
I have been running a pair of 32-bit guest Ubuntu Servers as virtual machines on a 32-bit host Ubuntu server.  Let's call them UBUNTUHOST, UBUNTUWEB, and UBUNTUNETWORK (running dns, dansguardian, etc).  All three are running Ubuntu 10.10 server edition.  UBUNTUHOST is running VMWare Server.  The other two servers are running as VMWare images under VMWare Server.  These are intended to be headless machines without X or any other graphical environment.

I have new 64-bit hardware and would like to continue with a similar setup.  After coming to grips with the fact that VMWare Server is at end of life and that I have some requirements that cannot be met under ESXi, I have decided to move to KVM (my CPU does support virtuatlization).  I would like to keep a similar configuration.

I first followed this howto:
[http://havetheknowhow.com/Configure-the-server/Configure-KVM.html](http://havetheknowhow.com/Configure-the-server/Configure-KVM.html)

and I then followed this one to migrate my VMWare images to KVM:
[http://blog.mymediasystem.net/uncategorized/vmware-kvm-migration-guide/](http://blog.mymediasystem.net/uncategorized/vmware-kvm-migration-guide/)

When I run "virsh UBUNTUWEB" I receive no errors.  Kvm_stat shows activity, but virt-top does not.

The commend "virsh console UBUNTUWEB" returns "No console available for domain."

I cannot ssh to the virtual machine.

I do not even know how to begin troubleshooting this problem.  At this point I do not know if it is a networking issue or something else.  I have read all of the documentation I can find, and I'm a bit lost.

From the /var/lob/libvirt/qemu/UBUNTUWEB.log file:
```
LC_ALL=C PATH=/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/sbin:/bin QEMU_AUDIO_DRV=none /usr/bin/kvm -S -M pc-0.12 -cpu qemu32 -enable-kvm -m 512 -smp 1,sockets=1,cores=1,threads=1 -name Squarebear4 -uuid 6a65319d-1d38-4d8e-a0dd-03bcb91c03ef -nodefaults -chardev socket,id=monitor,path=/var/lib/libvirt/qemu/UBUNTUWEB.monitor,server,nowait -mon chardev=monitor,mode=readline -rtc base=utc -boot c -drive file=/mnt/storage/Squarebear3/UBUNTUHOST.vmdk,if=none,id=drive-ide0-0-0,boot=on,format=raw -device ide-drive,bus=ide.0,unit=0,drive=drive-ide0-0-0,id=ide0-0-0 -device rtl8139,vlan=0,id=net0,mac=00:0c:29:2f:e3:8a,bus=pci.0,addr=0x3 -net tap,fd=34,vlan=0,name=hostnet0 -usb -vnc 127.0.0.1:0 -vga cirrus -device virtio-balloon-pci,id=balloon0,bus=pci.0,addr=0x4 
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"

```

And my defining .xml file:

```
<domain type='kvm'>
  <name>UBUNTUWEB</name>
  <uuid>6a65319d-1d38-4d8e-a0dd-03bcb91c03ef</uuid>
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
      <source file='/mnt/storage/UBUNTUWEB/UBUNTUWEB.vmdk'/>
      <target dev='hda' />
    </disk>
    <interface type='bridge'>
      <mac address='00:0c:29:2f:e3:8a'/>
      <source bridge='br0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>
```

Thank you for any help.

---

### Post by sendmoreinfo on 2010-12-07
First,  since the virtual disk is in VMDK format, you should fix  the XML definition:

> <source file='/mnt/storage/UBUNTUWEB/UBUNTUWEB.vmdk'/>

should be

> <source file='/mnt/storage/UBUNTUWEB/UBUNTUWEB.vmdk' format='vmdk'/>

virsh console will work only if  serial console is set up in the VM.  Before that, you'll have to use VNC console.

---

### Post by jwkite on 2010-12-07
Thank you so much for responding.

I have changed the line as recommended and started, but I still see nothing in virt-top.  What other errors may I be overlooking and is there a better way to tell if the virtual machine is actually running?

Thanks much.

---

### Post by sendmoreinfo on 2010-12-08
Try to connect to the VNC console of this VM.  'virsh vncdisplay ...' will give the address to connect to.

---

### Post by jwkite on 2010-12-13
Thank you so much.  I'm now one step closer!

For future reference for newbies like me, I changed the definition file as follows:
```
 <graphics type='vnc' port='5904' listen='192.168.1.29'/>
```
192.168.1.29 is the IP address of the host machine.

(Thanks to the [Eucalyptus]("http://cssoss.wordpress.com/2010/05/10/eucalyptus-beginner%E2%80%99s-guide-%E2%80%93-uec-edition-chapter-9-%E2%80%93%C2%A0troubleshooting/") troubleshooting site for that tip)

Now I can connect via VNC to 192.168.1.29:5904.

So now I have access to a console and receive the following messages:
```
Booting from Hard Disk...
Boot failed:  not a bootable disk

No bootable devices

```

At least I know what to look at next.  I will post updates back here.  Thanks again for the help.

---

### Post by jwkite on 2010-12-13
Thanks to the [Linux Archive]("http://www.linux-archive.org/gentoo-user/437896-problems-libvirt-qemu.html") for helping me recognize that I needed to add a line to my .xml file.

I changed
```
    <disk type='file' device='disk'>
      <source file='/mnt/storage/UBUNTUWEB/UBUNTUWEB.vmdk'/>
      <target dev='hda' />
    </disk>

```

To

```
    <disk type='file' device='disk'>
      <driver name='qemu' type='vmdk'/>
      <source file='/mnt/storage/UBUNTUWEB/UBUNTUWEB.vmdk'/>
      <target dev='hda' />
    </disk>

```

by adding the driver name and moving the type to that line.

It now appears that my migration is complete.  I hope my struggles help someone else in the future.  Thanks again sendmoreinfo for your help.

---

### Post by jwkite on 2010-12-13
For the record, this is solved for UBUNTUWEB, but I still cannot get UBUNTUNETWORK to work.  They are nearly identical images - frustrating!

---

### Post by HDave on 2010-12-31
I have been using VMWare Server for some time and have considering moving to KVM.  Sorry to hijack this thread, but what is your opinion of KVM and/or virtlib tools?  Happy you made the switch?

---

