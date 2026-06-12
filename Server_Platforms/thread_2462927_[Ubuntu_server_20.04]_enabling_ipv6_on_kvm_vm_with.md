---
title: "[Ubuntu server 20.04] enabling ipv6 on kvm vm with libvirt."
date: 2021-05-30
forum: Server Platforms
---

### Post by alx3456736547 on 2021-05-30
Hello, 

I've been trying to add ipv6 conectivity to a vm in kvm with libvirt, starting with the default NAT ipV4 virtual network.

ipv6 works fine on the host.
The ipv4 nat to the vm (named "test0") works.

I first tried to add an ipv6 block into the default network configuration, but since NAT with ipv6 sounds weird, and I wanted to make sure it wasn't the source of my problems, I created a second network "ipv6bridge", using this ipv6 only configuration :

```

<network>
  <name>ipv6bridge</name>
  <bridge name='virbr1' stp='on' delay='0'/>
  <mac address='52:54:00:b5:04:bf'/>
  <forward mode="route" />
[COLOR=#000000]  <ip family='ipv6' address='<my ipv6 block>::' prefix='120'>
    <dhcp>
      <range start='<my ipv6 block>::10' end='<my ipv6 block>::ff'/>
      <host id='<the host id for ipv6>' name='test0' ip='<my ipv6 block>::10'/>
    </dhcp>
  </ip>[/COLOR]
</network>

```

But with both (ipv6 in default NAT, or ipv6bridge network), I get the same error when I start them (using virsh net-start <network-name>

```

error: Failed to start network ipv6bridge
error: internal error: Check the host setup: enabling IPv6 forwarding with RA routes without accept_ra set to 2 is likely to cause routes loss. Interfaces to look at: eno1

```

So I guess this is about packet forwarding and not about converting the the ancient egyptian god.

I can change it using sysctl, but I don't manage to make it persistant through reboot, not even by putting it in the sysctl.conf file or sysctl.d.
There is no trace of it in the syslog, and the command netplan apply seems to reset any change I make with sysctl, so I guess netplan erases at boot any change I make.

Otherwise, if I set in netplan
eno1:
  accept_ra: false

The value of net.ipv6.conf.eno1.accept_ra will still be 0, but virsh won't complain while starting the network, which is completely counterintuitive.



Anyway, if I go further, by forcing sysctl -w net.ipv6.conf.eno1.accept_ra=2
the virtual network seems to work and gives the right ipv6 address to the vm, as shown by the virsh net-dhcp-leases command :

```

 Expiry Time           MAC address         Protocol   IP address                 Hostname   Client ID or DUID
---------------------------------------------------------------------------------------------------------------------------------------
 2021-05-30 14:57:22   52:54:00:79:3d:43   ipv6       <my ipv6 block>::10/120   test0      00:02:00:00:ab:11:48:86:57:70:35:90:a2:ed

```

the "ip -6 route show command " also shows that libvirt did its job by creating the route:

```

<my ipv6 block>::/120 dev virbr1 proto kernel metric 256 pref medium

```

the guest VM has its second interface set to the right ip as shown by ifconfig:

```

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::5054:ff:fe79:3d43  prefixlen 64  scopeid 0x20<link>
        inet6 <my ipv6 block>::10  prefixlen 128  scopeid 0x0<global>
        ether 52:54:00:79:3d:43  txqueuelen 1000  (Ethernet)
        RX packets 157  bytes 9189 (9.1 KB)
        RX errors 0  dropped 141  overruns 0  frame 0
        TX packets 20  bytes 1879 (1.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
 
But it won't have any connectivity, pinging the host or google won't do anything.

Trying to ping the guest from the host, I get
PING <my ipv6 block>::10(<my ipv6 block>::10) 56 data bytes
From <my ipv6 block>:ff:ff:ff:fd icmp_seq=1 Destination unreachable: Address unreachable

Trying a traceroute, even with forcing the virbr1 interface, it will send packets to the outside.

ip6tables -L outputs :

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
LIBVIRT_INP  all      anywhere             anywhere

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
LIBVIRT_FWX  all      anywhere             anywhere
LIBVIRT_FWI  all      anywhere             anywhere
LIBVIRT_FWO  all      anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
LIBVIRT_OUT  all      anywhere             anywhere

Chain LIBVIRT_FWI (1 references)
target     prot opt source               destination
ACCEPT     all      anywhere             <my ipv6 block>::/120
REJECT     all      anywhere             anywhere             reject-with icmp6-port-unreachable

Chain LIBVIRT_FWO (1 references)
target     prot opt source               destination
ACCEPT     all      <my ipv6 block>::/120  anywhere
REJECT     all      anywhere             anywhere             reject-with icmp6-port-unreachable

Chain LIBVIRT_FWX (1 references)
target     prot opt source               destination
ACCEPT     all      anywhere             anywhere

Chain LIBVIRT_INP (1 references)
target     prot opt source               destination
ACCEPT     udp      anywhere             anywhere             udp dpt:dhcpv6-server
ACCEPT     udp      anywhere             anywhere             udp dpt:domain
ACCEPT     tcp      anywhere             anywhere             tcp dpt:domain

Chain LIBVIRT_OUT (1 references)
target     prot opt source               destination
ACCEPT     udp      anywhere             anywhere             udp dpt:dhcpv6-client
ACCEPT     udp      anywhere             anywhere             udp dpt:domain
ACCEPT     tcp      anywhere             anywhere             tcp dpt:domain


```

That's as far as I go. 

When I try to define virbr1 in netplan, libvirt will refuse to start, it seems it wants to create it itself.

I guess there's something about setting forwarding in eno1 and virbr1, but I don't know if I can do it in Netplan, especially if libvirt creates virbr1 afterwards.

Thanks in advance if you can provide me with any explanation.

---

### Post by alx3456736547 on 2021-05-30
ip6tables -S outputs the following

```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N LIBVIRT_FWI
-N LIBVIRT_FWO
-N LIBVIRT_FWX
-N LIBVIRT_INP
-N LIBVIRT_OUT
-A INPUT -j LIBVIRT_INP
-A FORWARD -j LIBVIRT_FWX
-A FORWARD -j LIBVIRT_FWI
-A FORWARD -j LIBVIRT_FWO
-A OUTPUT -j LIBVIRT_OUT
-A LIBVIRT_FWI -d <my ipv6 block>::/120 -o virbr1 -j ACCEPT
-A LIBVIRT_FWI -o virbr1 -j REJECT --reject-with icmp6-port-unreachable
-A LIBVIRT_FWO -s <my ipv6 block>::/120 -i virbr1 -j ACCEPT
-A LIBVIRT_FWO -i virbr1 -j REJECT --reject-with icmp6-port-unreachable
-A LIBVIRT_FWX -i virbr1 -o virbr1 -j ACCEPT
-A LIBVIRT_INP -i virbr1 -p udp -m udp --dport 547 -j ACCEPT
-A LIBVIRT_INP -i virbr1 -p udp -m udp --dport 53 -j ACCEPT
-A LIBVIRT_INP -i virbr1 -p tcp -m tcp --dport 53 -j ACCEPT
-A LIBVIRT_OUT -o virbr1 -p udp -m udp --dport 546 -j ACCEPT
-A LIBVIRT_OUT -o virbr1 -p udp -m udp --dport 53 -j ACCEPT
-A LIBVIRT_OUT -o virbr1 -p tcp -m tcp --dport 53 -j ACCEPT

```

---

### Post by alx3456736547 on 2021-05-30
So, it appears I can't use the same ipv6 on the internal network and on the outside network, because it will mess up routing.
(Of course, like in ipv4, a router must have on each interface an ip address that belongs to the network on that interface).

If I modify the configuration of the network :

```

[COLOR=#000000]  <ip family='ipv6' address='<my ipv6 block>::100' prefix='120'>
    <dhcp>
      <range start='<my ipv6 block>::110' end='<my ipv6 block>::1ff'/>
      <host id='<the host id for ipv6>' name='test0' ip='<my ipv6 block>::110'/>
    </dhcp>
  </ip>[/COLOR]


``` 

Now I can ping the guest from the host, and the host from the guest.

The guest is still isolated thought.

I added a default ipv6 route on the guest through the right interface :

ip -6 route add default via <my ipv6 block>::100 dev enp6s0

But I still won't get an answer for my pings.

---

### Post by alx3456736547 on 2021-05-31
I tried adding the outside interface of the host in the configuration of  libvirt's virtual network, then I created a bridge on the host with netplan, and  tried to connect it to the virtual bridge :

```

  <forward dev='br1' mode='route'>
    <interface dev='br1'/>
  </forward>

```

The bridge generation code in netplan looks like that :

```

    bridges:
        br1:
            accept-ra: false
            macaddress: <same as ino1>
            interfaces: [eno1]
            dhcp4: true
            dhcp6: false
            addresses:
            - <my ipv6 block>::/56
            nameservers:
                addresses:
                - <ns address>::1
            gateway6: <gateway address>

```

It still doesn't work, this is a nightmare.

Though, the guest can ping <my ipv6 block>::/56, so at least it is indeed connected to br1, but it get no answer from anything further.

---

### Post by TheFu on 2021-05-31
Does using NAT make any sense with IPv6?
Have you tried using a bridge for both IPv4 and IPv6? 

My IPv6 knowledge is superficial at best. Attended a number of talks about it about a decade ago and decided I'd just block it until it was useful for my needs.

---

### Post by alx3456736547 on 2021-06-01
Hi, thanks for answering :)

Ipv6 doesn't make much sense indeed with ipv6 (maybe for mobile connections), but I tried it first because I hoped it would work alongside with the out the box ipv4 nat connection. Well it doesn't :(
The reason to make ipv6 only networks are because ipv4 are scarce and are becoming expensive, while you have billions of ipv6 for free. Anyway, on my test server, I've only one ipv4, so it's complicated to bridge it.

Anyway, my posts were messy because of my lacking knowledge. Here's a sum up from what I understood:

[U]




**ipv6 NAT Mode**
[/U]
Adding ipv6 in the default ipv4 NAT virtual network doesn't work as expected. The dhcp6 works, the host can ping the guest and the guest can ping the host, but there is no out of the box "inside to outside" NAT connectivity like for ipv4.







[U]**ipv6 ROUTE Mode**
[/U]
For this one, we create a second virtual network with libvirt, to which we connect a new interface on the guest.

The libvirt configuration of the network is like this:

virsh net-edit ipv6bridge

```

<network>
  <name>ipv6bridge</name>
  <uuid>137eb741-e85e-4b7c-9233-8cee419e0d14</uuid>
  <bridge name="virbr1"/>
  <forward mode="route" dev="[COLOR=#ff0000]eno1[/COLOR]"/>
  <ip family="ipv6" address='<my ipv6 block>::110' prefix='120'>
    <dhcp>
      <range start='<my ipv6 block>::111' end='<my ipv6 block>::1ff'/>
      <host id='00:02:00:00:ab:11:48:86:57:70:35:90:a2:ed' name='test0' ip='<my ipv6 block>::111'/>
    </dhcp>
  </ip>
</network>

```

We tell libvirt in the <forward> block to connect the virtual bridge (virbr1) to the hosts physical interface (eno1).

libvirt seems to do it work :

ip6tables -S

```

...
-A LIBVIRT_FWI -d <my ipv6 block>::100/120 -i eno1 -o virbr1 -j ACCEPT
...
-A LIBVIRT_FWO -s <my ipv6 block>::100/120 -i virbr1 -o eno1 -j ACCEPT
...

```

ip6tables -L

```

...
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
LIBVIRT_FWX  all      anywhere             anywhere
LIBVIRT_FWI  all      anywhere             anywhere
LIBVIRT_FWO  all      anywhere             anywhere
...

```

Routing tables are ok :

ip -6 route

```

...
<my ip block>::100/120 dev virbr1 proto kernel metric 256 pref medium
...
default via 2001:41d0:8:c4ff:ff:ff:ff:ff dev eno1 proto static metric 1024 pref medium

```

ipv6 forwarding seems to be on :

sysctl -a

```

net.ipv6.conf.all.forwarding = 1
net.ipv6.conf.all.mc_forwarding = 0
net.ipv6.conf.default.forwarding = 1
net.ipv6.conf.default.mc_forwarding = 0
[COLOR=#ff0000]net.ipv6.conf.eno1.forwarding = 1[/COLOR]
net.ipv6.conf.eno1.mc_forwarding = 0
net.ipv6.conf.lo.forwarding = 1
net.ipv6.conf.lo.mc_forwarding = 0
net.ipv6.conf.virbr0.forwarding = 1
net.ipv6.conf.virbr0.mc_forwarding = 0
net.ipv6.conf.virbr0-nic.forwarding = 1
net.ipv6.conf.virbr0-nic.mc_forwarding = 0
[COLOR=#ff0000]net.ipv6.conf.virbr1.forwarding = 1[/COLOR]
net.ipv6.conf.virbr1.mc_forwarding = 0
net.ipv6.conf.virbr1-nic.forwarding = 1
net.ipv6.conf.virbr1-nic.mc_forwarding = 0
net.ipv6.conf.vnet0.forwarding = 1
net.ipv6.conf.vnet0.mc_forwarding = 0
net.ipv6.conf.vnet1.forwarding = 1
net.ipv6.conf.vnet1.mc_forwarding = 0

```

and the firewall is off:

 ufw status
```

Status: inactive

```

I really don't understand why it doesn't work.

The host can talk to the guest, and it can talk to the outside.

But nothing goes through the host :
The guest can talk to the host, even to the host "public" address, but not to the outside, and the outside can not reach the guest.

(I had to specify the ipv6 gateway on the guest, strangely it's not set by dhcp6)
on the guest :

ip -6 route 

```

...
default via 2001:41d0:8:c4ad::110 dev enp6s0 proto static metric 1024 onlink pref medium

```







**_ipv6 bridge mode_**

From what I understand, on this mode, you create the interfaces on the host, and you directly plug the guests on them.

For now, I don't manage to create them with netplan :

```

network:
    version: 2
    renderer: networkd
    ethernets:
        eno1:
            accept-ra: false
            addresses:
            - <my ip block>::/56
            - <my ip block>::2/56:
                lifetime: 0
                label: "eno1:0"
...


```

The configuration is accepted, but I don't see any eno1:0 interface appear with ifconfig.

I guess I'll try with vlans, but again I'm in unknown territory.

edit : actually the right way seems to create a bridge on the host, connect the physical interface to it, and then connect the vms with the bridge, but I still don't manage to make it work. "brctl show" doesn't show any connection between the bridge and the vm.

---

### Post by TheFu on 2021-06-01
I don't use NAT except for toy VMs used for 1-2 days.

I would never imaging that NAT on IPv4 wouldn't block IPv6 on the same device.  It is the same NIC, just with 2 network layers.  Doesn't IPv6 have an automatic IPv4 translation subnet?  2001::..... something?  

Bridging isn't hard, pre-netplan.  Post-netplan, I think they finally have it down.  With the correct hardware, PCIe passthru (dedicated NIC) isn't hard either and vastly more secure.  Just depends on your needs.

I assumed if you have a full KVM system, then you'd have control over the LAN IPs and not be limited. Guess I was wrong.

Please don't tell me that you are using nested virtualization! Please don't do that with vt-x required hypervisors.  If you need something like that, don't use a full VM, use some sort of Linux Container.  Then you'd have the host forward ports to each container. There are multiple ways of doing that.  With LXD, you can have a container that gets safely treated like a VM. I've been running LAN-DNS filter systems inside LXD containers about a year. Much less storage used than a full VM, crazy fast, and I treat them the same as any other VM for almost everything. They have their own LAN IPs, weekly patching, etc.  Very much **NOT** like docker, but with similar performance.  I'm not ready to use them directly on the internet, but for internal LAN stuff, they have been excellent.

Whatever you do inside netplan, always ether enable or disable DHCP for both IPv4 and IPv6.  The defaults never make sense. For a period of time, they didn't actually work, which caused issues.  I couldn't get netplan working on an 18.04 system until the beginning of 2020.  In late 2019, something was still "off", at least for me.  Netplan vs the interfaces file doesn't really matter to me, though I wish netplay yaml wasn't so picky. Humans who aren't seasoned software devs have all sorts of problems with yaml.  The only things worse are XML and JSON.  Give me a Windows 3.1 inifile any day over all this other junk.

ifconfig is deprecated.  **ip** is the command to be used. Don't remember why I added this line.
 
Again, I haven't moved to 20.04 because of the bridge networking troubles, but in my notes, I have these:
[https://netplan.io/examples](https://netplan.io/examples)
[https://ubuntuforums.org/showthread.php?t=2443548&p=13961621#post13961621](https://ubuntuforums.org/showthread.php?t=2443548&p=13961621#post13961621)
[https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-network-with-netplan-on-ubuntu-bionic/)
and
```
# #################################
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: networkd
  ethernets:
     eth0:
       dhcp4: false
       dhcp6: false
  bridges:
      br0:
        interfaces: [eth0]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.31.15/24]
        gateway4: 192.168.31.1
        nameservers:
           addresses: [192.168.31.80]
```

I have been using netplan over a year on some systems, but none are bridged.  I like to avoid the bleeding edge and really don't want to impact my clients.

Last time I tried to use any networking setup by libvirt was around 2010 and it was slow-slow-slow. Back then, the fix was to manually create a bridge and on 10Gbps connections, to use openVswitch.  On 1Gbps the bridge-utils were fine.

I have never needed to edit the network settings inside the XML VM "definition" file.  Just add 1 of 3 bridges to the VM - public, backup, management LANs, and be done.

UFW isn't "the firewall".  It is an interface into the kernel firewall. It is always on.  Think of UFW as a meta-tool that creates iptables rules and iptables as the lowest level access for humans into the Linux firewall. Check the iptables rules, that will show what is really happening.  On a server, ufw usually isn't a sufficient way to control the firewall, I'm sorry to say.

---

### Post by alx3456736547 on 2021-06-02
Thank you for your help, it's very informative.

My context is a physical server only with remote access, and the provider gives with it one ipv4 and an ipv6 range.
After migrating an old server, I used it to experiment a much as I could before they would unplug it (and I discovered how much I lacked in practical networking, that's why for instance why I started to doubt if I could see everything through iptables or if there was another hidden firewall).

I'll try to continue testing on another computer and figure out about interfaces, labels, vlans and bridges and promiscous modes and I'll tell here what I was lacking when I find out.

Thanks again !

---

