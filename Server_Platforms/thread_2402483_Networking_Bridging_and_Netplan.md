---
title: "Networking Bridging and Netplan"
date: 2018-09-30
forum: Server Platforms
---

### Post by mcuciti on 2018-09-30
Hello all and thank you in advance for any assistance you can give. Here is my setup. 

Headless ubuntu server running 18.04.1. Mostly used for file server and as a kvm host. I am attempting to get my kvm guest boxes to connect directly to my network and get DHCP from my DHCP server on my network. My understanding is that in order to do this I will have to setup bridge networking using Netplan. I am attempting to get my /etc/netplan/*.yaml file configured as follows:

```

network:
version: 2
renderer: networkd
ethernets:
     enp2s0:
        dhcp4: false
bridges:
    br0:
        interfaces: [enp2s0]
        dhcp4: true
```

When I have this setup I can see my computer pull two addresses from my DHCP server. (makes sense, one for the bridge and one for the machine itself) however the computer is not accessible on either of those two addresses. In addition I can not ping out from that computer (attached a screen a KB for troubleshooting purposes). When attempting to ping out I get a "no destination to host" error. 

Can anyone shine some light on this issue for me? Happy to provide additional details as needed.

---

### Post by darkod on 2018-10-01
I don't know if you lost some blank spaces during the copy-paste, or your yaml file is identical to what you posyed. Because if it is identical, you need the network: line to start more to the left (all the rest is indented compared to network:).

Here is my file, note that I use static IP like I recommend any server to have, otherwise our files are quite similar.

```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp4s0:
      dhcp4: false
      dhcp6: false

  bridges:
    br0:
      interfaces: [ enp4s0 ]
      dhcp4: false
      dhcp6: false
      addresses: [ 192.168.1.5/24, 192.168.2.5/24 ]
      gateway4: 192.168.2.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]
```

---

### Post by Marconijholt on 2019-04-26
I don't want to dig up old horses, but i'm experiencing the exact same issue on ubuntu 18.04.2

My normal config is:
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            dhcp4: no
            dhcp6: no
            addresses: [192.168.1.20/22]
            gateway4: 192.168.1.1
            nameservers:
                addresses: [1.1.1.1, 1.0.0.1]


My bridge config is:
network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            dhcp4: no
            dhcp6: no
    bridges:
        br0:
            interfaces: [eno1]
            dhcp4: no
            dhcp6: no
            addresses: [192.168.1.20/22]
            gateway4: 192.168.1.1
            nameservers:
                addresses: [1.1.1.1, 1.0.0.1]



And the end result is, server not reachable, cant ping outwards from it, gets a server not reachable from 192.168.1.20.

the following info is my ifconfig. As you can see br0 has a ip assigned from dhcp, which it shouldnt. eno1 still has the 1.20 ip even tho br0 should now have it.

[IMG]https://i.imgur.com/pusIxL3.jpg[/IMG]


The chipset for the ethernet adapter is I219-V and is installed with the e1000e driver. 

Reboots don't have affect, even the very basic example config from [https://netplan.io/examples#bridging](https://netplan.io/examples#bridging) does not work, the br0 interface even gets 2 ip addresses from dhcp. 

Does anyone have any idea?

---

### Post by Tadaen_Sylvermane on 2019-04-26
I know nothing about netmasks. Why are you using 22 instead of the usual 24 for 192.168.1.*. That may be your problem. Notice your broadcast as well. Totally on the wrong subnet. Maybe a result of netmask? I don't know. That would likely be the issue. Another thing, yaml files are very specific about indentation from my research. Single spaces, not tabs. I never got it to work with anything else.

My servers working netplan config for a bridge. I also totally disable the 50-cloud yaml that the server comes with installed. Change it's name to 50-cloud.yaml.orig or something. 

```
network:
 version: 2
 renderer: networkd
 ethernets:
  enp2s0:
   dhcp4: false
   dhcp6: false
 bridges:
  br0:
   dhcp4: false
   dhcp6: false
   interfaces: [enp2s0]
   addresses: [192.168.1.2/24]
   gateway4: 192.168.1.1
   nameservers:
    addresses: [192.168.1.20]
```

Sources: [https://www.tecmint.com/configure-network-static-ip-address-in-ubuntu/](https://www.tecmint.com/configure-network-static-ip-address-in-ubuntu/)
[https://askubuntu.com/questions/971126/17-10-netplan-config-with-bridge](https://askubuntu.com/questions/971126/17-10-netplan-config-with-bridge)

---

