---
title: "Ping Ubuntu 22.04 Desktop to Virtual Machine Manager 4.0.0 VM Destination Host Unreac"
date: 2023-06-03
forum: Virtualisation
---

### Post by kotgc on 2023-06-03
[COLOR=#333333][FONT=Ubuntu][Goal]("https://i.imgur.com/5bURvD5.png"): Host machine running Virtual Machine Manager to have guest vm router on the LAN.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Host Ubuntu 22.04 Desktop 192.168.1.120 pinging VM router pfSense 192.168.1.1 error: Destination Host Unreachable.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The problem might be between netplan and libvirtd?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]```
ubuntu@ubuntu:/etc/netplan$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.120 icmp_seq=1 Destination Host Unreachable

```VMM automatically creates a bridge virbr0 and I don't know how to ignore it and use my created bridges NIC0-br0 and NIC1-br1.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]```

ubuntu@ubuntu:/etc/netplan$ ip -c a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br1 state UP group default qlen 1000
    link/ether 1c:61:b4:6d:38:4f brd ff:ff:ff:ff:ff:ff
    inet6 fe80::31ca:9227:dcb3:d09e/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether a8:a1:59:6e:1f:8b brd ff:ff:ff:ff:ff:ff
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:88:b4:b4 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether fe:54:00:33:3c:4b brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe33:3c4b/64 scope link
       valid_lft forever preferred_lft forever
8: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether fe:54:00:50:81:3f brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe50:813f/64 scope link
       valid_lft forever preferred_lft forever
9: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 0a:d4:78:1f:cd:41 brd ff:ff:ff:ff:ff:ff
    inet 100.76.25.213/10 brd 100.127.255.255 scope global dynamic noprefixroute br0
       valid_lft 294sec preferred_lft 294sec
    inet6 2406:2d40:4100:8fb2:19c5:376e:1317:8ae1/64 scope global temporary dynamic
       valid_lft 197sec preferred_lft 47sec
    inet6 2406:2d40:4100:8fb2:8d4:78ff:fe1f:cd41/64 scope global dynamic mngtmpaddr
       valid_lft 197sec preferred_lft 47sec
    inet6 fe80::8d4:78ff:fe1f:cd41/64 scope link
       valid_lft forever preferred_lft forever
10: br1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether d2:da:46:a2:b2:3e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.120/24 brd 192.168.1.255 scope global noprefixroute br1
       valid_lft forever preferred_lft forever
    inet6 fe80::d0da:46ff:fea2:b23e/64 scope link
       valid_lft forever preferred_lft forever

```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Bridges I created:
```

ubuntu@ubuntu:/etc/netplan$ bridge link
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 master br1 state forwarding priority 32 cost 4
3: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 master br0 state forwarding priority 32 cost 100

```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]NetworkManager configuration file:
```

ubuntu@ubuntu:/etc/netplan$ cat 01-network-manager-all.yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp2s0:
      dhcp4: true
    enp3s0:
      dhcp4: true
  bridges:
    br0:
      dhcp4: true
      interfaces:
        - enp3s0
    br1:
      dhcp4: false
      addresses: [192.168.1.120/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8,8.8.8.4]
      interfaces:
        - enp2s0

```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Routes:
```

ubuntu@ubuntu:/etc/netplan$ ip r
default via 100.64.0.1 dev br0 proto dhcp metric 425
default via 192.168.1.1 dev br1 proto static metric 20426
34.120.255.244 dev br0 proto dhcp scope link metric 425
100.64.0.0/10 dev br0 proto kernel scope link src 100.76.25.213 metric 425
169.254.0.0/16 dev virbr0 scope link metric 1000 linkdown
192.168.1.0/24 dev br1 proto kernel scope link src 192.168.1.120 metric 426
192.168.100.1 dev br0 proto dhcp scope link metric 425
192.168.122.0/24 dev virbr0 proto kernel scope link src 192.168.122.1 linkdown

```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Not sure if there's an iptables issue?
```

ubuntu@ubuntu:/etc/netplan$ sudo iptables -n -t nat -L
[sudo] password for ubuntu:
Chain PREROUTING (policy ACCEPT)
target prot opt source destination
```[/FONT][/COLOR]```

[COLOR=#333333][FONT=Ubuntu]Chain INPUT (policy ACCEPT)
target prot opt source destination[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Chain OUTPUT (policy ACCEPT)
target prot opt source destination[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Chain POSTROUTING (policy ACCEPT)
target prot opt source destination
LIBVIRT_PRT all -- 0.0.0.0/0 0.0.0.0/0[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Chain LIBVIRT_PRT (1 references)
target prot opt source destination
RETURN all -- 192.168.122.0/24 224.0.0.0/24
RETURN all -- 192.168.122.0/24 255.255.255.255
MASQUERADE tcp -- 192.168.122.0/24 !192.168.122.0/24 masq ports: 1024-65535
MASQUERADE udp -- 192.168.122.0/24 !192.168.122.0/24 masq ports: 1024-65535
MASQUERADE all -- 192.168.122.0/24 !192.168.122.0/24
[/FONT][/COLOR]
```

---

### Post by TheFu on 2023-06-04
What are the IPs for each bridge?  They cannot be on the same subnet.
Using DHCP with servers is a bad idea.

---

### Post by MAFoElffen on 2023-06-05
> **TheFu said:**
> Using DHCP with servers is a bad idea.
DHCP is just a service. Why not have a service on a server, as long as it is setup in a logically sound manner?  Why not on a server in a VM or container? A virt bridge can be assigned a dedicated NIC to isolate it (logically) from it's Host...

Fishing for your thoughts on that... 

That is like 'routers' can provide DNS, firewall, sftp, ACL, and other services... But that doesn't mean 'that' service being located there, is the only way it can do done. Some services in some infrastructures are moved off and 'specialized' in how that are applied... Whether the decision for that is for more isolation, compartmentalization, or added functionality.

Linux itself follows the methodology of modules and layers that can be interchanged, and be very flexible in how that are presented, applied, as well as where that are laid out and/or located.

Sorry. Just some thoughts and a bit of curiosity on what you are saying. That short statement (without further context) just brought "so many" things to mind. Because some factions preach ad teach that in some (other) OS'es... (And I feel that a lot of that is their own marketing hype, locking people into using "their" products and licensing.)

I am sincerely interested in your thoughts on this.

---

### Post by TheFu on 2023-06-05
I've seen DHCP failures take down nearly an entire data center.  They'd set the DHCP lease period to be conveniently short to allow for new, non-production, systems to be brought up.  When the primary and redundant DHCP servers failed (I don't recall why), all the other servers didn't just keep their existing IPs and dropped off the network.

For this reason, I stand by setting up static IPs on all servers.

Nobody plans for redundant DHCP servers to fail.  We plan for 1 failure, not 2.  I wasn't on the DHCP team, so I don't know the details. I'm just glade that my CSAs were old-school and setup our mission critical servers NOT to use DHCP.  All our users (22K+) were able to keep working while the rest of the company 100K+ employees were struggling.  BTW, we had multiple DHCP server vendor SEs on site. They had desks with our architecture teams and were dedicated to our account.

As an admin, most of my job is to avoid bonehead failures.  DHCP has a place ... for non-critical systems and desktops, but please, please, please, keep it away from controlling server network settings.  Forget what these "vendors" preach as their suggested "best practice".

---

### Post by MAFoElffen on 2023-06-06
@kotcg --

In your netplan .yaml file
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
      interfaces: [enp2s0]
      addresses: [192.168.1.120/24]
      # gateway4 is deprecated, use routes instead
      routes:
      - to: default
        via: 192.168.1.1
        metric: 100
        on-link: true
      mtu: 1500
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: false
      dhcp6: false
      optional: true

```
Using systemd-networkd, instead of Network Manager... Officially recommended after 18.04. IMHO, I feel it's because sometimes the two get confused if you use netplan .yaml files and have both active at the same time... Because Network Manager config files are actually elsewhere, and in a different format.
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl unmask systemd-networkd
sudo systemctl enable systemd-networkd
sudo systemctl enable systemd-resolved
sudo systemctl start systemd-resolved
systectl status systemd-networkd
systemctl status systemd-resolved
sudo netplan generate
sudo netplan --debug apply

```
Check to make sure the bridge is defined and working
```

brctl show
networkctl
networkctl status br0
ip a show br0
ip route
arp -n

```
Then create this XML stub file named host-bridge.xml, for use with KVM:
```

<network>
  <name>host-bridge</name>
  <forward mode="bridge"/>
  <bridge name="br0"/>
</network>

```
While in the same directory, as that file, define the libvirtd bridge
```

virsh net-define host-bridge.xml
virsh net-start host-bridge
virsh net-autostart host-bridge
virsh net-list --all

```
In Virt Manager, when you then use host-bridge as your Virt switch, then it should add the network XML stub, similar to this, to your VM's Domain XML:
```

<interface type='network'>
    <source network='host-bridge'/>
    <model type='virtio'/>
    <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
</interface>

```
Basically, your initial netplan .yaml file was incorrect and had the NIC confused, where you have the interface half defined by grabbing dhcp info, 'before' handing it off to the bridge interface config. You can see where I told it dhcp as false, as if static, then handed the interface to the bridge define... Where it then gets it's config from there (instead). Your's was just a bit off by where things were defined. For a bridge in netplan, the configuration of the device is in the bridge section... 

You should then try to ping 192.168.1.1... Then try to connect to it via a browser to get the the login screen of PfSense to configure it.

@TheFu -- True. But the OP was asking about help getting his virt bridge working, to install a virtual router appliance as his private / personal LAN router / firewall / appliance. Isn't that in affect the same job as any hard router? Just saying... That isn't like MS Server where they try to install 'the world' (of services) on the same server. As you say, dhcp has it's place and time... in a private network setting (such as what he described, right?) I use dhcp for private LAN and to support FOG PXE deployment servers.

I use pfsense and DD-WRT appliances as guests in my virtual networking schemes... Though I trust hard / metal routers for my outgoing edge-router appliances. But that is just me.

---

### Post by TheFu on 2023-06-06
> **MAFoElffen said:**
> @TheFu -- True. But the OP was asking about help getting his virt bridge working, to install a virtual router appliance as his private / personal LAN router / firewall / appliance. Isn't that in affect the same job as any hard router? Just saying... That isn't like MS Server where they try to install 'the world' (of services) on the same server. As you say, dhcp has it's place and time... in a private network setting (such as what he described, right?) I use dhcp for private LAN and to support FOG PXE deployment servers.

I use pfsense and DD-WRT appliances as guests in my virtual networking schemes... Though I trust hard / metal routers for my outgoing edge-router appliances. But that is just me.

I have OPNSense on my WAN and LAN routers.  Dedicated HW for the WAN, a VM for the LAN, so you aren't alone on that.  Real hardware for routers that keep the bad traffic out.  I wouldn't trust a VM for that, regardless of what VMware suggests to deploy.  

For guests on wifi, which are outside my WAN connection, they use the ISP's DHCP server.  I do let the opnsense VM provide DHCP reservations for specific devices like TV-tuners because there's no other way to set the IPs on those devices.  No unknown devices on the either the server or wired LANs.

My pi-holes are only DNS servers/filters. No DHCP. I run them in lxd containers, as primary and backup.

I'm certain between the two of us, we can come up with different, but still very excellent LAN infrastructure choices.  As usual, there are many ways to solve a problem and we make choices based on our experiences.  If I hadn't seen such a huge failure in a highly professional IT shop, I'd say to relax.  Further, I've caused an outage in my HOME LAN many years ago that was related to DNS/DHCP mistakes and before that, I was hacked when I was running a version of BIND that was a few months behind on patches.  Fortunately, after they broke in, they couldn't get any farther and every attempt created an alert that I couldn't miss.

---

### Post by MAFoElffen on 2023-06-07
LMAO! Yup. I can relate. Had someone who mistakenly broadcasted his dhcp from his Win Server VM, back upstream into the Department's network infrastructure, and was duplicating IPv4 addresses in that subnet. Took a full day to track it down via WireShark and the captured Virtual MAC address...

I didn't know until then, that by default, Hyper-V has it's own type of MAC address generation scheme:
```

Hyper-V generates the MAC address as described below (mapping MAC address to aa-bb-cc-dd-ee-ff):

 
[LIST]
[*]The first three octets (aa-bb-cc) are Microsoft's IEEE  organizationally Unique Identifier, 00:15:5D (which is common on all  Hyper-V hosts.
[*]The next two octets (dd-ee) are derived from the last two octets of the server's IP address.
[*]The last octet (ff) is automatically generated from the range 0x0-0xFF.
[/LIST]
 Because the last octet is an 8-bit value, there is a default limit of 256 possible MAC addresses.


```
That helped me trace down that dhcp disaster... LOL Yes. Things happen.

---

### Post by TheFu on 2023-06-07
I generally force the VM MAC address to known values that map to the main IPv4 address.
```
00:16:3e:35:b2:**81** --> 172.22.22.**81**
```
Simple thing, but very handy.

All sorts of these little details learned over decades as an admin add up to way to prevent problems,  downtime, and just generally make certain knowledge easier to find.

---

### Post by DuckHook on 2023-06-09
=d>
I learn amazing stuff from you guys all the time.

---

### Post by TheFu on 2023-06-09
> **DuckHook said:**
> =d>
I learn amazing stuff from you guys all the time.

Back at 'cha!  I'm positive I've stolen some of your stuff - probably over 100 times. ;)
_Standing on the shoulders of giants_ is the Linux way.

---

### Post by kotgc on 2023-12-04
I've finished fine tuning the VM router setup and it works nicely.
I like post #8's number management, however I set the LAN within a broader network's range. This only leaves managing the MAC address numbers which I understand is impossible.
Here's my final code:
```

ubuntu@ubuntu:/etc/netplan$ cat 01-netcfg.yaml 
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: false
      dhcp6: false
    enp3s0:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [enp3s0]
      dhcp4: false
      dhcp6: false
      macaddress: a8:a1:59:6e:1f:8b
      parameters:
        stp: false
    br1:
      interfaces: [enp2s0]
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.120/24]
      macaddress: 1c:61:b4:6d:38:4f
      routes:
        - to: default
          via: 192.168.1.170
      nameservers:
        addresses: [8.8.8.8]
      parameters:
        stp: false

```

---

### Post by TheFu on 2023-12-04
Bridge MACs don't matter, since they are ... er ... bridges.  The network interface using the bridge gets to control the MAC.

I'm not a fan of using virtualization to setup WAN routers.  Security reasons.  When a router fails, I want no traffic in or out.  BTW, you probably want at least 2 DNS listed.  For LAN-only routers, using a VM is fine in my book. It isn't the end of the world if traffic leaks across different the LAN segments.

Why use the filename 01-netcfg.yaml?  That isn't very descriptive.  YAML files are processed in order, so using numbers isn't bad. They have to end in .yaml to be processed, but netcfg?  Wouldn't that be better named "bridges-bitches? .... to "01-bridges-bitches.yaml"

Perhaps I'm missing something, but why bother specifying MACs at all?
Lastly, MACs can be changed, but that is a driver and hardware capability.  Most of my NICs support changing the MAC. I haven't played with that in about a decade, so I just assume the newer, better, cards can do it too.

---

### Post by MAFoElffen on 2023-12-04
@TheFu --

I think he did that because in the post before this: [https://ubuntuforums.org/showthread.php?t=2487417&p=14146008#post14146008](https://ubuntuforums.org/showthread.php?t=2487417&p=14146008#post14146008)
You mentioned about broadcasting DHCP on the wrong network/subnet brought something down... And I, in that post, mentioned I had nightmare about tracing the same, that I had to trace down with WireShark through the MAC Address to a Hyper-V VM... And in the next post, you mentioned your rule of thumb, of how you come up with MAC Addresses for your VM's...

So maybe, from those posts in this thread, that he assumed he should reset his(?)

---

### Post by TheFu on 2023-12-04
> **MAFoElffen said:**
> @TheFu --

I think he did that because in the post before this: [https://ubuntuforums.org/showthread.php?t=2487417&p=14146008#post14146008](https://ubuntuforums.org/showthread.php?t=2487417&p=14146008#post14146008)
You mentioned about broadcasting DHCP on the wrong network/subnet brought something down... And I, in that post, mentioned I had nightmare about tracing the same, that I had to trace down with WireShark through the MAC Address to a Hyper-V VM... And in the next post, you mentioned your rule of thumb, of how you come up with MAC Addresses for your VM's...

So maybe, from those posts in this thread, that he assumed he should reset his(?)

I don't remember information from other posts, especially if they are over 5 hours ago.  If I've slept, it is all new to me.

My issue with DHCP was that the DHCP server was down so every system dependent on it for a lease renewal or reboot couldn't get an IP.  At work, an entire campus with thousands of workstations didn't work due to that.  Once at home, when I was centralizing my IP management via DHCP reservations and my DHCP server failed, I didn't realize the issue until just after patching, which needed a reboot. None of the rebooted systems (all of them) came back up. It sucked.  I spent time trying to figure out which patch was the issue, not that DHCP failed.  Took hours - all because I was too lazy to set static IPs on each system/VM.  I learned my lesson. Never again.

---

### Post by MAFoElffen on 2023-12-04
"169.254. x.y"

If a DHCP client fails to get an assigned address from the DHCP server, then it assigns itself an IP in that range. I remember that well. More nightmares. 

First time i saw that, I was "What the heck?". Yup. LOL.

---

