---
title: "Can't access Apache on VM from Host!"
date: 2020-04-24
forum: Virtualisation
---

### Post by mpugliesi2 on 2020-04-24
Hello. I will try to explain the scenario as much as I can.

My Host is Xubuntu 18.04.4 . I have two VM of Ubuntu Server 18.04.4 on VirtualBox. 

Both VM were installed with two Network cards.  One card configured with NAT with DHCP. The second card with Host-Only and Fix IP, DHCP on Host Network manager disable.

In one server I have installed apache2, I already opened UFW ports for apache.   

The problem is, I can ping from my host (xubuntu) to the server where I have installed apache, but I can't open apache default page from a web Browser in my host.

What am I missing? 

Here are some information: 

```
[COLOR=#2C001E][FONT=Ubuntu]galactus@NorrinRadd:/var/www/html$ tracepath 192.168.56.60  (IP from Server with Apache in VirtualBox)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu] 1:  NorrinRadd                                            0.093ms reached[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]     Resume: pmtu 65535 hops 1 back 1[/FONT][/COLOR]
```


```
[COLOR=#2C001E][FONT=Ubuntu]galactus@NorrinRadd:/var/www/html$ ifconfig[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]enp7s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        ether a4:1f:72:ff:9f:f0  txqueuelen 1000  (Ethernet)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX packets 0  bytes 0 (0.0 B)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX packets 0  bytes 0 (0.0 B)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet 127.0.0.1  netmask 255.0.0.0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet6 ::1  prefixlen 128  scopeid 0x10<host>[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        loop  txqueuelen 1000  (Local Loopback)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX packets 5982  bytes 830433 (830.4 KB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX packets 5982  bytes 830433 (830.4 KB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]vboxnet0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet 192.168.56.50  netmask 255.255.255.0  broadcast 192.168.56.255[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet6 fe80::800:27ff:fe00:0  prefixlen 64  scopeid 0x20<link>[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        ether 0a:00:27:00:00:00  txqueuelen 1000  (Ethernet)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX packets 0  bytes 0 (0.0 B)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX packets 1055  bytes 217873 (217.8 KB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]vboxnet1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet 192.168.56.60  netmask 255.255.255.0  broadcast 192.168.56.255[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet6 fe80::800:27ff:fe00:1  prefixlen 64  scopeid 0x20<link>[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        ether 0a:00:27:00:00:01  txqueuelen 1000  (Ethernet)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX packets 0  bytes 0 (0.0 B)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX packets 869  bytes 165061 (165.0 KB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]wlp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet 192.168.43.194  netmask 255.255.255.0  broadcast 192.168.43.255[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        inet6 fe80::5dd4:6783:f7b9:a55c  prefixlen 64  scopeid 0x20<link>[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        ether 54:35:30:fe:d9:01  txqueuelen 1000  (Ethernet)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX packets 828237  bytes 1089377733 (1.0 GB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        RX errors 0  dropped 0  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX packets 363005  bytes 46042746 (46.0 MB)[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]galactus@NorrinRadd:/var/www/html$[/FONT][/COLOR]
```

```
[COLOR=#2C001E][FONT=Ubuntu]galactus@NorrinRadd:/var/www/html$ ping -c 4 192.168.56.50[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]PING 192.168.56.50 (192.168.56.50) 56(84) bytes of data.[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]64 bytes from 192.168.56.50: icmp_seq=1 ttl=64 time=0.068 ms[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]64 bytes from 192.168.56.50: icmp_seq=2 ttl=64 time=0.063 ms[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]64 bytes from 192.168.56.50: icmp_seq=3 ttl=64 time=0.058 ms[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]64 bytes from 192.168.56.50: icmp_seq=4 ttl=64 time=0.065 ms[/FONT][/COLOR]

[COLOR=#2C001E][FONT=Ubuntu]--- 192.168.56.50 ping statistics ---[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]4 packets transmitted, 4 received, 0% packet loss, time 3031ms[/FONT][/COLOR]
[COLOR=#2C001E][FONT=Ubuntu]rtt min/avg/max/mdev = 0.058/0.063/0.068/0.008 ms[/FONT][/COLOR]

```

And yes, I can't use NAT for port forwarding and I can't use Bridge mode on network card!!!  Host-Only!


Why? Because this is an assignment from College! 

The worst thing is that this work when Windows is the Host system!

---

### Post by darkod on 2020-04-24
What is the IP and subnet of the host?

PS. Better yet, open terminal on the host and post the output of the following:
```
ifconfig
ip route show
```

---

### Post by slickymaster on 2020-04-24
*Thread moved to **Virtualisation**.*

---

### Post by mpugliesi2 on 2020-04-24
Thanks for your help (Obrigado pela ajuda).

```
galactus@NorrinRadd:~$ ifconfig
enp7s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether a4:1f:72:ff:9f:f0  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5147  bytes 552360 (552.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5147  bytes 552360 (552.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vboxnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.56.50  netmask 255.255.255.0  broadcast 192.168.56.255
        inet6 fe80::800:27ff:fe00:0  prefixlen 64  scopeid 0x20<link>
        ether 0a:00:27:00:00:00  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 394  bytes 66468 (66.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


vboxnet1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.56.60  netmask 255.255.255.0  broadcast 192.168.56.255
        inet6 fe80::800:27ff:fe00:1  prefixlen 64  scopeid 0x20<link>
        ether 0a:00:27:00:00:01  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 284  bytes 43836 (43.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.194  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::5dd4:6783:f7b9:a55c  prefixlen 64  scopeid 0x20<link>
        ether 54:35:30:fe:d9:01  txqueuelen 1000  (Ethernet)
        RX packets 3995148  bytes 5129548799 (5.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4631145  bytes 4921301322 (4.9 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
galactus@NorrinRadd:~$ 

```




```

galactus@NorrinRadd:~$ ip route show
default via 192.168.43.1 dev wlp6s0 proto dhcp metric 600 
169.254.0.0/16 dev wlp6s0 scope link metric 1000 
192.168.43.0/24 dev wlp6s0 proto kernel scope link src 192.168.43.194 metric 600 
192.168.56.0/24 dev vboxnet0 proto kernel scope link src 192.168.56.50 
192.168.56.0/24 dev vboxnet1 proto kernel scope link src 192.168.56.60 
galactus@NorrinRadd:~$
```

---

### Post by Doug S on 2020-04-24
There seems to be confusion in your information.
Both addresses, 192.168.56.50 and .60 seem to be on your host.

Notice when i do a tracepath to a VM from the host I get:

```
doug@s18:~$ tracepath 192.168.122.17
 1?: [LOCALHOST]                      pmtu 1500
 1:  192.168.122.17                                        0.303ms reached
 1:  192.168.122.17                                        0.213ms reached
     Resume: pmtu 1500 hops 1 back 1
```
 And also notice the times, your replies seem to be too fast, indicating a local (even for VMs) interface. Example of pinging a local IF:

```
doug@s18:~$ ping 192.168.122.1
PING 192.168.122.1 (192.168.122.1) 56(84) bytes of data.
64 bytes from 192.168.122.1: icmp_seq=1 ttl=64 time=0.048 ms
64 bytes from 192.168.122.1: icmp_seq=2 ttl=64 time=[COLOR="#FF0000"]0.048[/COLOR] ms
64 bytes from 192.168.122.1: icmp_seq=3 ttl=64 time=0.046 ms
64 bytes from 192.168.122.1: icmp_seq=4 ttl=64 time=0.043 ms
64 bytes from 192.168.122.1: icmp_seq=5 ttl=64 time=0.045 ms
64 bytes from 192.168.122.1: icmp_seq=6 ttl=64 time=0.044 ms
```Example of pinging the VM:

```
doug@s18:~$ ping 192.168.122.17
PING 192.168.122.17 (192.168.122.17) 56(84) bytes of data.
64 bytes from 192.168.122.17: icmp_seq=1 ttl=64 time=0.460 ms
64 bytes from 192.168.122.17: icmp_seq=2 ttl=64 time=0.279 ms
64 bytes from 192.168.122.17: icmp_seq=3 ttl=64 time=[COLOR="#FF0000"]0.292[/COLOR] ms
64 bytes from 192.168.122.17: icmp_seq=4 ttl=64 time=0.263 ms
64 bytes from 192.168.122.17: icmp_seq=5 ttl=64 time=0.215 ms
```However, I am using a qemu/kvm and not virtualbox

---

### Post by mpugliesi2 on 2020-04-24
It's my Notebook with Xubuntu the Host system.  

Both VM are inside virtualbox in my notebook, that is why I have a  fast ping reponse.

---

### Post by darkod on 2020-04-24
I don't have much experience with VBox without bridged mode, but like Doug says and it looks like ifconfig confirms it, the 192.168.56.50 and 192.168.56.60 seem to be IPs assigned to vboxnet0 and vboxnet1 from the host side.

From inside VM1 and VM2, what is the output of the same two commands?
```
ifconfig
ip route show
```

Ater we see that we could tell you more.

---

### Post by mpugliesi2 on 2020-04-24
You can see here:

Client
[[IMG]https://i.postimg.cc/HJkCwyCw/Ajuda-client.png[/IMG]]("https://postimg.cc/HJkCwyCw")


Server
[[IMG]https://i.postimg.cc/R6j5xpJd/Ajuda-server.png[/IMG]]("https://postimg.cc/R6j5xpJd")

---

### Post by darkod on 2020-04-24
I will let Doug to confirm, because as I said I haven't worked with VBox without bridge that much.

But I see multiple problems here:
1. You assigned 10.0.2.15 as internal IP to both server and client. You shouldn't do that, they need different IPs. If they can belong to the same NATed subnet, assign IPs from same subnet (but different IPs). If they belong to different NATed subnets, they will have IPs from different subnets.
2. You have assigned 192.168.56.50 and .60 from inside the VMs too. It shouldn't be like that unless I'm mistaken. If those IPs are used on the host side you shouldn't also assign them inside the VMs.

Looks like the whole VBox + NAT thing is confusing you. You seem to treat it almost as if host and VMs are on same LAN but they are not (the virtual NAT in VBox takes care to separate them).

You also need to think how ipv4 routing works in this situation. Not sure up to what level VBox is intelligent about this or you need to make sure VMs and host can route traffic correctly using static routes you made yourself.

---

### Post by mpugliesi2 on 2020-04-24
I am trying to understand, but look. those IPs are not my fault!

Look the assignment:

```
The connectivity must include the ability of each computer to PING the other computer and
for each computer to have Internet connectivity. For the host-only adapter, use temporary
network configurations, you can use the ip command. The ip command allows you to
configure settings which take effect immediately, however they are not persistent and will be
lost after a reboot. Next, create a web server and web client on the two computers.


**ubuntuserver IP addressing: [Adapter1 should be on NAT and adapter2**
**should be on Host-Only]**
**Adapter 1(enp0s3): address will be obtained from internal DHCP server (most**
**likely 10.0.2.15)**
**Configure the Adaptor 2(enp0s8): IP = 192.168.56.50 / SNM = 255.255.255.0**



**ubuntuclient IP addressing: [Adapter1 should be on NAT and adapter2 should**
**be on Host-Only]**
**Adapter 1(enp0s3): address will be obtained from internal DHCP server (most**
[B]likely 10.0.2.15)
 Adaptor 2(enp0s8): IP = 192.168.56.60 / SNM = 255.255.255.0[/B]

```

Blame the teacher for that!  :)

---

### Post by Doug S on 2020-04-24
> **mpugliesi2 said:**
> Both VM are inside virtualbox in my notebook, that is why I have a  fast ping response.So was my example.

I don't know what is going on, but it does not look correct to me. But like I mentioned before I don't use virtualbox. I also mainly use VMs bridged to the host LAN, but now have a few unbridged (KVM based) on a test 20.04 server

---

### Post by Doug S on 2020-04-24
> **mpugliesi2 said:**
> 
```
**ubuntuserver IP addressing: [Adapter1 should be on NAT and adapter2**
**should be on Host-Only]**
**Adapter 1(enp0s3): address will be obtained from internal DHCP server (most**
**likely 10.0.2.15)**
**Configure the Adaptor 2(enp0s8): IP = 192.168.56.50 / SNM = 255.255.255.0**

**ubuntuclient IP addressing: [Adapter1 should be on NAT and adapter2 should**
**be on Host-Only]**
**Adapter 1(enp0s3): address will be obtained from internal DHCP server (most**
[B]likely 10.0.2.15)
 Adaptor 2(enp0s8): IP = 192.168.56.60 / SNM = 255.255.255.0[/B]

```

My best guess, and it is a quess, is that it should read:

```
**ubuntuserver IP addressing: [Adapter1 should be on NAT and adapter2**
**should be on [COLOR="#FF0000"]Quest[/COLOR]-Only]**
**Adapter 1(enp0s3 [COLOR="#FF0000"](on host)[/COLOR]): address will be obtained from internal DHCP server (most**
**likely 10.0.2.15)**
**Configure the Adaptor 2(enp0s8): IP = 192.168.56.50 / SNM = 255.255.255.0**

**ubuntuclient IP addressing: [Adapter1 should be on NAT and adapter2 should**
**be on [COLOR="#FF0000"]Quest[/COLOR]-Only]**
**Adapter 1[COLOR="#FF0000"](enp0s3 (on host, and the same one as above))[/COLOR]: address will be obtained from internal DHCP server (most**
[B]likely 10.0.2.15)
 Adaptor 2(enp0s8): IP = 192.168.56.60 / SNM = 255.255.255.0[/B]

and there should only be one vboxnet with an address of 192.168.56.1 on the host.

```

---

### Post by darkod on 2020-04-24
According to host-only explication here: [https://blogs.oracle.com/scoter/networking-in-virtualbox-v2](https://blogs.oracle.com/scoter/networking-in-virtualbox-v2)

The fault is that you created separate host-only adapters/devices for the two VMs. If the idea is the server and client VM to communicate, they need to be on the same vboxnet0 host-only adapter.

PS. In general helping others with assignments is against forum rules. Please figure it out fast with what we have put here because we shouldn't be doing this. :)

---

### Post by mpugliesi2 on 2020-04-24
Unfortunately not! And can tell you why. If the Host system is Windows, this configuration works! I repeated the same configuration he is asking with a friend on Windows and it works! Teacher uses a MacBook and also works.  If I can't find a solution I will use Windows instead.  I need the marks! I would prefer to do it on Linux.

---

### Post by mpugliesi2 on 2020-04-24
Ok. Thanks. I will give a try!

---

### Post by mpugliesi2 on 2020-04-24
> **darkod said:**
> According to host-only explication here: [https://blogs.oracle.com/scoter/networking-in-virtualbox-v2](https://blogs.oracle.com/scoter/networking-in-virtualbox-v2)

The fault is that you created separate host-only adapters/devices for the two VMs. If the idea is the server and client VM to communicate, they need to be on the same vboxnet0 host-only adapter.

PS. In general helping others with assignments is against forum rules. Please figure it out fast with what we have put here because we shouldn't be doing this. :)


Thanks a Million Man!!!  It works!!!

I will mark as solved!!!

---

