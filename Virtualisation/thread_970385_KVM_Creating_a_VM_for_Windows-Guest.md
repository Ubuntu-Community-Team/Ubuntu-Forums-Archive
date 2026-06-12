---
title: "KVM: Creating a VM for Windows-Guest"
date: 2008-11-04
forum: Virtualisation
---

### Post by pred2k on 2008-11-04
Hi, on my Ubuntu 8.10 Server with KVM Installation (Intel CPU with VT-Support) i want to run a virtual Windows XP SP2. I already successfully created a Ubuntu-JeOS-VM with the vmbuilder.

The Windows-CD-Image is on the server. The server has no display and is manged via ssh. When booting the new Windows system for installation, i want to connect with vnc to that VM and go though the setup. After everything is configured i want to use the better Windows Remote Desktop for accessing the virtual Windows System.

So, now my question is: How to create the Windows Virtual Maschine?
I read about the way [creating it with virt-install]("https://help.ubuntu.com/community/KVM#Create%20VMs%20running%20other%20operating%20systems:%20virt-install") or simply with qemu-img and kvm.

the one command would be:
```
qemu-img create windows.img -f qcow 5G
sudo kvm -no-acpi -m 750 -cdrom ~/windows_xp_install.iso -boot d windows.img
```

the others are:
```
sudo apt-get install python-virtinst
sudo virt-install --connect qemu:///system -n xpsp2 -r 512 -f windows.qcow2 -s 12 -c windowsxpsp2.iso --vnc --noautoconsole --os-type windows --os-variant winxp --network=br0
```
virt-install creates an Virtual Machine that will be manged with libvirt with an XML-File, right?

Sorry for my newbie question: But what is qemu? what do i need it for. I though kvm has has everything to create and run virtual machines.

Any more advice for doing it better or different?

---

### Post by rmcewen on 2008-11-05
Yes, virt-install creates the xml config file needed by libvirt and its associated toolset in /etc/libvirt/qemu.  Since your box is headless, you could use the libvirt tool "virsh" to manage the guest once it's created (i.e start, shutdown, pause, resume, etc).

Qemu is the processor emulation software that kvm uses as its "management layer" I guess you could say.  Or I guess you could say kvm is just qemu with a hardware virtualization driver.  What this means is that pretty much anything qemu supports, so does the qemu/kvm combination.  I found much more info on the qemu forum than the kvm site when working with raw qemu/kvm commands.

When I was playing with kvm, I first tried everything using the "raw" kvm commands which worked fine and looked something like this to start an existing guest:

> qemu-system-x86_64 -hda debian-etch.img -m 512 -boot c -net nic,vlan=0,macaddr=00:00:10:52:37:48 -net tap,vlan=0,ifname=tap0,script=no -vnc :1

Next I basically rebuilt everything the libvirt/virt-install way which lookes like this to start an existing guest:

> virsh start debian-etch-master

Creating the guests I thought was about the same using either "raw" or "libvirt" methods as far as complexity.

Using libvirt has a few pros and cons I think:

PROS:

1. Management of existing guests is easier since all settings are stored in the xml config file.

2. Bridged networking was easier to set up since it handles creating the tap interfaces automatically.

3. It has a decent programming API which was important to me.

CONS:

1. Every last configuration option qemu/kvm supports may not be supported by libvirt (though I haven't noticed any so far).

In any case, I was able to create a Windows 2003 Server guest using both methods with no problems.  Like you, I used Vnc for the initial install and then switched to Remote Desktop to manage the guest but keep in mind, you'll have to use bridged networking for the guest, otherwise you won't be able to connect externally.

My main advice would be to not try to mix the methods, pick one and stick with it.  I'd use the libvirt tools unless you really want to know the underlying command/options.

Also note that I used the latest kvm and libvirt versions by building from source so I can't say for sure if there are any issues with the repository packages.

---

### Post by pred2k on 2008-11-06
Thanks for your information, rmcewen.

I created the Windows VM now with this command:

```
sudo virt-install --connect qemu:///system -n xpsp2 -r 512 -f windows.qcow2 -s 12 -c windowsxpsp2.iso --vnc --noautoconsole --os-type windows --os-variant winxp --network=br0 --hvm
```

The --hvm Parameter was needed, else got get this error: [FONT="Courier New"]Unsupported virtualization type[/FONT]

After the quick and successfull creation i need to manually edit the VMs-xml-File. The XP-ISO wasn't included as CD-ROM right. Also i need do change the boot-device that the machine booted from cd and the listen ip for vnc so that i could access if over my bridged-network (also needed to be changed in qemu.conf).

Creating the partition and the first copy-process of the WinXP was no Problem :)

[IMG]http://www.abload.de/img/1-xpinstallunterqemu-kyjeb.png[/IMG]

But after that, when the system reboots, i am getting this error now:

[IMG]http://www.abload.de/img/2-xpinstallfehlerordl.png[/IMG]

That means in english: [FONT="Courier New"]Error, reading the Harddisc.
Restart with ctrl+arl+del[/FONT]

Edit: The problem was also reported here: [http://ubuntuforums.org/showthread.php?t=879329](http://ubuntuforums.org/showthread.php?t=879329)

---

### Post by rmcewen on 2008-11-07
That's essentially the way I did it.

I did create the disk image manually with qemu-img prior to calling virt-install:

```
qemu-img -f qcow2 hda.qcow2 100GB
```

Here's my virt-install:

```
virt-install -n win2003-master \
-r 1000 \
--vcpus=1 \
-f /var/vm/win2003-master/hda.qcow2 \
-w bridge:br0 \
--vnc \
--accelerate \
-c /var/iso/win2003.iso \
--os-type=windows \
--os-variant=win2k3 \
--noapic \
--connect qemu:///system
```

And the config file I ended up with ("virtio" for the network model is after installing virtio driver in guest):

```
<domain type='kvm'>
  <name>win2003-master</name>
  <uuid>13f177ac-adfd-3cc9-a61d-9f9c10633845</uuid>
  <memory>1024000</memory>
  <currentMemory>1024000</currentMemory>
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
    <disk type='file' device='disk'>
      <source file='/home/data/vm/win2003-master/hda.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='00:16:3e:43:8a:08'/>
      <source bridge='br0'/>
      <model type='virtio'/>
    </interface>
    <serial type='pty'>
      <target port='0'/>
    </serial>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='tablet' bus='usb'/>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
  </devices>
</domain>

```

As I mentioned, my libvirt and qemu/kvm are the latest versions compiled from source so maybe something was fixed.

```
root@vhost:~# virsh version
Compiled against library: libvir 0.4.6

root@vhost:~# qemu-system-x86_64
QEMU PC emulator version 0.9.1 (kvm-77)
```



I assume after changing the xml config you did a "virsh define <filename>" or possibly restarting libvirtd would do it too.

I haven't tried a guest with XP, just 2003 server.  I'll try one with XP and see if I have any issues.

---

### Post by pred2k on 2008-11-07
I tried to use another HDD-Image. So i did:
```
sudo apt-get install qemu
qemu-img create -f qcow2 xpsp2.qcow2 10G

```
But i didn't help.

The added this to my xml-File:
```
  <features>
    <acpi/>
    <apic/>
    <pae/>
  </features>
```
Re-defined it and tried to install XP again.
Still the same error.

I use the repository packages for 8.10 Server amd64:
```
pred2k@ubunas:~$ virsh version
Connecting to uri: qemu:///system
Compiled against library: libvir 0.4.4
Using library: libvir 0.4.4
Using API: QEMU 0.4.4
Running hypervisor: QEMU 0.9.1
```

I tried to install WinXP 32bit with SP3, WinXP 64 Bit and Win Server 2003 R2 without any success.

---

### Post by rmcewen on 2008-11-13
I wonder if it could be some sort of problem with the permissions of the disk image file.  Maybe check those to make sure it is accessible by the user qemu/kvm is running as.

---

### Post by rcrcomputing on 2008-11-22
I just noticed this thread.  I posted a quick workaround for this about a week ago in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/105195](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/105195)

---

### Post by airoff on 2008-11-23
I hope someone else can verify this, but I believe I have a workaround to the "lost drive" problem.  I used W2K3 R2 Standard, 32 bit on a Ubuntu 8.10 server 64 bit.

Use Virtual Machine Manager to create a new VM.  Set the hard disk to an IMG, not a QCOW2.

The preinstall went fine.  Before you reboot the windows machine, remember to set the CD back to the win2k3 iso image.

Worked for me - anyone else?

--airoff

---

