---
title: "Can't ping/ssh VM [ NAT mode ]"
date: 2010-10-12
forum: Virtualisation
---

### Post by luvshines on 2010-10-12
I have used VMware-Server in the past on RHEL/Fedora host where the VM's were also RHEL/Fedora.
I used NAT mode and was able to ssh between the VM's and host pretty easily

Thinking on similar lines, I installed VMware-Server on Ubuntu host(running lucid lynx) and the guest image is Maverick(10.10), but I am not able to ssh/ping the guest machine from my host, in NAT mode. **I can't use any other mode because of network issues**

**[COLOR="Red"]Though reverse is working perfect, ie from Guest to Host[/COLOR]**

There are no blocking firewalls on any of the machines

Ifconfig snippets:
```
On host machine:
vmnet8    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:172.16.8.2  Mask:255.255.0.0
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

On guest machine:
eth0      Link encap:Ethernet  HWaddr 00:0c:29:f4:6f:93  
          inet addr:172.16.8.130  Bcast:172.16.8.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fef4:6f93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21197 (21.1 KB)  TX bytes:27212 (27.2 KB)
          Interrupt:18 Base address:0x2000
```

Routing tables:
```
On host machine:
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.73.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.5.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.5.1     0.0.0.0         UG    0      0        0 wlan0

On guest machine:
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.8.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.8.2      0.0.0.0         UG    0      0        0 eth0
```

Any ideas how to get this working ??

---

### Post by luvshines on 2010-10-13
**[COLOR="Red"]Bumping it ![/COLOR]**

**It works when I try on bridge but I can't stick to bridging, have to get it working in NAT only**

---

### Post by luvshines on 2010-10-15
---bump---

---

### Post by luvshines on 2010-10-21
[color="red"][size="5"]bump !![/size][/color]

---

### Post by JustinR on 2010-10-21
> **luvshines said:**
> [color="red"][size="5"]bump !![/size][/color]

Have you tried pinging the actualy VMware device? (172.16.8.2)

---

### Post by luvshines on 2010-10-22
> **JustinR said:**
> Have you tried pinging the actualy VMware device? (172.16.8.2)

I have run /usr/bin/vmware-config.pl the script again to reconfigure VMware

On host, Vmware device vmnet8 is now:
```
vmnet8    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:172.16.8.1  Mask:255.255.255.0

```

**I am able to ping this device**

VM has the address, 172.16.8.128 and its nameserver is 172.16.8.2

[B]VM is able to ping both the nameserver and host machine (192.168.5.102)
But host machine is still not able to ping the VM[/B]

Also ran traceroute on both VM and Host machine:
```

## On VM (gets answer in 2 Hops)
$traceroute 192.168.5.102
traceroute to 192.168.5.102 (192.168.5.102), 30 hops max, 60 byte packets
 1  172.16.8.2 (172.16.8.2)  0.971 ms  0.119 ms  0.121 ms
 2  192.168.5.102 (192.168.5.102)  0.212 ms  0.169 ms  0.164 ms

## On Host (takes 30 hops and fails)
$ traceroute 172.16.8.128
traceroute to 172.16.8.128 (172.16.8.128), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * * ...

```

As if it's not able to follow route and contact vmnet8 interface

---

### Post by JustinR on 2010-10-22
> **luvshines said:**
> I have run /usr/bin/vmware-config.pl the script again to reconfigure VMware

On host, Vmware device vmnet8 is now:
```
vmnet8    Link encap:AMPR NET/ROM  HWaddr   
          inet addr:172.16.8.1  Mask:255.255.255.0

```

**I am able to ping this device**

VM has the address, 172.16.8.128 and its nameserver is 172.16.8.2

[B]VM is able to ping both the nameserver and host machine (192.168.5.102)
But host machine is still not able to ping the VM[/B]

Also ran traceroute on both VM and Host machine:
```

## On VM (gets answer in 2 Hops)
$traceroute 192.168.5.102
traceroute to 192.168.5.102 (192.168.5.102), 30 hops max, 60 byte packets
 1  172.16.8.2 (172.16.8.2)  0.971 ms  0.119 ms  0.121 ms
 2  192.168.5.102 (192.168.5.102)  0.212 ms  0.169 ms  0.164 ms

## On Host (takes 30 hops and fails)
$ traceroute 172.16.8.128
traceroute to 172.16.8.128 (172.16.8.128), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * * ...

```

As if it's not able to follow route and contact vmnet8 interface

Hi, you can't ping a VM NAT address, although you can in Bridged Networking.

But you should be able to essentially achieve the same thing if you just use the VMWare Adator IP (Not the VM network adaptor IP), the 172.16.8.1 address.

---

### Post by luvshines on 2010-10-23
> **JustinR said:**
> Hi, you can't ping a VM NAT address, although you can in Bridged Networking. 

Does that mean I'll never be able to ping the ip 172.16.8.128 (NAT mode ip) ?

> But you should be able to essentially achieve the same thing if you just use the VMWare Adator IP (Not the VM network adaptor IP), the 172.16.8.1 address.

Pardon me, but I didn't understand this comment

---

### Post by JustinR on 2010-10-23
> **luvshines said:**
> Does that mean I'll never be able to ping the ip 172.16.8.128 (NAT mode ip) ?



Pardon me, but I didn't understand this comment

Yes thats what is means, and what I meant was that instead of pinging the Guest Network IP (172.16.8.128), but ping the VMWare Network Adapter thats showing up on the host computer (172.16.8.1).

---

### Post by luvshines on 2010-11-04
Still no luck with this one :(

---

### Post by CharlesA on 2010-11-04
The only way I've been able to get two-way communication going in a VM is to use bridged networking.

[s]Is there a reason you are using NAT?[/s]

What sort of networking scheme do you have in place that you cannot use bridged networking?

---

### Post by luvshines on 2010-11-05
When I am on office network, the machine has to be installed with loads of customized softwares which require loads of RAM and disk space, has to be compliant with office policies and to be used in a very restrictive way.

Each of the IP is monitored :(

In bridging, it will show on office network as a standalone machine which will create trouble
Hence I wanted to restrict my VM for NAT

---

### Post by CharlesA on 2010-11-05
That makes sense then.

It gets a bit complicated when you have the machine on a seperate network, unfortunately.

Are you able to ping it if you switch to "host-only interface" ?

---

### Post by herda05 on 2010-11-08
This isn't complicated, it's real simple. However, from my testing 8 months ago, something in Vmware or Ubuntu 9.04 and later broke ssh from host to VM. I have used Vmware for close to four years on Ubuntu and am unable to go leave Ubuntu 8.10 due to this problem. I posted on here and the vmware forums, and just recently looked again to find the issue has not been addressed.

As you can see in [this thread]("http://http://ubuntuforums.org/showthread.php?t=1435846") from March, it seems no progress has been made.

You might be out of luck on this issue.

---

### Post by JustinR on 2010-11-08
Hi,

We all need to read the VirtualBox Manual:
> 
The disadvantage of NAT mode is that,
much like a private network behind a router, the virtual machine is invisible and unreachable
from the outside internet; you cannot run a server this way unless you set up port forwarding
(described below).


Port Forwarding:
[Chapter 6 Section 3.1.]("http://www.virtualbox.org/manual/ch06.html#natforward")

---

### Post by herda05 on 2010-11-08
JustinR, that's incorrect for mutiple reasons, not least of which is that we are dealing with Vmware server.

However, it seems this has been fixed. Check out this link [here]("http://ubuntuforums.org/showthread.php?t=1473373&highlight=vmware+ping").

You can get the patch [here]("http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/").

I'm currently attempting to test now.

---

### Post by luvshines on 2010-11-09
> **herda05 said:**
> JustinR, that's incorrect for mutiple reasons, not least of which is that we are dealing with Vmware server.

However, it seems this has been fixed. Check out this link [here]("http://ubuntuforums.org/showthread.php?t=1473373&highlight=vmware+ping").

You can get the patch [here]("http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/").

I'm currently attempting to test now.

Applied the patch, rebuilt, reconfigured and **VOILA!! It started working :D**

Thanks a ton herda :guitar:
Marking it SOLVED for now, will report back if nething breaks

PS: I have been using NAT with vmware-server on RHEL with no issues only Ubuntu was giving trouble.

---

### Post by MurkMenthaa on 2012-03-10
[Allow Access to a VMware Virtual Machine(NAT) From Another Computer]("http://www.howtogeek.com/howto/vmware/allow-access-to-a-vmware-virtual-machinenat-from-another-computer/")

A rather elegant solution to if you're just running a virtual server for testing. Someone might find it handy (i did:)

---

