---
title: "Best method for virtualization without GUI"
date: 2012-05-10
forum: Virtualisation
---

### Post by RAND0M1ZER on 2012-05-10
Hello ):P

This is my first post on these forums and I'm really starting to get into Linux. After enjoying my time using Ubuntu and Linux Mint for about 6 months and having some more spare time with school over, I decided to finally move my home server from Windows to Ubuntu.

On my previous Windows Server I used VirtualBox to run pfSense which is a freeBSD based router distro. I am trying to figure out what the best way to do this in Linux would be since I am not running a GUI.

I tried following some tutorials online and have been able to create the virtual machines in KVM but get stuck when it comes time to install/configure the OS. This is because I don't know how to access the guest OS.

Any guidance would be greatly appreciated, but please take it slow as I'm still a beginner. :P


My configuration file for the VM pfsense.xml is:

```


<domain type='kvm'>
  <name>pfsense</name>
  <uuid>1789bc53-e9cc-16bb-5e55-d69eb7d0729e</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
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
    <emulator>/usr/bin/kvm</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw'/>
      <source file='/home/administrator/pfsense.img'/>
      <target dev='hda' bus='ide'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <disk type='block' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/md127/Media/pfSense-2.0.1-RELEASE-i386.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
      <address type='drive' controller='0' bus='1' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:e2:c2:9c'/>
      <source network='default'/>
      <model type='e1000'/>
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
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
    <graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>
  </devices>
</domain>

```

Then I tried running:

```

$ sudo virsh console pfsense

```

and get

```

Connected to domain pfsense
Escape character is ^]

```

---

### Post by papibe on 2012-05-10
Hi RAND0M1ZER.

Take a look at this tutorial: [VBoxHeadless - Running Virtual Machines With VirtualBox 3.0 On A Headless Ubuntu 9.04 Server]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-3.0-on-a-headless-ubuntu-9.04-server").

Also take a look at this episode of the Linux Action Show: [Virtualbox tips for Pros and Beginners]("http://www.jupiterbroadcasting.com/12691/virtualbox-pros-and-beginners-las-s18e10/"). The first part of the broadcast is Tech and Linux news. The VirtualBox talk start around half through the end.

I hope that points you in the right direction.
Regards.

---

### Post by RAND0M1ZER on 2012-05-10
Thanks for the links I'll take a look at those. So you would recommend using Virtual Box over KVM?

I do remember seeing some interesting web interfaces for Virtual Box and the familiarity I already have from the Windows version should make it easier however isn't the performance of KVM much better because Virtual Box is software based?

---

### Post by dcstar on 2012-05-16
> **RAND0M1ZER said:**
> Hello ):P

This is my first post on these forums and I'm really starting to get into Linux. After enjoying my time using Ubuntu and Linux Mint for about 6 months and having some more spare time with school over, I decided to finally move my home server from Windows to Ubuntu.

On my previous Windows Server I used VirtualBox to run pfSense which is a freeBSD based router distro. I am trying to figure out what the best way to do this in Linux would be since I am not running a GUI.
.........

If you want a headless box just to run VMs then you should try the free VMware ESXi product. It's only downside is that to manage it you need a networked Windows PC as they only have a client for that platform.

Since this is a "bare metal" VM (based on Linux) the performance is very good, and the flexibility in assigning resources to multiple VMs is excellent as well.

---

### Post by RAND0M1ZER on 2012-05-16
> **dcstar said:**
> If you want a headless box just to run VMs then you should try the free VMware ESXi product. It's only downside is that to manage it you need a networked Windows PC as they only have a client for that platform.

Since this is a "bare metal" VM (based on Linux) the performance is very good, and the flexibility in assigning resources to multiple VMs is excellent as well.

I actually tried ESXi before but ended up not using it because of the 2tb limitation for RAID arrays. I think I'm going to use VirtualBox as it seems to be the easiest to manage.

---

### Post by Amorget on 2012-05-16
There are other bare metal options out there:

[http://ubuntuforums.org/showthread.php?t=1962114&highlight=bare+metal](http://ubuntuforums.org/showthread.php?t=1962114&highlight=bare+metal)

---

