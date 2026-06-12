---
title: "KVM - Guest VM has no network connectivity"
date: 2021-03-09
forum: Virtualisation
---

### Post by Alan5127 on 2021-03-09
Hi All,

I am trying to get a Debian 10 VM up and running in the KVM-Host (running on Ubuntu Server 20.04.2 LTS)

I believe I have all the necessary packages installed on the KVM-Host machine:

```
KVM-Host$ sudo apt install --dry-run bridge-utils qemu-kvm libvirt-daemon-system

Reading package lists... Done
Building dependency tree       
Reading state information... Done

bridge-utils is already the newest version (1.6-2ubuntu1).
libvirt-daemon-system is already the newest version (6.0.0-0ubuntu8.7).
qemu-kvm is already the newest version (1:4.2-3ubuntu6.14).

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

For the avoidance of doubt, there is no WiFi involved at any point, only ethernet NICs - the KVM-Host machine, my desktop, and the router (that is running DHCP service and is the default gateway) are all connected to a switch via ethernet cable.

I created a network bridge:

```
KVM-Host$ virsh iface-list

 Name   State    MAC Address
------------------------------------
 br0    active   de:c3:29:25:ea:2f
 eno1   active   de:c3:29:25:ea:2f
 eno2   active   de:c3:29:25:ea:2f

```

```
KVM-Host$ brctl show

bridge name    bridge id        STP enabled    interfaces
br0        8000.dec32925ea2f    no        bond0
                            vnet0

```

I note that both the VM Guest's 'vnet0' interface and the KVM-Host's 'bond0' interface are connected to the br0 bridge - I am inferring that this means that they should be talking to each other?


```
KVM-Host$ ip route

default via 172.25.25.254 dev br0 proto static 
172.25.25.0/24 dev br0 proto kernel scope link src 172.25.25.3 

```

```
KVM-Host$ ip address show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether de:c3:29:25:ea:2f brd ff:ff:ff:ff:ff:ff
3: eno2: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master bond0 state UP group default qlen 1000
    link/ether de:c3:29:25:ea:2f brd ff:ff:ff:ff:ff:ff
4: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0 state UP group default qlen 1000
    link/ether de:c3:29:25:ea:2f brd ff:ff:ff:ff:ff:ff
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether de:c3:29:25:ea:2f brd ff:ff:ff:ff:ff:ff
    inet 172.25.25.3/24 brd 172.25.25.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::f0f3:b3ff:fe26:2cc9/64 scope link 
       valid_lft forever preferred_lft forever
11: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:1b:f4:e1 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe1b:f4e1/64 scope link 
       valid_lft forever preferred_lft forever

```

I note that 'vnet0' is in an 'UNKNOWN' state - not sure if that is the issue, and if so, what I do to address it?


```
KVM-Host$ virsh net-dumpxml host-bridge

<network>
  <name>host-bridge</name>
  <uuid>a07efbb0-aa83-435e-a4ad-93b2303cad21</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>

```

This is the network interface section from the VMGuest machine description in /etc/libvirt/qemu/Debian10-Test.xml  (I have tried changing the model type from 'virtio' to 'e1000', and 'rtl8139' (all options) - none make any difference.

```
<interface type='bridge'>
      <mac address='52:54:00:1b:f4:e1'/>
      <source bridge='br0'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x09' slot='0x01' function='0x0'/>
    </interface>
```



```
KVM-Host$ brctl showmacs br0

port no    mac addr        is local?    ageing timer
  1    00:15:62:20:14:41    no           1.46
  1    00:21:70:4d:ad:4f    no           0.00
  1    00:80:0f:b0:3f:1e    no          72.52
  1    00:d9:d1:f5:e9:b0    no           8.98
  1    28:80:23:12:e9:16    no           9.85
  1    34:31:c4:2f:ac:09    no           0.04
  1    52:54:00:1b:f4:e1    no           0.04
  1    6c:ad:f8:fd:9b:55    no          30.68
  1    84:2b:2b:a1:b2:1a    no           9.34
  1    84:2b:2b:a3:5b:42    no          75.13
  1    90:f6:52:f8:af:98    no           9.44
  1    a8:13:74:72:d4:69    no         129.83
  1    d4:53:83:b3:96:0f    no           5.64
  1    de:c3:29:25:ea:2f    yes           0.00
  1    de:c3:29:25:ea:2f    yes           0.00
  1    e8:2a:44:c1:ce:b3    no         208.79
  2    fe:54:00:1b:f4:e1    yes           0.00
  2    fe:54:00:1b:f4:e1    yes           0.00

```

The MAC listed above as '52:54:00:1b:f4:e1' is the same as you see in Virt-Manager - Debian10-Test - Info Screen - NIC - MAC Address

Not sure if required, but IPv4 forwarding is enabled:

```
KVM-Host$ cat /proc/sys/net/ipv4/ip_forward

1
```


I have created the VM using this command:

```
virt-install --name Debian10-Test --description "Debian10-Test" --virt-type kvm --memory 2048 --vcpus 2 --hvm --cpu host --cdrom /media/D_Data/VM/Media/debian-10.8.0-amd64-netinst.iso --disk path=/media/D_Data/VM/KVM/Debian10-Test.qcow2,bus=virtio,size=20,format=qcow2 --noautoconsole --graphics spice --network bridge:br0 --os-variant debian10
```


The VM appears to be created fine, and I can connect to it from my desktop (Ubuntu Desktop 18.04 LTS) using Virt-Manager.

When I run the VM, it boots up into the Debian 10 install as it would if I did it on bare metal, but when it gets to the DHCP configuration, the VM shows:

> Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively the DHCP server may
be slow or some network hardware is not working properly,

I have disabled the KVM-Host firewall to see if that helps, but it made no difference:

```
KVM-Host$ sudo ufw status

Status: inactive

```


There is no issue with DHCP elsewhere in the LAN, and I can communicate between the KVM Server and my Desktop no problem, so there is no general network issue that I can see (other than, possibly, the 'vnet0' item mentioned above).

If I try entering the network config manually (I used 172.25.25.102/24 which is guaranteed not being used, and confirmed via my router), it gets to a 'page' saying:

> Detecting link on ens1

then asks for a hostname and other config.

that appears to work fine, and it installs.  I can login, but it is not actually connected - I cannot ping in or out, ssh into it etc.


Any suggestions are welcome.

Thanks,

Alan.

---

### Post by TheFu on 2021-03-10
Simplify and test.  That's my only advice after over 20 yrs doing virtualization.
Is this a debian-only issue or does the bridge not work for other VMs too?

I've never used virt-install.  Always setup VMs using virt-manager.
I don't have a 20.04 VM host and have never setup bridging using netplan either.
Bridging with ifupdown on 16.04 and 18.04 work well.  I don't use bonding either. NICs and switch ports just don't fail that often, IME.

Sorry, I'm not any help.

---

### Post by Alan5127 on 2021-03-11
Hi TheFu,
> **TheFu said:**
> Simplify and test.  That's my only advice after over 20 yrs doing virtualization.

Sounds like good advice!


> **TheFu said:**
> Is this a debian-only issue or does the bridge not work for other VMs too?

It is on other VMs too - I decided to test using Debian, since I usually find that to be one of the simplest and most bullet proof OSs, so I figured if that didn't work, it would imply the issue is with something I have mis-configured and / or not configured at all..


> **TheFu said:**
> I've never used virt-install.  Always setup VMs using virt-manager.

I tried it using virt-manager first, and encountered the same issue, so I figured as there is more potential to miss something, or click on the wrong thing (or fail to click on something) in a GUI, I would try using virt-install, but that gives the same result.

I also thought it would be easier to post here asking for help, giving the command as that is easy to see exactly what I have done.  It was my first time with virt-install!


> **TheFu said:**
> I don't have a 20.04 VM host and have never setup bridging using netplan either.
Bridging with ifupdown on 16.04 and 18.04 work well.

I had thought that it made most sense to use 20.04 LTS for a new KVM-Host, since it pushes out the day I have to bite the bullet and move to a new version!  My desktop is on 18.04 LTS, and I would not update that until around Jan 2023, at which time I will go to 22.04 LTS.  I am a conservative in that respect.

Perhaps I was naive, but I thought that 20.04 having been out for a year nearly, and on sub-version 2 (20,04.2) it would have any significant wrinkles ironed out by now, but I may have been wrong.

Finding that /etc/network/interfaces is no longer with us was a bit of a shock (been using that for longer than I care to remember), and I certainly don't feel so confident with NetPlan yet, but I'm sure it will come.

I am however thinking that I might wipe my Ubuntu Server 20.04 LTS KVM-Host, and start with a fresh Ubuntu Server 18.04 LTS KVM-Host, and see if that works.  It *feels* like a big deal, but I have rock solid documentation of how I set it up, so I should be able to replicate in an hour or so (albeit I will have to re-write for /etc/network/interfaces of course!)

That will be a weekend project I think.


> **TheFu said:**
>  I don't use  bonding either. NICs and switch ports just don't fail that often, IME.

If I scrub 20.04, then I won't bond the interfaces - that will, as you suggested above, simplify things, and you are right - I don't recall having a NIC fail on me for a very long time, perhaps since the nineties!


> **TheFu said:**
> Sorry, I'm not any help.

Quite the opposite - just having someone else, metaphorically at least, walking along with me is quite a lot of help!


Thanks,

Alan.

---

### Post by ajgreeny on 2021-03-11
Did your VMs have a network connection previously or are they all new.

I have 5 different VMs using KVM/QEMU and at one point yesterday they all lost network connections.  My host was Xubuntu 20.04 with a wireless network connection which was still good on the host but all my VMs lost connection even though using NAT, not bridged network connections.
Like TheFu I use virt-manager

I wondered if the update of linux-firmware package was the culprit so rebooted the host and immediately all VM network was back up and running.

I realise this is a different situation to yours with me using NAT connections to a WiFi host but perhaps this is something to consider.  I attempted to change to bridged connections before rebooting just in case it worked, but as has always been my experience using KVM, that failed.

Do you ned bridged connections or would NAT be good for whatever use you make of the VMs?

---

### Post by TheFu on 2021-03-11
I'd think 20.04 was ready, and netplan is one of the few changes for sake of change that I actually like.  But not enough to jump in full speed with non-test hardware.  [https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629](https://ubuntuforums.org/showthread.php?t=2444748&p=13962629#post13962629) should have an example of a Bridged + Bonded KVM netplan.  I've been capturing posts with specific netplan solutions for some time. I knew there'd be a day when I needed the examples.

I've had a realtek NIC (on the MB) fail in the last few years. Fortunately, I have cheap spare GigE NICs from around 2005 that don't come close to GigE, but 350 Mbps isn't too bad for what the system needs to accomplish.  In newer systems, I a NIC bigot - Intel only with known-to-work drivers.  Some of the really new Intel chips aren't supported by Linux, so beware if that is your situation.  The new 2.5Gbps stuff has been problematic for about a year since it started showing up in motherboards.

But I would start with a simple bridge first, get that working. Only then would I'd add complexity.

All the stuff you did seems like something I would do, if I hadn't been carefully watching for issues the last year.  I prefer to avoid problems.  I do have 1 20.04 system - it is a KVM guest. There are some things that haven't worked too well with it.  Mainly spice performance with using any DE (I use fvwm which flies on spice) and the required storage ballooned from my prior release - about 2x more is needed for the OS. I had to add more storage within a few months of installing 20.04. Previously, that system had been running on half the storage since 2010 with upgrades along the way.

All my bridges are manually created, not part of libvirt's install.  I only use NAT for throw-away VMs.

---

### Post by ajgreeny on 2021-03-11
My VMs are all what you would probably call "throw-away" as I use them only to check different Linux distros and not for any specific uses.

For me NAT makes total sense; for your uses it may not be good enough, eg, if you're running a server of some sort on it you probably need bridged network in order to get third party connections to it to work reliably.

---

