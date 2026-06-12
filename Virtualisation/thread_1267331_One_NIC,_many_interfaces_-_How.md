---
title: "One NIC, many interfaces - How?"
date: 2009-09-15
forum: Virtualisation
---

### Post by Gustavo Narea on 2009-09-15
Hello,

I'm going to host several KVM virtual machines on a single computer (which has just one NIC), and each guest should have its own IP address (and the host should have its own address too). How can I do this?

Below is my attempt in */etc/network/interfaces* on the host machine:
```
auto lo                                     
iface lo inet loopback                      


auto br0
iface br0 inet static
    bridge_ports eth0 tap0
    address 192.168.1.150
    netmask 255.255.255.0

auto br1
iface br1 inet static
    bridge_ports eth0 tap1
    address 192.168.1.151
    netmask 255.255.255.0


auto tap0
iface tap0 inet manual
    tunctl_user gustavo

auto tap1
iface tap1 inet manual
    tunctl_user gustavo


auto eth0
iface eth0 inet manual
    dns-nameservers 192.168.1.1
    gateway 192.168.1.1
    up    ip link set $IFACE promisc on
    down  ip link set $IFACE promisc off
```

But when I run "sudo /etc/init.d/networking restart", I get:
```
 * Reconfiguring network interfaces...                                                                                                                       
Waiting for br0 to get ready (MAXWAIT is 32 seconds).                                                                                                        
 * if-up.d/mountnfs[br0]: waiting for interface br1 before doing NFS mounts                                                                                  
 * if-up.d/mountnfs[br0]: waiting for interface tap0 before doing NFS mounts                                                                                 
 * if-up.d/mountnfs[br0]: waiting for interface tap1 before doing NFS mounts                                                                                 
 * if-up.d/mountnfs[br0]: waiting for interface eth0 before doing NFS mounts                                                                                 
**device eth0 is already a member of a bridge; can't enslave it to bridge br1.**                                                                                

Waiting for br1 to get ready (MAXWAIT is 32 seconds).
 * if-up.d/mountnfs[br1]: waiting for interface tap0 before doing NFS mounts
 * if-up.d/mountnfs[br1]: waiting for interface tap1 before doing NFS mounts
 * if-up.d/mountnfs[br1]: waiting for interface eth0 before doing NFS mounts
Set 'tap0' persistent and owned by uid 1000                                 
 * if-up.d/mountnfs[tap0]: waiting for interface tap1 before doing NFS mounts
 * if-up.d/mountnfs[tap0]: waiting for interface eth0 before doing NFS mounts
Set 'tap1' persistent and owned by uid 1000                                  
 * if-up.d/mountnfs[tap1]: waiting for interface eth0 before doing NFS mounts
                                                                                                                                                      [ OK ]
```

br0 (192.168.1.150) and br1 (192.168.1.151) seem to work, because I can access the host machine with either IP address.

What's the correct way to do it?

Thanks in advance!

---

### Post by scrooge_74 on 2009-09-15
What you made was trying to tie a single nic to several virtual ones, I went through that same problem a while back using qemu. I think that set up works the other way around.


 I think the way to go is tun tap devices, since I changed to VirtualBox it handles that by itself when I give the Virtual Machines the bridged option and then tell them the name of the real net card. After setting the tun tap device when ever a virtual machine fired up the system would take care of making a virtual ethernet that would hook up to my real one so router would assign IPs

---

### Post by xOrphenochx on 2009-09-18
I have mine like this. And if you're using virt-manager too, make sure that all of the vnetworks are deleted when making these changes, it's caused problems for me. With this KVM server ends up getting the 10.1.1.1 address. I've ran atleast 5 machines at once doing this. As long as you have one bridged connection, you should be fine, but since you have 2, that's probably the reason you're getting that error message. 

```
# The loopback network interface
auto lo
iface lo inet loopback 

# The primary network interface
auto eth0
iface eth0 inet dhcp

#KVM Bridged Networking
auto br0
iface br0 inet static
        address 10.1.1.1
        netmask 255.0.0.0
        gateway 10.0.0.1
        bridge_ports eth0
```

---

### Post by Terc on 2009-10-19
Here's how I'm doing it - and it's working, but I have a 32 second pause during startup.

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
bridge_ports eth0 eth1 eth2 eth3
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
```


Also, for my routing, I have some iptables to enable, so after broadcast, I have:
```
pre-up iptables-restore < /etc/iptables.rules
```

When I do a networking restart, I get "Waiting for br0 to get ready (MAXWAIT is 32 seconds).
I'm sure there's some way to reduce the maxwait, just not sure where to change it at.

---

