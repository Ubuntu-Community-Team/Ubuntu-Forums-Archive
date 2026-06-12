---
title: "Cant get a virtual machine running"
date: 2012-09-10
forum: Server Platforms
---

### Post by gonro952 on 2012-09-10
i have been trying to get a virtual machine to run on my server for some time now... i really cant figure out what iv done wrong, i followed all the steps in [https://help.ubuntu.com/community/KVM]("https://help.ubuntu.com/community/KVM") and i have gotten a virtual server running but i cannot connect to i have set up bridge networking and it still will not connect, when i try to connect to the ip of the virtual machine it goes just to my server. ill post my network config to see if anyone can help
 ```
# The primary network interface
auto eth0
iface eth0 inet static
        address 172.29.xx.10
        netmask 255.255.255.0
        network 172.29.xx.0
        broadcast 172.29.xx.255
        gateway 172.29.xx.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search biaeos.com

auto br0
iface br0 inet static
        address 172.29.xx.11
        network 172.29.xx.0
        netmask 255.255.255.0
        broadcast 172.29.xx.255
        gateway 172.29.xx.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

and config fer the virtual machine

```
<domain type='kvm' id='1'>
  <name>secretseek</name>
  <uuid>43ecf9e9-88f2-dc23-2ddf-4dde70ab7769</uuid>
  <memory>4194304</memory>
  <currentMemory>4194304</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type arch='x86_64' machine='pc-1.0'>hvm</type>
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
      <source file='/var/lib/libvirt/images/secretseek/ubuntu-kvm/tmp79l96V.qcow2'/>
      <target dev='hda' bus='ide'/>
      <alias name='ide0-0-0'/>
      <address type='drive' controller='0' bus='0' unit='0'/>
    </disk>
    <controller type='ide' index='0'>
      <alias name='ide0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x01' function='0x1'/>
    </controller>
    <interface type='bridge'>
      <mac address='52:54:00:XX:XX:XX'/>
      <source bridge='br0'/>
      <target dev='vnet0'/>
      <model type='virtio'/>
      <alias name='net0'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1'>
      <listen type='address' address='127.0.0.1'/>
    </graphics>
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
  </domain>
```

the virtual machine will start but i cannot ssh into it because it when i use the ip for br0 its still going to the main server not the virtual machine. 
Any help is appreciated.

---

### Post by gonro952 on 2012-09-10
okayy so i got into virsh lastnight and tried to take a screenshot and it looked like it hanged but i tried again just now and here it is 
[ATTACH]224000[/ATTACH]
Obviously somthing is wrong i dont kno exactly what though the building of the machine completed with no errors and here is the command i used to create it
```
sudo vmbuilder kvm ubuntu --suite 'precise' --flavour 'virtual' --arch 'amd64'  --addpkg 'acpid' --firstboot '/var/lib/libvirt/images/secretseek/boot.sh'  --mem '4096'  --rootsize '4096'  --swapsize '2048'  --hostname 'secretseek'   --components 'main'  --addpkg 'tasksel'  --addpkg 'openssh-server'  --name 'vm1'  --user 'secretseek'  --pass 'xxxxx'  --ip '172.29.xx.11'  --mask '255.255.255.0'  --net '172.29.xx.0'  --bcast '172.29.xx.255' --part 'vmbuilder.partition' --templates 'mytemplates' --addpkg 'unattended-upgrades'  --gw '172.29.xx.1'  --dns '208.67.222.123'  --bridge 'br0'  --libvirt 'qemu:///system' 
```

---

