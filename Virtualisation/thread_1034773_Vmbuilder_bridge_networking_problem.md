---
title: "Vmbuilder: bridge networking problem"
date: 2009-01-09
forum: Virtualisation
---

### Post by gecka on 2009-01-09
Hello,

I have created a bridge interface like this (on the server):

```

auto br0
iface br0 inet static
        address 10.0.4.10
        network 10.0.4.0
        netmask 255.255.255.0
        broadcast 10.0.4.255
        gateway 10.0.4.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```

I create a VM using vmbuilder giving it IP 10.0.4.22

smg.xml:
```

<domain type='kvm'>
  <name>smg2</name>
  <uuid>be68974e-5566-707b-bb71-8622f68d6382</uuid>
  <memory>524288</memory>
  <currentMemory>524288</currentMemory>
  <vcpu>1</vcpu>
  <os>
    <type>hvm</type>
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
      <source file='/home/laurent/VMBuilder/smg2/disk0.qcow2'/>
      <target dev='hda' bus='ide'/>
    </disk>
    <disk type='file' device='disk'>
      <source file='/home/laurent/VMBuilder/smg2/disk1.qcow2'/>
      <target dev='hdb' bus='ide'/>
    </disk>
    <interface type='bridge'>
      <mac address='52:54:00:45:02:80'/>
      <source bridge='br0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <graphics type='vnc' port='-1' listen='127.0.0.1'/>
  </devices>
</domain>


```


When my VM has finished installing, I start it. I can then access it from the host OS and SSH to it. I can ping the two ways: host => vm and vm => host. But:

- I can't access the VM from the network (by ip)
- I can't access to the network from the VM (by ip)

I have opened access to 10.0.4.22 in host OS firewall (ufw allow from any to 10.0.4.22). Here is the VM's /etc/network/interface

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.4.22
        netmask 255.255.255.0 
        network 10.0.4.0
        broadcast 10.0.4.255
        gateway 10.0.4.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.0.4.1
        dns-search smg2


```


regards

---

### Post by aesis05401 on 2009-01-09
I use VirtualBox, so this may not apply, but don't you have to tap the bridge and then assign rights to the tap?

First, I have this utility installed: tunctl [<Sourceforge page>]("http://sourceforge.net/projects/tunctl/") 

I create my bridge:
```

sudo brctl addbr br0
sudo ifconfig eth0 0.0.0.0 promisc
sudo brctl addif br0 eth0
sudo dhclient br0

```
Now I do the tap:
```

sudo tunctl -u <username> -t tap0
sudo ifconfig tap0 <ip_Address_4_VM> up
sudo brctl addif br0 tap0
sudo chmod 666 /dev/net/tun

```
Then I configure the VM to use tap0, not br0 (In VirtualBox this is just set on an options page).

I was told it had to work this way, but that info could be less than perfect, but it works for my VMs.  If anyone knows better please let me know too :)

---

### Post by gecka on 2009-01-09
> **aesis05401 said:**
> I use VirtualBox, so this may not apply, but don't you have to tap the bridge and then assign rights to the tap?

Thanks a lot but I have found part of my answer. The VM has, in fact, access to the network and internet. I added "nameserver 10.0.4.10" in my VM resolv.conf and now the VM can access the internet and I still cannot acces my VM from network.

But, shutting down UFW make it work! 

So two question:

- Can the line "nameserver HOST_IP" in VM's resolv.conf be added automatically at install time (using vmbuilder?) ?

- How to configure UFW to allow traffic to my VM ("ufw allow from any to 10.0.4.22" does not work....)

Regards

---

