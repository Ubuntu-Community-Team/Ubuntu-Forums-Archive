---
title: "How to get DHCP-assigned IP addresses for KVM guests?"
date: 2011-06-02
forum: Server Platforms
---

### Post by sumitsu on 2011-06-02
I am trying to set up 2 Ubuntu virtual machines using KVM+libvirt+qemu on an Ubuntu Server 10.10 host machine (Intel x64 Core i7), then obtain IP addresses for each VM via DHCP.  I believe I've created the libvirt XML files for each VM, and I can use virsh to start the VMs (or so virsh says) but I cannot figure out how to do the following:


[LIST=1]
[*]Set each guest VM to acquire an IP address via DHCP
[*]Find out what the assigned (guest) IP addresses are
[*]SSH into the guest VMs
[*]Change the configuration to assume the assigned IP address as a static IP configuration
[/LIST]

(The reason I'm trying to get the IP addresses via DHCP initially, then configure them statically, is that I have been instructed by the network engineer for my network to do it that way; apparently it is easier for them if I first obtain IP addresses dynamically via DHCP, then they can reserve them for static use once I obtain them.)

I've been through all the documentation I can find about setting up KVM under Ubuntu, and I still cannot determine even if it is getting an IP address, let alone what that address is.

I have also tried opening console access to the guest VM, without success.  It looks like I can start the console, but I do not get any feedback from the guest, nor do I even see what I am typing; there is no input or output visible after the escape character is identified:

```

virsh # ttyconsole VM1
/dev/pts/2

virsh # console VM1
Connected to domain VM1
Escape character is ^]

```Here is my VM libvirt XML:

```

<domain type='kvm' id='4'>
  <name>VM1</name>
  <uuid>6b24ebcb-d86a-90f5-f4c7-61d804c2b3b9</uuid>
  <memory>10485760</memory>
  <currentMemory>10485760</currentMemory>
  <vcpu>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
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
      <driver name='qemu' type='qcow2'/>
      <source file='/root/VM1/tmpT5zz_B.qcow2'/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:e7:9e:44'/>
      <source bridge='virbr0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <serial type='pty'>
      <source path='/dev/pts/2'/>
      <target port='0'/>
      <alias name='serial0'/>
    </serial>
    <console type='pty' tty='/dev/pts/2'>
      <source path='/dev/pts/2'/>
      <target type='serial' port='0'/>
      <alias name='serial0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' autoport='no' listen='127.0.0.1'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
      <alias name='video0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x02' function='0x0'/>
    </video>
    <memballoon model='virtio'>
      <alias name='balloon0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </memballoon>
  </devices>
  <seclabel type='dynamic' model='apparmor'>
    <label>libvirt-6b24ebcb-d86a-90f5-f4c7-61d804c2b3b9</label>
    <imagelabel>libvirt-6b24ebcb-d86a-90f5-f4c7-61d804c2b3b9</imagelabel>
  </seclabel>
</domain>

```And here is my VM network configuration:

```

virsh # net-dumpxml default
<network>
  <name>default</name>
  <uuid>c6070bb8-6af1-9efb-0bad-78188e57d00a</uuid>
  <forward mode='route'/>
  <bridge name='virbr0' stp='on' delay='0' />
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='10.10.10.0' end='10.10.11.255' />
    </dhcp>
  </ip>
</network>

```Please let me know if you have any thoughts/suggestions, or if there is any additional information which I should include.  Thanks!

---

