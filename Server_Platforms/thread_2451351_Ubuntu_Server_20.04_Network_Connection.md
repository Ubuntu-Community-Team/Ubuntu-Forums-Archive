---
title: "Ubuntu Server 20.04 Network Connection"
date: 2020-10-02
forum: Server Platforms
---

### Post by Dii_Reno on 2020-10-02
After deploying my installation onto a 2TB drive the /etc/network/interfaces file shows as completely empty. ip link show shows the interface in a down state.. i'm guessing due to the installer not configuring the interface file. Is this normal, or is this a bug known or unknown.

---

### Post by TheFu on 2020-10-02
/etc/network/interfaces is deprecated since 17.10 or so.  Use netplan to configure server networking.
The _ubuntu server guide_ explains. [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)

---

### Post by ameinild on 2020-10-04
Netplan also have some good examples on the website for basic configuration: [https://netplan.io/examples/](https://netplan.io/examples/)

---

### Post by TheFu on 2020-10-04
> **ameinild said:**
> Netplan also have some good examples on the website for basic configuration: [https://netplan.io/examples/](https://netplan.io/examples/)

True. And since around Feb 2020, they actually work. ;)

Netplan uses a file format called YAML - Yet Another Markup Language.  It is space and tab sensitive, but human readable.  Either use all spaces or all tabs for the indentations. Do not mix. Doing mixed files will only cause problems, though it shouldn't, in theory.

I keep a few simple examples in my notes so I don't need to search and wonder what works anymore.

After any changes, 2 commands must be run:
```
sudo netplan generate
sudo netplan apply --debug
```

Not that the **bold** NIC device names and IPs/subnets will be different for your setup.

```
# #################################
#   [ for dhcp - tested]
network:
  version: 2
  renderer: networkd
  ethernets:
    **enxc0335eee724f**:
      dhcp4: true
      dhcp6: false
```

```
# #################################
#   [ for static - tested]
network:
    version: 2
    renderer: networkd
    ethernets:
        **ens3**:
            addresses:
            - 172.22.22.90/24
            dhcp4: false
            dhcp6: false
            gateway4: 172.22.22.1
            nameservers:
                addresses: [ "1.1.1.1", "1.0.0.1" ]
                search: []
```

For KVM + bridged but with DHCP IPs for the hostOS, 
[https://ubuntuforums.org/showthread.php?t=2443548&p=13961621#post13961621](https://ubuntuforums.org/showthread.php?t=2443548&p=13961621#post13961621)

For KVM + bridged but with static IP for the hostOS, 
[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)

For bridged and bonded NICs for KVM, 
[https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629](https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629)

I have some example links for LXD and VLAN tagged too.
# #################################
#   [ for bridge + static - lxd ]
[https://lxadm.com/Bridge_with_a_static_IP_with_netplan](https://lxadm.com/Bridge_with_a_static_IP_with_netplan)
I know that the KVM + bridge + static can be used with LXD. That's how I do it.

To have a valid Netplan, create a file in /etc/netplan/.
I like to use something like 01-ens3-static.yaml for the name, though it shouldn't matter as long as the filename ends in .yaml.  If I wanted DCHP on a different subnet, I'd create another file 02-ens4-dhcp.yaml just for clarity. The filename template is : {unique-number}-{network device}-{static|dhcp}.yaml

My most complex network setups are still using 16.04 as the OS, so I only have a few netplan systems. Netplan wasn't the default until 17.10, so 18.04 and 20.04 both use netplan.  About a year ago, I did an 18.04 Server install and the generated netplan file didn't work.  I did another 18.04 install last Feb and it did. I almost cried with happiness. The issue could have been user error because the 18.04 installer network setup page wasn't clear. I didn't go through it 10 times to figure out the issue.  With 20.04, a new installer with a new network data page is included. On 18.04, there's an option to use the new installer, which I always accept now. With the new installer, I've not had network setup problems. I always setup static IPs for any system that isn't portable.

After any changes and running those 2 commands at the top, it might be necessary to have systemctl restart networking too. I don't recall.

Indentation must be consistent and as shown.  The only way to share that information correctly in these forums is to use "code tags". Those are in the advanced editor here.

Anyway, hope this is helpful.

---

