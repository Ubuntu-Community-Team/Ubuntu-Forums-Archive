---
title: "kvm guest blocks host traffic"
date: 2010-11-29
forum: Virtualisation
---

### Post by donut87 on 2010-11-29
Hi,

I have an ubuntu server (Lucid) setup. I installed kvm/qemu by following [these]("https://help.ubuntu.com/community/KVM/Installation") Instructions. Then I set up my network configuration following [these]("https://help.ubuntu.com/community/KVM/Networking") Instructions. So I have a network bridge for my VMs and everything works fine for my opensuse (a VMWare import) and my WinXP (just for testing). But if I turn on my virtual Ubuntu (Server Lucid or Desktop Maverick) the Host is unreachable can't ping anything in the network/internet. The Guest Ubuntu however is reachable and after some time the other guests become unreachable too. 
Does anyone know this kind of problem? Knowing a solution would be even better :-)


Regards

Donut

P.S. If I should post some logs/information just ask for it.

---

### Post by gdahlm on 2010-11-29
Check to make sure you don't have a duplicate MAC address.  If you could post the config from the file /etc/libvirt/qemu/machinename.xml for the ubuntu host it would be helpful.

---

### Post by donut87 on 2010-12-10
I'm certain that there is no duplicate MAC address. At the beginning we had, but we never did turn on two machines with the same MAC address. After these problems became visible we made sure that every machine has its own MAC address. (Just for explanation: I'm not in control of this network and I have to get an IP address via DHCP; this will only work when I do have a MAC address known to the router configuration).
So here is the config file:

[HTML]
<domain type='kvm'>
  <name>UbuntuRailsServer</name>
  <uuid>02c125fd-22cf-b735-b678-94c0c53298ed</uuid>
  <memory>1048576</memory>
  <currentMemory>1048576</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-0.12'>hvm</type>
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
      <source file='/var/lib/libvirt/images/UbuntuServerRails.img'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <disk type='file' device='cdrom'>
      <driver name='qemu' type='raw'/>
      <source file='/var/lib/libvirt/images/ubuntu_server.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
    <interface type='bridge'>
      <mac address='00:04:75:81:96:2c'/>
      <source bridge='br0'/>
    </interface>
    <console type='pty'>
      <target port='0'/>
    </console>
    <console type='pty'>
      <target port='0'/>
    </console>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' autoport='yes'/>
    <video>
      <model type='cirrus' vram='9216' heads='1'/>
    </video>
  </devices>
</domain>
[/HTML]

---

