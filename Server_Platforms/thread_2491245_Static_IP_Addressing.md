---
title: "Static IP Addressing"
date: 2023-10-01
forum: Server Platforms
---

### Post by linuxlearner77 on 2023-10-01
Apologies if this has been asked before, but nothing turned up when I used the search function.

I am setting up pihole on my server (OS is Ubuntu Sever). However, I need to set a static IP to my pihole VM. Are there any reputable guides on how to do this for a beginner?

Thanks.

---

### Post by MAFoElffen on 2023-10-02
Using search functions:
[https://ubuntuforums.org/search.php?searchid=29748407](https://ubuntuforums.org/search.php?searchid=29748407)
[https://ubuntuforums.org/search.php?searchid=29748408](https://ubuntuforums.org/search.php?searchid=29748408)
[https://tecadmin.net/setup-static-ip-address-on-ubuntu-using-netplan/](https://tecadmin.net/setup-static-ip-address-on-ubuntu-using-netplan/)

Many times. Search works to find many examples. In fact...
```

mafoelffen@msi-ubuntu:~$ grep . /etc/netplan/00-installer-config.yaml
# This is the custom network config written by MAFoElffen
network:
  version: 2
  renderer: networkd
  ethernets:
    enp6s0:
      dhcp4: false
      dhcp6: false
      addresses:
          - 10.0.0.5/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      routes:
          - to: default
            via: 10.0.0.1
            metric: 100
            on-link: true
      mtu: 1500
## Begin SR-IOV on enp7s0f0 
    enp7s0f0:
      virtual-function-count: 7
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v0:
      link: enp7s0f0
      addresses:
          - 10.0.0.10/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v1:
      link: enp7s0f0
      addresses:
          - 10.0.0.11/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v2:
      link: enp7s0f0
      addresses:
          - 10.0.0.12/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v3:
      link: enp7s0f0
      addresses:
          - 10.0.0.13/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v4:
      link: enp7s0f0
      addresses:
          - 10.0.0.14/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v5:
      link: enp7s0f0
      addresses:
          - 10.0.0.15/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
    enp7s0f0v6:
      link: enp7s0f0
      addresses:
          - 10.0.0.16/8
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
      dhcp4: false
      dhcp6: false
      optional: yes
## End SR-IOV on enp7s0f0
## Begin Bridge on enp7s0f1
    enp7s0f1:
      dhcp4: false
      dhcp6: false
      optional: yes
  bridges:
    br0:
      interfaces: [enp7s0f1]
      addresses: [10.0.0.6/8]
      routing-policy:
         - from: 10.0.0.6
           table: 10
      # ** ADDITIONAL ROUTING POLICY **
         - to: 172.16.1.0/24
           table: 172
      # *******************************
      routes:
         - to: 0.0.0.0/0
           via: 10.0.0.1
           table: 10
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1, 1.0.0.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no
      optional: yes
## End Bridge on enp7s0f1

```
This is mine from my workstation...

Device names found by doing
```

ip a

```
Use the device names from your own output... 

Do this to find the filename of thw file you need to update
```

ls /etc/netplan/*.yaml

```
Use this, substituting your filename
```

sudo vi /etc/netplan/your_filename.yaml

```
Then, after editing, saving and exiting the file, do this to generate and apply the changes
```

sudo netplan generate
sudo netplan apply

```
I, personally prefer to use networkd as my renderer instead of using NetworkManager... There is osme soomds you would need to do, if switching from one to the other to switch using different renderer daemons... networkd is the defau;t renderer for Server Edition. NetworkManager is the default renderer for Desktop Edition.

---

### Post by TheFu on 2023-10-02
> **linuxlearner77 said:**
> Apologies if this has been asked before, but nothing turned up when I used the search function.

I am setting up pihole on my server (OS is Ubuntu Sever). However, I need to set a static IP to my pihole VM. Are there any reputable guides on how to do this for a beginner?

Thanks.

I put piholes into LXC container which are about 10x lighter than a full VM.
$ more /etc/netplan/[COLOR="#FF0000"]01-eth0-static.yaml[/COLOR] network:
```
    version: 2
    renderer: networkd
    ethernets:
      [COLOR="#FF0000"]eth0[/COLOR]:
        addresses:
            - [COLOR="#FF0000"]172.22.22.81/24
[/COLOR]        dhcp4: false
        dhcp6: false
        routes:
          - to: default
            via: [COLOR="#FF0000"]172.22.22.1[/COLOR]
        optional: true
        nameservers:
           addresses: [[COLOR="#FF0000"] "1.1.1.1", "1.0.0.1"[/COLOR] ]
           search: [[COLOR="#FF0000"]example.foo example.com[/COLOR]]
```

Change for your specific needs. I'll make those red.
Then run **netplan generate/apply** cycle.

My piholes are on Ubuntu 22.04.3 currently, using far too much storage at 2.5G.
```
$ dft
Filesystem             Type           Size  Used Avail Use% Mounted on
lxd/containers/pihole2 zfs             32G  2.5G   30G   8% /
```
But it is better than most "lite" VMs.

---

### Post by linuxlearner77 on 2023-10-02
> **MAFoElffen said:**
> Using search functions:
[https://ubuntuforums.org/search.php?searchid=29748407](https://ubuntuforums.org/search.php?searchid=29748407)
[https://ubuntuforums.org/search.php?searchid=29748408](https://ubuntuforums.org/search.php?searchid=29748408)
[https://tecadmin.net/setup-static-ip-address-on-ubuntu-using-netplan/](https://tecadmin.net/setup-static-ip-address-on-ubuntu-using-netplan/)

Many times. Search works to find many examples. In fact...


Thanks for the information. The first two searches you have above say "Sorry - no matches. Please try some different terms", which is what I often got when tried searching the forums. 

In any event, I followed this [guide]("https://coygeek.com/docs/pihole-ubuntu/"), and ended up setting up the static IP address upon installation of Ubuntu server. My current server is just a a flat network (i.e., one PC with a bunch of VMs, a router as AP, and ISP modem/router). I picked Google as my upstream DNS servers (for now), disabled my ISP DHCP, enabled Pi-Hole's etc, etc. Here is my .yaml file:
```

network:
    ethernets:
      ens18:
        addresses:
        - 192.168.2.11/24
        nameservers:
           addresses:
            - 192.168.2.1
            search: []
         routes:
         - to: default
            via: 192.168.2.1
    version: 2
```
**Note**: I had to manually type that out so my spaces may be off.

It is very different from yours, but everything is seemingly working OK. Looking at this again, I think there is a mistake in the addresses line though. I have pihole handing out IPs from 192.168.2.10 to 192.168.2.254. So, I should probably change the addresses line to 192.168.2.10/24 (not x.x.x.11/24)?

Probably unrelated, but the only problem I am having is that when I input commands (e.g., hostname -f), I get this:
```
Name or service not known

```

My hostname is ubuntu202310. However,

My hostname in /etc/hostname does show ubuntu_202310 and in /etc/hosts there is:
```

127.0.0.1 localhost
127.0.1.1 ubuntu_202310
```

So obviously that is not right. I am assuming I should just pick one (i.e., ubuntu_202310 or ubuntu202310) and make those files consistent. 
I am also assuming I should change the ip address for the server name from 127.0.1.1 to 127.0.0.1 too?


> **TheFu said:**
> I put piholes into LXC container which are about 10x lighter than a full VM.

My piholes are on Ubuntu 22.04.3 currently, using far too much storage at 2.5G.
```
$ dft
Filesystem             Type           Size  Used Avail Use% Mounted on
lxd/containers/pihole2 zfs             32G  2.5G   30G   8% /
```
But it is better than most "lite" VMs.

Absolutely. But I am noob, so I'll probably stick to VMs for now :) I appreciate your response though, and will revist it when I get better at virtualization.

---

### Post by TheFu on 2023-10-02
Static IPs need to be outside the range that the DHCP dynamic IPs are provided.  I typically retain .1 - .99 for static IPs on my /24 subnets and limit DHCP dynamic IPs to be 2x the highest number of devices that will ever be on the network. I consider having too many available IPs to be leased a security hole.  None of the normal devices inside the house get dynamic IPs. They either have static IPs assigned or the DHCP server does reservations ... providing static IPs in the .1 - .99 range.  

Dynamic IPs are just for guest devices, so just people visiting and their devices.  They are actually placed onto a different subnet, not the same ones that I use for my stuff ... which are also separate for servers, desktops, and wifi stuff. That's 3 different subnets that the guests cannot access. Guests are on a wifi network outside the 3 subnets our stuff is on.

As for VMs or Containers being easier.  With LXD doing the management for the containers, it is much easier.  I treat my LXD/LXC containers like they are physical systems.  They get patched weekly. They have static IPs. They just use far fewer resources and don't have any GUI, but most of my VMs are servers and don't have any GUI either.  Basically, they are the same.  Now, if you decide to run some other container type - like Docker - then many of the rules change. But not with LXD/LXC containers.

Using a VM is 100% fine too. I use both and spun up my first VM in the late 1990s.  In the last 5 yrs, my VM/Container ratio as drastically changed.  It was about 12:0 and not it is about 6:7.  That's 6 full VMs and 7 linux containers. Basically it comes down to security considerations. VMs can more easily handle firewall rules and adding specific kernel modules. Containers don't do those things well ... or we have to break the main security provision that these containers provide to let them load kernel drivers or do firewalls.

The 127.0.x.x IPs aren't important.  Any in the 127.x.x.x/8 subnet can be used. Doesn't matter, except that 1 is needed and that is typically 127.0.0.1. These are "localhost" and just for intra-system socket protocols.  Nobody outside the system can access those IPs.  Find a network calculator online.  Plug in "127.0.0.1/8" and read the 10 lines it puts out.  There are some neat things that are possible thanks to this little network trick that works on every computing device with IPv4.

> I have pihole handing out IPs from 192.168.2.10 to 192.168.2.254. So, I should probably change the addresses line to 192.168.2.10/24 (not x.x.x.11/24)?
Don't confuse DHCP information and DNS information.  DNS is completely separate.  If it was me, I'd set the DHCP range to be .200 - .220 and leave this IP as .10.

Also, if you ever plan to run a VPN server at home to allow yourself remote access, I wouldn't use 192.168.2.x/24 as a subnet.  It is a little too common.  192.168.77.x/24 is uncommon and much less likely to have conflicts.  Neither really matter, unless you run a VPN server or need to connect to a work VPN and their subnet matches yours. Then you will be screwed.  These "private subnets" won't be routed over the internet, so it won't matter at all to commercial VPN services.  Having a unique, private subnet at home just avoids possible issues in the future.

This is the sort of information that nobody tells you, especially the network segmentation aspects.

---

### Post by linuxlearner77 on 2023-10-02
Ah, thank you for the reply. I assume I had set everything up correctly (minus the poor segmentation). I will make the change to the etc/hostname and etc/hosts files and that would probably solve that minor issue then.

I am starting to learn about this nebulous world in my off time for fun, so I appreciate the insight! I have a long way to go lol.

---

### Post by TheFu on 2023-10-03
> etc/hostname and etc/hosts

On all OSes, don't know why people from MS-Windows didn't learn this, but on all OSes, there's a huge difference between an absolute path like "/etc/hosts"
and
a relative path like "etc/hosts".

Please learn the difference. BTW, you want absolute paths more of the time.  Relative paths are useful relative only to some known directory, usually $HOME, but sometimes the `pwd`.

When you write etc/hosts ... that's relative and I don't have enough information to know which directory you actually mean. It is unlikely your `pwd` is /, so do you mean $HOME/etc/hosts?  See why I'm confused?

Too fill in some basic knowledge, work through the first 250 or so pages of this book [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

---

