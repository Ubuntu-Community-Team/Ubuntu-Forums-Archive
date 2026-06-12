---
title: "About set up Static IP on LAMP server"
date: 2023-01-23
forum: Virtualisation
---

### Post by satimis on 2023-01-23
Hi all,

I followed below document to set up Static IP on a LAMP server running on Ubuntu 22.04 VM (VituralBox)

Setting Up Static IP Address on Ubuntu 22.04 LTS
[https://itslinuxfoss.com/setting-up-static-ip-address-ubuntu-22-04/](https://itslinuxfoss.com/setting-up-static-ip-address-ubuntu-22-04/)
Method 1: Set up Static IP Address Using Command Line

Host - Ubuntu 22.04 desktop

The installation was not so straightforwards.  Finally I figured out the problem encountered.  Now Host can ping VM and VM can ping Host.

On Host browser running [VM_Fixed_IP] it starts "Apache2 Default Page" it works!

But I can't resolve
1) On Host
$ ip a```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 04:d9:f5:7d:0e:40 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.164/24 metric 100 brd 192.168.1.255 scope global dynamic enp4s0
       valid_lft 4330sec preferred_lft 4330sec
    inet6 fe80::6d9:f5ff:fe7d:e40/64 scope link 
       valid_lft forever preferred_lft forever

```

Bridge Adapter
Name:  enp4s0

2)
On VM
$ ip a```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:56:96:e3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.161/32 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet 192.168.1.167/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 4396sec preferred_lft 4396sec
    inet6 fe80::a98e:1f06:7c77:fce/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

Bridge Adapter
Name:  enp0s3

They are not the same.

On VM Manager
Settings -> Networks
Bridge Adapter
Name: [enp4s0 ]

Is it correct?  Thanks

Regards

---

### Post by MAFoElffen on 2023-01-23
Please post the netplan .yaml files of both the host and the VM... Separately.

Why is it that you say you have a birdge adaptr configured for both the host (enp4s0) and the VM (enp0s3)? Am I confused about reading that?

---

### Post by satimis on 2023-01-23
> **MAFoElffen said:**
> Please post the netplan .yaml files of both the host and the VM... Separately.

Why is it that you say you have a birdge adaptr configured for both the host (enp4s0) and the VM (enp0s3)? Am I confused about reading that?
Hi,

**[COLOR="#FF0000"]Host[/COLOR]**
$ cat /etc/netplan/01-network-manager-all.yaml```
 
# Let NetworkManager manage all devices on this system
network:
# version: 2
# renderer: NetworkManager
    ethernets:
        enp4s0:
            addresses: []
            dhcp4: true
    version: 2

```

**[COLOR="#FF0000"]VM[/COLOR]**
cat /etc/netplan/01-network-manager-all.yaml```
 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  
```
  
On Vertual Machine Manager
Settings -> Network
Adapter 1
   Attached to: [Bridge Adapter  ]
          Name: [enp4s0  ]
          
But on VM Terminal
$ ip a > ip.txt
$ cat ip.txt```

.....
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:56:96:e3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.161/32 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet 192.168.1.167/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
...
...
```

2: enp0s3

Please refers to ip.txt file attached.

Regards

---

### Post by MAFoElffen on 2023-01-23
> **satimis said:**
> Hi,

**Host**
```

$ cat /etc/netplan/01-network-manager-all.yaml

```
```
 
# Let NetworkManager manage all devices on this system
network:
[COLOR=#FF0000]#[/COLOR] version: 2
[COLOR=#FF0000]#[/COLOR] renderer: NetworkManager
    ethernets:
        enp4s0:
            addresses: [COLOR=#FF0000][][/COLOR]
            [COLOR=#FF0000]dhcp4: true[/COLOR]
    [COLOR=#ff0000]version: 2[/COLOR]

```

**VM**
```

cat /etc/netplan/01-network-manager-all.yaml

```
```
 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  
```
  
On Virtual Machine Manager
Settings -> Network
Adapter 1
   Attached to: [Bridge Adapter  ]
          Name: [enp4s0  ]
          
But on VM Terminal
$ ip a > ip.txt
$ cat ip.txt```

.....
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:56:96:e3 brd ff:ff:ff:ff:ff:ff
    inet [COLOR=#FF0000]192.168.1.161/32[/COLOR] scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet [COLOR=#FF0000]192.168.1.167/24 [/COLOR]brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
...
...
```

2: enp0s3

Please refers to ip.txt file attached.

Regards
What catches my eyes is "Highlighted in red"... Before I start on that... Remind me. Your VM Host system is VirtualBox?

---

### Post by satimis on 2023-01-23
> **MAFoElffen said:**
> Highlighted in red... Remind me. Your VM Host system is VirtualBox?
Yes, correct.

---

### Post by MAFoElffen on 2023-01-23
Okay... Neither of those are setting a static address persistently. In fact, your hosts has conflicting information that just might confuse it. The guide your followed (Setting a static address from command line) would set a static address temporarily, that would not survive any reboot...

Do you need help setting a persistent static address? On the Host? VM? Or both?

---

### Post by MAFoElffen on 2023-01-23
Host:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses: 
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

VM:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```
On each after the file updates:
```

sudo netplan generate
sudo netplan apply

```

---

### Post by satimis on 2023-01-23
> **MAFoElffen said:**
> Okay... Neither of those are setting a static address persistently. In fact, your hosts has conflicting information that just might confuse it. The guide your followed (Setting a static address from command line) would set a static address temporarily, that would not survive any reboot...

Do you need help setting a persistent static address? On the Host? VM? Or both?
Both, thanks

This is not my first time setting static IP on Ubuntu.  I have long experience setting static IP on Ubuntu 18.04 and 20.04 in the past.  I can't realize why it is so difficult for me on Ubuntu 22.04.

Similarly I also have encountered problem building LAMP server on Ubuntu 22.04.  But neither I have problem building LAMP server on Ubuntu 20.04 in the past.

Regards

---

### Post by satimis on 2023-01-23
> **MAFoElffen said:**
> Host:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses: 
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

VM:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```
On each after the file updates:
```

sudo netplan generate
sudo netplan apply

```
Thanks

I suppose those are the content of /etc/netplan/01-network-manager-all.yaml ?

According to my recollection on Ubuntu 20.04 I didn't use netplan.  I worked in a different way

Regards



Regards

---

### Post by TheFu on 2023-01-23
> **satimis said:**
>  According to my recollection on Ubuntu 20.04 I didn't use netplan.  I worked in a different way

Netplan use began sometime after 18.04.  If you upgraded from 18.04 to 20.04, it is possible the old method was pulled forward and you had a mixed system with some 20.04 subsystems and some 18.04 subsystems.  This is confusing to you and anyone trying to help.

Netplan files don't have any mandate for names, except they need to end in .yaml and be in the correct directory. They are processed in alphabetical order.  I use a different netplan file for each interface which is usually tied to a different subnet.

For example:
```
$ ls /etc/netplan/
enp3s0-static-config.yaml
enp7s0f0-SAN-static-config.yaml
enp7s0f1-mgnt-static-config.yaml.disable

```
I like descriptive names.

01-network-manager-all.yaml as a name wouldn't be what I used, but I purge network-manager off all my systems.  If you change the renderer to not be network manager, then that file name would be a lie and confusing.  For some reason, I thought that if going static, the renderer needed to be networkd. I could be wrong.

BTW, static IPs are fine for the host, but you'll probably want to configure a bridge to be used by the VMs, right?  That's does in the YAML too. Oh ... you're using vbox. Forget what I've said.  I have no good experience using vbox on Linux hosts.

---

### Post by MAFoElffen on 2023-01-23
@TheFu - Agreed

I waited for him to remind me and confirm that he is using VBox. VirtualBox does bridges 'internally' in it's own remappings kind of way. I figured that is why we don't see it.

I also remember he is using LAMP and even though he says Server, is using GUI. I remember and have been seeing his posts... Trying to fit the pieces together of what he is trying to do..

Of late, I know he was having problems accessing his web pages... Thus, the static addresses.

@satimis- In 22.04... In testing QA for 23.04, I'm still using NetPlan. Please explain how you think networking works in 22.04. 

It could be done 4 ways, and variations of each, just off the top of my head. But you would have to make it work, and would take extra work, to do those. NetPlan is already in place. I recommended based on what you have in place. With the renderer you have in place.

---

### Post by satimis on 2023-01-24
> **TheFu said:**
> Netplan use began sometime after 18.04.  If you upgraded from 18.04 to 20.04, it is possible the old method was pulled forward and you had a mixed system with some 20.04 subsystems and some 18.04 subsystems.  This is confusing to you and anyone trying to help.

Netplan files don't have any mandate for names, except they need to end in .yaml and be in the correct directory. They are processed in alphabetical order.  I use a different netplan file for each interface which is usually tied to a different subnet.

For example:
```
$ ls /etc/netplan/
enp3s0-static-config.yaml
enp7s0f0-SAN-static-config.yaml
enp7s0f1-mgnt-static-config.yaml.disable

```
I like descriptive names.

01-network-manager-all.yaml as a name wouldn't be what I used, but I purge network-manager off all my systems.  If you change the renderer to not be network manager, then that file name would be a lie and confusing.  For some reason, I thought that if going static, the renderer needed to be networkd. I could be wrong.

BTW, static IPs are fine for the host, but you'll probably want to configure a bridge to be used by the VMs, right?  That's does in the YAML too. Oh ... you're using vbox. Forget what I've said.  I have no good experience using vbox on Linux hosts.
Thanks for your advice.

Just start Ubuntu 20.04 on another SSD drive of this PC.  

$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers 218.102.32.172  219.76.98.90

# The primary network interface
auto enp0s3
iface enp0s3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.1.164
        network         192.168.1.0
        netmask         255.255.255.0
        broadcast       192.168.1.255
        gateway         192.168.1.1
        bridge_ports    enp0s3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

In the past I just created this file to set Static IP on Ubuntu 20.04 VM (VirtualBox), not running NetPlan

Regards

---

### Post by TheFu on 2023-01-24
/etc/network/interfaces was deprecated before 20.04.  The tools underneath, known as ifupdown have NOT been maintained since 2011.

Updated:  s/ipupdown/ifupdown/
Just goes to show why doing LTS-to-LTS upgrades can be problematic. The system ends up in a mix setup for any subsystems left behind.  I remember the first time I got netplan working with bridges ... was in the fall of 2020.  Could have been my ignorance or bugs in the handling. Hard to know.  To me, seems that methods that were supported 6 months ago in netplan are being deprecated as all the new examples have a "via" command in the routing that was never necessary previously.  I can see where that is necessary.  

Just wish some other subsystems (snaps and lxd) were getting some user-focused solutions too.

---

### Post by MAFoElffen on 2023-01-24
I think the last time I used that file / format was in 16.04 LTS... The transition was in 18.04LTS. By 20.04LTS, 2 of the packages were gone to be able to continue using /etc/network/interfaces...

---

### Post by satimis on 2023-01-25
> **MAFoElffen said:**
> @TheFu - Agreed

I waited for him to remind me and confirm that he is using VBox. VirtualBox does bridges 'internally' in it's own remappings kind of way. I figured that is why we don't see it.

I also remember he is using LAMP and even though he says Server, is using GUI. I remember and have been seeing his posts... Trying to fit the pieces together of what he is trying to do..

Of late, I know he was having problems accessing his web pages... Thus, the static addresses.

@satimis- In 22.04... In testing QA for 23.04, I'm still using NetPlan. Please explain how you think networking works in 22.04. 

It could be done 4 ways, and variations of each, just off the top of my head. But you would have to make it work, and would take extra work, to do those. NetPlan is already in place. I recommended based on what you have in place. With the renderer you have in place.
Hi,

VirtualBox - Alread advied on #5

Change Host .yaml as advised

$ cat /etc/netplan/01-network-manager-all.yaml```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses:
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

$ sudo netplan generate
$ sudo netplan apply
No complaint

$ ifconfig shows: inet 192.168.1.164 

Today the 1st time starting this PC, PC couldn't connect Internet.  Before booting the PC, the indictor light of the LAN socket on the motherboard is on.  After booting finished the indicator light is off.  

Hardware connection:
FTTH optic fibre
-> Optical fibre modem -> Router -> PC

$ sudo ufw status
Status: inactive

This Router works on another Ubuntu 22.04 PC without problem.  After having checked all hardware and software I found the problem comes from .yaml file.

Now I change it back to its original file.

$ cat /etc/netplan/01-network-manager-all.yaml```

# Let NetworkManager manage all devices on this system
network:
    ethernets:
        enp4s0:
            addresses: []
            dhcp4: true
    version: 2

```

$ ifconfig ```

enp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.164  netmask 255.255.255.0  broadcast 192.168.1.255
.....
.....
```

Now PC can connect Internet without problem.

Regards

---

### Post by MAFoElffen on 2023-01-25
Either go through the Network Manager GUI and set the config to stacticand fill out the fields, apply

Or Change the renderers on both from NetworkManager to networkd... with the configs I provided, albiet the renderer changed.
then 
```

snap set network-manager defaultrenderer=false

```

Here is mine from 2 of my 4 KVM Hosts:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
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
    enp4s0:
      dhcp4: false
      dhcp6: false
      optional: yes

  bridges:
    br0:
      interfaces: [enp4s0]
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

mafoelffen@opti-ubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:25:90:83:c0:52 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.5/8 brd 10.255.255.255 scope global enp3s0
       valid_lft forever preferred_lft forever
    inet6 2601:603:1f80:6dd0::9a7f/128 scope global dynamic noprefixroute 
       valid_lft 307711sec preferred_lft 307711sec
    inet6 2601:603:1f80:6dd0:225:90ff:fe83:c052/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 300sec preferred_lft 300sec
    inet6 fe80::225:90ff:fe83:c052/64 scope link 
       valid_lft forever preferred_lft forever
3: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether 00:25:90:83:c0:53 brd ff:ff:ff:ff:ff:ff
4: wlp5s1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:f6:52:46:b7:67 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.209/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp5s1
       valid_lft 172486sec preferred_lft 172486sec
    inet6 2601:603:1f80:6dd0::62ec/128 scope global dynamic noprefixroute 
       valid_lft 307724sec preferred_lft 307724sec
    inet6 2601:603:1f80:6dd0:ccee:4be2:975a:1850/64 scope global temporary dynamic 
       valid_lft 301sec preferred_lft 301sec
    inet6 2601:603:1f80:6dd0:5c5:38a0:7568:41e8/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 301sec preferred_lft 301sec
    inet6 fe80::aecf:1205:a595:6c4a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether a6:5e:15:92:7a:cd brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.6/8 brd 10.255.255.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 2601:603:1f80:6dd0::c5cf/128 scope global dynamic noprefixroute 
       valid_lft 307720sec preferred_lft 307720sec
    inet6 2601:603:1f80:6dd0:a45e:15ff:fe92:7acd/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 300sec preferred_lft 300sec
    inet6 fe80::a45e:15ff:fe92:7acd/64 scope link 
       valid_lft forever preferred_lft forever
6: virbr3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:1a:63:ed brd ff:ff:ff:ff:ff:ff
    inet 192.168.120.1/24 brd 192.168.120.255 scope global virbr3
       valid_lft forever preferred_lft forever
7: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:04:a1:8b brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
8: virbr2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:4b:30:6d brd ff:ff:ff:ff:ff:ff
    inet 192.168.130.1/24 brd 192.168.130.255 scope global virbr2
       valid_lft forever preferred_lft forever
9: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:ba:65:30 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.1/24 brd 192.168.100.255 scope global virbr1
       valid_lft forever preferred_lft forever

mafoelffen@Mikes-B460M:~$ cat /etc/netplan/01-network-manager-all.yaml
# Let networkd manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp2s0:
      addresses:
        - 10.0.0.3/8
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4, 1.1.1.1]
      routes:
        - to: default
          via: 10.0.0.1
          metric: 100
          on-link: true
      dhcp4: false
      dhcp6: false
      optional: yes

mafoelffen@Mikes-B460M:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 18:c0:4d:3f:4d:d5 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.3/8 brd 10.255.255.255 scope global noprefixroute enp2s0
       valid_lft forever preferred_lft forever
    inet6 2601:603:1f80:6dd0:604e:6d0b:9cf1:c93a/64 scope global temporary dynamic 
       valid_lft 298sec preferred_lft 298sec
    inet6 2601:603:1f80:6dd0:1ac0:4dff:fe3f:4dd5/64 scope global dynamic mngtmpaddr 
       valid_lft 298sec preferred_lft 298sec
    inet6 fe80::1ac0:4dff:fe3f:4dd5/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 58:a0:23:dc:fd:ca brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.229/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 89755sec preferred_lft 89755sec
    inet6 2601:603:1f80:6dd0::ba04/128 scope global dynamic noprefixroute 
       valid_lft 225011sec preferred_lft 225011sec
    inet6 2601:603:1f80:6dd0:9a45:d86f:80db:c269/64 scope global temporary dynamic 
       valid_lft 299sec preferred_lft 299sec
    inet6 2601:603:1f80:6dd0:fb52:5f69:1c5d:a252/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 299sec preferred_lft 299sec
    inet6 fe80::d973:71a9:69bb:3517/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: virbr2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:8b:ee:f3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.0/24 brd 192.168.1.255 scope global virbr2
       valid_lft forever preferred_lft forever
5: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:ff:9b:ed brd ff:ff:ff:ff:ff:ff
    inet 172.16.10.1/24 brd 172.16.10.255 scope global virbr1
       valid_lft forever preferred_lft forever
6: virbr0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 52:54:00:89:e2:31 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
14: vnet7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master virbr0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:66:b9:a7 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe66:b9a7/64 scope link 
       valid_lft forever preferred_lft forever


```

---

### Post by satimis on 2023-01-25
Hi MAFoElffen,

Whether you suggest on .yaml file
change;
  renderer: NetworkManager
to:
  renderer: Network
?

Also I tested VM, it go problem as well.  I'm now trying to sort it out if possible

Regards

---

### Post by satimis on 2023-01-25
Hi MAFoEffen.

According to your revised posting #16

1)
> 
Either go through the Network Manager GUI and set the config to stacticand fill out the fields, apply

Pls advise which document shall I follow?

2)
> 
Or Change the renderers on both from NetworkManager to networkd... with the configs I provided, albiet the renderer changed.
then ......

After editing .yaml file

Perform;
$ sudo netplan generate
$ sudo netplan apply

Then;
$ sudo set network-manager defaultrenderer=false
??

Regards

---

### Post by MAFoElffen on 2023-01-25
Lets start with the VM. That way you can work out what works for you before correcting your host....

```

sudo snap set network-manager defaultrenderer=false

```

Then your Netplan file:
```

# Static Config file for satimis'es VM
network:
  version: 2
  renderer: networkd
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

```

sudo netplan generate
sudo netplan apply

```
Does it work?

And if it doesn't... Lets take this step by step to get it to work... By asking and resolving one thing at a time.

---

### Post by satimis on 2023-01-25
> **MAFoElffen said:**
> Lets start with the VM. That way you can work out what works for you before correcting your host....

```

sudo snap set network-manager defaultrenderer=false

```

Then your Netplan file:
```

# Static Config file for satimis'es VM
network:
  version: 2
  renderer: networkd
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

```

sudo netplan generate
sudo netplan apply

```
Does it work?
Performed following steps

$ sudo snap set network-manager defaultrenderer=false
[sudo] password for satimis: ```

error: snap "network-manager" not found

```

$ cat /etc/netplan/01-network-manager-all.yam```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes 
        
```

$ sudo netplan generate
$ sudo netplan apply
Both no complaint

$ ifconfig```

enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.161  netmask 255.255.255.255  broadcast 0.0.0.0
        inet6 fe80::a98e:1f06:7c77:fce  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:56:96:e3  txqueuelen 1000  (Ethernet)
        RX packets 635  bytes 342766 (342.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 424  bytes 49505 (49.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 212  bytes 16810 (16.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 212  bytes 16810 (16.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Host can ping VM on 192.168.1.161

I can't resolve how the Stactic IP = 192.168.1.161 ?

If I expect setting it = 192.168.1.171
Then How ?

Regards

---

### Post by MAFoElffen on 2023-01-25
First, stop using 'ifconfig'... It has been deprecated for years. Instead use what it was deprecated to
```

ip a

```
Then for your Nameservers:
```

sudo nano /etc/systemd/resolved.conf

```
Change 
```

#DNS=

```
to 
```

DNS=8.8.8.8 1.1.1.1 4.4.4.4

```
Then
```

sudo ln -rsf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf 
sudo systemctl restart systemd-resolved 

```

---

### Post by satimis on 2023-01-25
> **MAFoElffen said:**
> First, stop using 'ifconfig'... It has been deprecated for years. Instead use what it was deprecated to
```

ip a

```
Then for your Nameservers:
```

sudo nano /etc/systemd/resolved.conf

```
Change 
```

#DNS=

```
to 
```

DNS=8.8.8.8 1.1.1.1 4.4.4.4

```
Then
```

sudo ln -rsf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf 
sudo systemctl restart systemd-resolved 

```
Performed steps as advised and went through without complaint

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.1.161/32 scope global noprefixroute enp0s3
    inet 192.168.1.116/24 brd 192.168.1.255 scope global dynamic noprefixroute enp0s3
    inet6 fe80::a98e:1f06:7c77:fce/64 scope link noprefixroute 

```

$ sudo snap set network-manager defaultrenderer=false```

error: snap "network-manager" not found

```
The network-manager on Ubuntu 22.04 repo has been installed, not snap package

$ apt policy network-manager```

network-manager:
  Installed: 1.36.6-0ubuntu2
  Candidate: 1.36.6-0ubuntu2
  Version table:
 *** 1.36.6-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.36.4-2ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
If to change Static IP to **[COLOR="#FF0000"]192.168.1.171[/COLOR]** how to do it ?  Thanks

Can I perform the same steps on Host to set Static IP ?

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Something strange happens after rebooting VM

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 

```

Do I need to remove repo network-manager and install snap network-manage package ?


Regards

---

### Post by MAFoElffen on 2023-01-25
Since the 'snap set' is not finding NetworkManager in snap core20, do:
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd.service
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service

```

---

### Post by #&amp;thj^% on 2023-01-25
> **MAFoElffen said:**
> Since the 'snap set' is not finding NetworkManager in snap core20, do:
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd.service
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service

```
+1 +1 +1

---

### Post by satimis on 2023-01-25
> **MAFoElffen said:**
> Since the 'snap set' is not finding NetworkManager in snap core20, do:
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd.service
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service

```
$ sudo systemctl stop NetworkManager
No complaint
$ sudo systemctl stop NetworkManager
No complaint
sudo systemctl disable NetworkManager```

Unit /etc/systemd/system/NetworkManager.service is masked, ignoring.

```

$ sudo systemctl stop NetworkManager
$ sudo systemctl stop NetworkManager
$ sudo systemctl stop NetworkManager
$ sudo systemctl start systemd-networkd.service
All without complait

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 

```
Still the same

---

### Post by satimis on 2023-01-25
> **1fallen said:**
> +1 +1 +1
What did you suggest ?

---

### Post by MAFoElffen on 2023-01-25
And on reboot, does it come up with the static addressing?

If not, then do (again) so it builds against the correct system pieces
```

sudo netplan generate
sudo netplan apply 
sudo reboot

```

---

### Post by satimis on 2023-01-26
> **MAFoElffen said:**
> And on reboot, does it come up with the static addressing?
No, unable to connect Internet.

$ ip a```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 08:00:27:5d:c6:94 brd ff:ff:ff:ff:ff:ff

```

> 
If not, then do (again) so it builds against the correct system pieces
```

sudo netplan generate
sudo netplan apply 
sudo reboot

```
I have tried them before you post without result.  Now I tried it again and the result is identical to as before.

$ sudo netplan generate```

[sudo] password for satimis: 
/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```

Even deleting all : (colon) on .yaml file without result.  The only solution is to delete your suggested content.

The problem encountered on the VM is identical to the problem on the Host reported in my previous  posting

Regards

---

### Post by MAFoElffen on 2023-01-26
WhiteSpace and Indentation is important in .yaml files... You have to count all the spaces and do no use any tabs.
[quote=satimisThe problem encountered on the VM is identical to the problem on the Host reported in my previous  posting][/quote]
You say that is just like before? Where did you tell anyone that? You didn't. You said there were no complaints.

---

### Post by satimis on 2023-01-26
> **MAFoElffen said:**
> WhiteSpace and Indentation is important in .yaml files... You have to count all the spaces and do no use any tabs.
I copy&paste your suggested content on .yaml file.  I have tested it on 3 Ubuntu VMs with similar result

> 
You say that is just like before? Where did you tell anyone that? You didn't. You said there were no complaints.
on #15 above;
I said the same situation as I set Static IP on Host.  After reboot Host can't connect Internet

Without complaint - I meant no complaint popup on running that command

Regards

---

### Post by satimis on 2023-01-26
Hi MAFoElffen,

Further to my previous posting

Problem encountered below;

sudo netplan generate
[sudo] password for satimis: ```

/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```
According to my recollection.  The above problem happens only after rebooting the VM/Host

Pls refers to my posting #15
$ sudo netplan generate
$ sudo netplan apply
No complaint

Regards

---

### Post by MAFoElffen on 2023-01-26
From #5:
[quote=satimis]
Change Host .yaml as advised

$ cat /etc/netplan/01-network-manager-all.yaml
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses:
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

$ sudo netplan generate
$ sudo netplan apply
No complaint

$ ifconfig shows: inet 192.168.1.164
[/quote]
Since Post #5, you have changed Network Manager to networkd....

In Post #25 you took other actions, to correct snap core20 not finding NetworkManager to be able to set rendering from it to false... That is all that I can think of that would change that on reboot.

But now, instead of "no complaints" on sudo netplan generate, you get an error on your whitespace/identation.  This is a different error, caused by you. Please correct that so that the yaml file is valid. If you do not do that, then any further instruction is fruitless. You need to be able to follow instructions for this to work.

---

### Post by satimis on 2023-01-27
Hi MAFoElffen,,

Sorry, I'm now confused because there are many postings on this thread, already Page-4.

Let me to make it clear first before proceeding further ;
1)
On #7 - P-1
You advised me to setup the Host Static IP

Host:
Code:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses: 
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

Then run each command after the file updates:
Code:```

sudo netplan generate
sudo netplan apply

```

Remark:
Your advice works without problem before rebooting the PC

2)
On #15 P-2
I reported on posting that I tested your code and steps on Host and it worked without problem.

$ sudo netplan generate
$ sudo netplan apply
No complaint (no warning popup)

$ inet 192.168.1.164 (Static IP)

Remark: I haven't reboot the PC

But on next day, starting PC, Host couldn't connect Internet.  Finally I figured the problem out.
(remark: I'm not going to repeat the problem and solution here.  Pls refers to my posting)

3)
On #19 P-2
You gave me further advice and suggested testing it on VM first.

> 
Lets start with the VM. That way you can work out what works for you before correcting your host....


I have tried on 3 VMs according to your advice with following result;
3a)
The steps works seamlessly.  I could set Static IP

3b)
After reboot all VMs unable to connect Internet.  I have to delete your code on .yaml file and reboot VM.  Then VM can connect Internet again.

That is the present situation

Regards

---

### Post by MAFoElffen on 2023-01-27
If it works, but doesn't after a reboot, then I consider it a failure and not working... That is why we are on post #33. I feel it should have taken about 3-4 posts.

I want this to work for you. If we tell you to do something. and it doesn't work... And you instantly back off all the changes (instead of fixing it from there), then all of a sudden you are completely back to square #1 again.

That makes sense to you, right?

I have machines using both Network Manager or networkd with static addresses. To me, it's easy and not a big deal. Your machines are having difficulties, so we adjusted to just use networkd, where static addressing is used most often. And still(???)

Lets get this done and behind us. Get it working consistently, and reliably on your VM... Then you can follow the same steps to take care of it on your host.

---

### Post by satimis on 2023-01-27
> **MAFoElffen said:**
> If it works, but doesn't after a reboot, then I consider it a failure and not working... That is why we are on post #33. I feel it should have taken about 3-4 posts.

I want this to work for you. If we tell you to do something. and it doesn't work... And you instantly back off all the changes (instead of fixing it from there), then all of a sudden you are completely back to square #1 again.

.........
Hi,

Sorry, #33 above is my reply to you.

To make it simple avoiding confusion, please advise what you expect me to try again?  According to which # number ?

Thanks

Regard

---

### Post by satimis on 2023-01-27
Hi MAFoElffen,

I solved the problem by performing following steps;

Static IP of VM - 192.168.1.168

The content of .yaml file;
$ cat /etc/netplan/01-network-manager-all.yaml```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
     dhcp4: false
     addresses: [192.168.1.168/24]
     routes:
      - to: default
        via: 192.168.1.1
     nameservers:
       addresses: [8.8.8.8,8.8.4.4]

```

$ sudo netplan apply
No warning

$ ip a```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:5d:c6:94 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.168/24 brd 192.168.1.255 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe5d:c694/64 scope link 
       valid_lft forever preferred_lft forever

```

Static IP 192.168.1.168 set

On browser run 192.168.1.168
"Apache2 Default Page" started

Host can ping 192.168.1.168

Reboot VM
Still connect Internet

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.1.168/24 brd 192.168.1.255 scope global enp0s3
    inet6 fe80::a00:27ff:fe5d:c694/64 scope link 

```

I'll try another Ubuntu22.04 VM first before proceeding to edit the Host.

Regards

---

### Post by MAFoElffen on 2023-01-27
Lets document all on your VM, so you have it for your host...

Your /yaml file:
```

# Static Config file for satimis'es VM
network:
  version: 2
  renderer: networkd
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```
Or change to the IP address to whatever you want...
```

sudo netplan generate
sudo netplan apply

```
Then you already have done for your Nameservers:
     ```

sudo nano /etc/systemd/resolved.conf

```
Change
```

#DNS=

```
To
```

DNS=8.8.8.8 1.1.1.1 4.4.4.4

```
Then
```

sudo ln -rsf /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
sudo systemctl restart systemd-resolved 

```
Then you did
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd.service
sudo systemctl enable systemd-networkd.service
sudo systemctl start systemd-networkd.service

```
Then 
```

sudo reboot

```
On reboot
```

ip a

```
That is doing static IP while converting Network Manager to networkd rendering...

---

### Post by satimis on 2023-01-27
Hi MAFoElffen,

Lot of thanks for your detailed advice.  I'll try it on all my VMs later.

DNS:
8.8.8.8 and 8.8.4.4
google nameserver

What are the DNS:
1.1.1.1  4.4.4.4  127.0.0.53
???

Regards

---

### Post by satimis on 2023-01-27
Hi MAFoElffen,

After having perfomed the steps on #36 above, following actions were done automatically.

$ ls -al /etc/resolv.conf ```

lrwxrwxrwx 1 root root 39 Jan 26 05:33 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

```

$ cat /etc/systemd/resolved.conf```

....
# Quad9:      9.9.9.9#dns.quad9.net 149.112.112.112#dns.quad9.net 2620:fe::fe#dns.quad9.net 2620:fe::9
#dns.quad9.net
DNS=8.8.8.8 1.1.1.1 4.4.4.4
.....

```

Regards

---

### Post by satimis on 2023-01-28
Hi MAFoElffen,

I have an Ubuntu 22.40 VM (LAMP stack installed) here with Static IP set up some time before.  I can't recall how to set the Static IP on this VM.

Also I have 2 websites migrated on this VM.  Host can browse the websites on their IPs

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

$ ip a | grep inet```

    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
    inet 192.168.1.160/24 brd 192.168.1.255 scope global noprefixroute enp0s3
    inet6 fe80::c9c2:963f:dd97:9c8a/64 scope link noprefixroute 

```

$ cat /etc/netplan/01-network-manager-all.yaml ```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```

$ sudo ls /etc/network/```

if-down.d  if-post-down.d  if-pre-up.d  if-up.d

```

No /etc/network/interfaces file created.

Could you please help me to find out how the Static IP being set here?

Thanks

Regards

---

### Post by MAFoElffen on 2023-01-28
For Network Manager, one other place to look... Look in: Settings > Network > Wired > Geared Icon > IPV4 Tab >  IPv4 Method = Manual > Addresses...

It stores it connections in /etc/NetworkManager/system-connections/. The first wire Connection is named: /etc/NetworkManager/system-connections/'Wired connection 1.nmconnection' and looks like this:
```

[connection]
id=Wired connection 1
uuid=c0ec6f1f-ee71-3050-a9cf-8d49310297f8
type=ethernet
autoconnect-priority=-999
interface-name=enp0s25
timestamp=1653779584

[ethernet]
mac-address=3C:97:0E:07:B8:DF

[ipv4]
address1=10.0.0.20/32,10.0.0.1
dns=1.1.1.1;1.0.0.1;8.8.8.8;8.8.4.4;
ignore-auto-dns=true
method=manual

[ipv6]
addr-gen-mode=stable-privacy
method=auto

[proxy]

```
The Open DNS addresses:
Google Public DNS: 8.8.8.8, 8.8.4.4
Cloudflare: 1.1.1.1, 1.0.0.1
Level 3 Communications: 4.4.4.4
Cisco OpenDNS: 208.67.222.222, 208.67.220.220
DNS Watch: 84.200.69.80, 84.200.70.40
OpenNIC: 206.125.173.29, 45.32.230.225
UncensoredDNS: 91.239.100.100, 89.233.43.71

---

### Post by satimis on 2023-01-28
> **MAFoElffen said:**
> For Network Manager, one other place to look... Look in: Settings > Network > Wired > Geared Icon > IPV4 Tab >  IPv4 Method = Manual > Addresses...

It stores it connections in /etc/NetworkManager/system-connections/. The first wire Connection is named: /etc/NetworkManager/system-connections/'Wired connection 1.nmconnection' and looks like this:
```

[connection]
id=Wired connection 1
uuid=c0ec6f1f-ee71-3050-a9cf-8d49310297f8
type=ethernet
autoconnect-priority=-999
interface-name=enp0s25
timestamp=1653779584

[ethernet]
mac-address=3C:97:0E:07:B8:DF

[ipv4]
address1=10.0.0.20/32,10.0.0.1
dns=1.1.1.1;1.0.0.1;8.8.8.8;8.8.4.4;
ignore-auto-dns=true
method=manual

[ipv6]
addr-gen-mode=stable-privacy
method=auto

[proxy]

```
The Open DNS addresses:
Google Public DNS: 8.8.8.8, 8.8.4.4
Cloudflare: 1.1.1.1, 1.0.0.1
Level 3 Communications: 4.4.4.4
Cisco OpenDNS: 208.67.222.222, 208.67.220.220
DNS Watch: 84.200.69.80, 84.200.70.40
OpenNIC: 206.125.173.29, 45.32.230.225
UncensoredDNS: 91.239.100.100, 89.233.43.71
$ ls -al /etc/NetworkManager/system-connections/```

total 12
drwxr-xr-x 2 root root 4096 Jan 19 20:30  .
drwxr-xr-x 7 root root 4096 Aug  9 19:51  ..
-rw------- 1 root root  311 Jan 19 20:30 'Wired connection 1.nmconnection'

```

$ sudo cat /etc/NetworkManager/system-connections/Wired\ connection\ 1.nmconnection | grep add```

address1=192.168.1.160/24,192.168.1.1
addr-gen-mode=stable-privacy

```

Now, I got it.  Thanks

What is the DNS for 127.0.0.53 ???

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Can I change its IP running

On
/etc/NetworkManager/system-connections/Wired\ connection\ 1.nmconnection | 

Change;
address1=192.168.1.160/24,192.168.1.1

To:
address1=192.168.1.180/24,192.168.1.1

Then run;
$ sudo netplan generate
$ sudo netplan apply

???

---

### Post by satimis on 2023-01-28
> **MAFoElffen said:**
> Lets document all on your VM, so you have it for your host...

Your /yaml file:
```

# Static Config file for satimis'es VM
network:
  version: 2
  renderer: networkd
    ethernets:
      enp0s3:
        addresses: 
          - 192.168.1.167/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```
Or change to the IP address to whatever you want...
```

sudo netplan generate
sudo netplan apply

```
Then you already have done for your Nameservers:
     ```

sudo nano /etc/systemd/resolved.conf

```
Change ........
..
Hi

Just tested your advice.

Steps performed;
1)
Clone an Ubuntu 22.04 LAMP server VM

2)
On the new Ubuntu 22.04 LAMP server VM

Edit /etc/netplan/xxx.yaml
Change its IP from 192.168.1.160/24
To: 192.168.1.170/24

Save and exit

3)
On Terminal run;
$ sudo netplan generate
$ sudo netplan apply

$ ip a | grep inet```

....
192.168.1.170
....

```

Its IP changed.  Wonderful !!!

Now I can create many new Ubuntu 22.04 LAMP server VMs as I need.

Thanks again for your advice.

Regards

Remark: reboot without problem.

---

### Post by MAFoElffen on 2023-01-28
127.0.0.53 points to systemd.resolved: [https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53](https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53)

---

### Post by satimis on 2023-01-28
> **MAFoElffen said:**
> 127.0.0.53 points to systemd.resolved: [https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53](https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53)
I see;```

/run/systemd/resolve/stub-resolv.conf tells DNS client libraries to send their queries to 127.0.0.53. This is where the systemd-resolved process listens for DNS queries, which it then forwards on.

```

Thanks

Regards

---

### Post by satimis on 2023-02-08
Hi MAFoElffen,

I'm unable to set Static IP for the Host

$ cat 01-network-manager-all.yaml_20230125```
 
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
    ethernets:
      enp4s0:
        addresses:
          - 192.168.1.164/24
        nameservers:
          addresses: [127.0.0.53, 8.8.8.8, 1.1.1.1]
        routes:
          - to: default
            via: 192.168.1.1
        dhcp4: false
        optional: yes

```

$ sudo netplan generate```

/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```

$ sudo netplan apply```

/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```

I must set /etc/netplan/01-network-manager-all.yaml as```

network:
# version: 2
# renderer: NetworkManager
    ethernets:
        enp4s0:
            addresses: []
            dhcp4: true
    version: 2

```

Please help.  Thanks

Regards

---

### Post by MAFoElffen on 2023-02-09
It told you exactly what was wrong and where
```

/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```
Check you indention and spacing to ensure it is correct and consistent.

---

### Post by satimis on 2023-02-09
> **MAFoElffen said:**
> It told you exactly what was wrong and where
```

/etc/netplan/01-network-manager-all.yaml:5:14: Invalid YAML: inconsistent indentation:
    ethernets:
             ^

```
Check you indention and spacing to ensure it is correct and consistent.
Sorry, no.  I copied and pasted the complete content from posting on /etc/netplan/applications/.yaml

I encountered this warning before on setting Static IP on VM.  Finally I figured out changing NetwordManager to networkd then the warning gone and Static IP set.  This is a wrong warning.

I can't imagine encountering such difficulties in set up Static IP via NetPlan.  I'm not a beginner.

This is a new 2TB NVMe PCIe 3.0 SSD drive, with Ubuntu 22.04 freshly installed, about 2 weeks ago.  I have another 1TB NVMe PCIe 3.0 SSD drive in this PC, with Ubuntu 22.04 running.  I can't remember exactly whether it was upgraded from Ubuntu 20.04.  VBox is also running.  Static IP of Host and VMs are set via "interfaces" "if-up" "if-down" etc.  It works without  problem.

Also I have another 500G SATA3 SSD drive, with KVM running on Ubuntu 22.04 as Host.  The Static IPs of Host and all guests are set via "interfaces" "if-up" "if-down" etc.  It also works without  problem.

Regards

---

### Post by satimis on 2023-02-09
Hi MAFoElffen,

Further to my previous posting.

I have tried the suggestion on following URL

How to Configure Static IP Address on Ubuntu 22.04
[https://tecadmin.net/how-to-configure-static-ip-address-on-ubuntu-22-04/](https://tecadmin.net/how-to-configure-static-ip-address-on-ubuntu-22-04/)
Method 2: 
Configuring Static IPv4 Address on Ubuntu 22.04 Server with CLI

/etc/netplan/.yaml```

network:
    version: 2
    renderer: networkd
    ethernets:
        eth0:
            addresses:
                - 192.168.1.164/24
            nameservers:
                addresses: [8.8.8.8, 8.8.4.4]
            routes:
                - to: default
                  via: 192.168.1.1
                  
```

Internet can be conneted but "ip a" shows Static IP_ 192.168.1.165 not .164.

It is very strange to me.

Regards

---

### Post by MAFoElffen on 2023-02-10
Please post:
```

sudo cat /etc/NetworkManager/system-connections/*

```
Why? Becuase in that same last post, you talked about doing both networkd and Network Manager...

---

### Post by satimis on 2023-02-10
> **MAFoElffen said:**
> Please post:
```

sudo cat /etc/NetworkManager/system-connections/*

```
Why? Becuase in that same last post, you talked about doing both networkd and Network Manager...
Hi,

It is very strange to me.

Now I'm unable to boot this 2TB NVMe SSD drive.  BIOS detects it. But booting it, it always boots the 1TB NVMe SSD drive.

If removing the 1TB NVMe SSD from the PC, booting 2TB NVMe SSD drive drops to GRUB.

I don't know how to fix the problem.

Other drives;
500G SSD - Ubuntu 22.04 KVM
1TB SSD - Windows 11
can be booted without problem.

Pls help.  How to fix the problem?  Thanks

Regards

---

### Post by MAFoElffen on 2023-02-10
Not sure what you did or might have done. It was not connected on what I posted on needed output on a Network Manager config...

Start a new thread (In the General Section) on not booting. Run boot-repair report and post the boot-info report url. Do not do a repair.

---

### Post by satimis on 2023-02-10
> **MAFoElffen said:**
> Not sure what you did or might have done. It was not connected on what I posted on needed output on a Network Manager config...

Start a new thread (In the General Section) on not booting. Run boot-repair report and post the boot-info report url. Do not do a repair.
Thanks for your advice.

I would wide-out this 2TB NVMe SSD drive and reinstall Ubuntu 22.04

Regards

---

### Post by MAFoElffen on 2023-02-10
> **satimis said:**
> Thanks for your advice.

I would wide-out this 2TB NVMe SSD drive and reinstall Ubuntu 22.04

Regards

??? That is not what I said nor advised.

---

### Post by DuckHook on 2023-02-10
> **MAFoElffen said:**
> ??? That is not what I said nor advised.
Greetings MAFoElffen

OP is juggling multiple issues on multiple threads. Though not a direct consequence of postings on this thread, I believe his OS is too far jumbled through a history of attempted/aborted fixes to untangle and a reinstall in his case may be best.

I advised him of such on another thread. He doesn't refer to it, which renders his posting here confusing.

---

### Post by MAFoElffen on 2023-02-11
@DuckHook

LOL. Understood now. Yes. He has gone back and forth and done "a lot" of things... Which some things conflict with other things. A fresh install and he can do "what worked" and be better off.

---

