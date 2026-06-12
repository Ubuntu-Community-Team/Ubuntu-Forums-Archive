---
title: "Following along create a new VM with VMManager - flummoxed at network"
date: 2022-05-05
forum: Virtualisation
---

### Post by hpu3 on 2022-05-05
I choose `Bridged device' when going thru "create a new VM" with VMManager... I want a bridged device but when I select that from the drop down (which has only 3 choices) It demands a Device name.  I see no way to determine what goes in that slot.

The process so far has selected a "Device model" named Virtio ( with no help from me)  There are several others, I've tried them all but that implacable "Device name" remains blank and no way to figure out what goes there.

However, something has to go there since the procedure will not proceed without a correct entry for 'Device Name'

I do have an active network connection in the host.  And have generated and run numerous VMs using VBox.
 on this host.

 Some say the KVM type vm is better.... Thats why I'm slogging around with it, but so far, it seems only better at aggravating the stink out of USER.

All the docs on bridging get way out in the weeds, but still need a real name for `Device Name:'

---

### Post by TheFu on 2022-05-05
To my knowledge, you have to create a bridge outside virt-manger.  How to do that depends on the specific release.

virtio is the driver you want to use for anything that supports it.  Networking, disk controllers and new for 22.04, GPUs.  It is designed to be extremely fast and have low-overhead for virtual machines.  For example, my virtio NICs using a bridged connection routinely test at 25-35 Gbps speeds - so, over 25x the speed of the physical NIC in the system. Obviously, the physical NIC comes into play when networking outside the same machine, but between different VMs and the host machine, it is freakishly fast.

For the disk controller, it isn't THAT much faster, but it definitely has much lower overhead.

I don't have a 22.04 KVM host, so I don't know how much faster virtio-gpu is compared to the SPICE+QXL protocol.  Plus, since I typically connect to a desktop over the network, not from the same physical machine, I have doubts that virtio-gpu will be useful to me.

VBox is a toy in comparison to KVM, slower, and much less stable IME.  

I can help with how to setup a bridge for 18.04 from first hand knowledge.  I don't have first hand knowledge for bridges since netplan took over, but the netplan.io website does have examples.  If you are on a desktop, I don't think there is any GUI method to create a bridge. You'll need to learn and love /etc/netplan/ yaml files. Here's an example that you can change for your needs:
```
# #################################
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: networkd
  ethernets:
     [COLOR="#008000"]eth0[/COLOR]:
       dhcp4: false
       dhcp6: false
  bridges:
      **br0**:
        interfaces: [[COLOR="#008000"]eth0[/COLOR]]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.1.15/24]
        gateway4: 192.168.1.1
        nameservers:
           addresses: [192.168.1.1]

```
Indentation is key. Get that wrong and it won't work. Indentation is part of the YAML standard, which does make it suck.
Run these commands after making updates. You'll need to get the correct device, IP, gateway, subnets, nameservers, etc.:
```
sudo netplan generate
sudo netplan apply --debug
```
Don't even attempt to use DHCP. It won't end well.

---

