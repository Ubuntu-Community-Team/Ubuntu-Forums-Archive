---
title: "Linux Bridge Looses Connection to Internet"
date: 2019-05-17
forum: Virtualisation
---

### Post by dman7773 on 2019-05-17
Even though this is networking, I guess it would go here since it is to get my KVM going. 

I am running Ubuntu Xenial LTS.


I am adding a linux bridge.


With no bridge, my ethernet works with no issues. I use static ip 192.168.3.57 with my router. But when I create a Linux bridge I loose internet connection.  Any ideas why?


Here is my info:


```
    one@localhost:~$ route -n
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 enp37s0
    192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 enp37s0

```

------


```
    one@localhost:~$ ifconfig 
    enp37s0   Link encap:Ethernet  HWaddr 70:85:c2:7c:fa:ec  
              inet addr:192.168.3.57  Bcast:192.168.3.255  Mask:255.255.255.0
              inet6 addr: fe80::7285:c2ff:fe7c:faec/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:12496 errors:0 dropped:0 overruns:0 frame:0
              TX packets:9955 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:7131864 (7.1 MB)  TX bytes:1643970 (1.6 MB)
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:166 errors:0 dropped:0 overruns:0 frame:0
              TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:12412 (12.4 KB)  TX bytes:12412 (12.4 KB)



```--------
```


    brctl addbr br0 tunctl -u 
    kvmuser -t tap0 ifconfig enp37s0 up 
    ifconfig tap0 up 
    brctl addif br0 enp37s0 
    brctl addif br0 tap0
    ifconfig br0 192.168.3.57 netmask 255.255.255.0 up
    route add default gw 192.168.3.1



```

---------------------


Note, also, when I add the default gateway I get file exists message. Checking I see:


```
    root@localhost:/home/one# ip route list
    default via 192.168.3.1 dev enp37s0
    192.168.3.0/24 dev enp37s0  proto kernel  scope link  src 192.168.3.57

```

---

### Post by tomh0665 on 2019-05-17
You need to de-configure enp37s0 and only run "ifconfig enp37s0 up" before adding it to br0; just like tap0.

---

### Post by dman7773 on 2019-05-17
> **tomh0665 said:**
> You need to de-configure enp37s0 and only run "ifconfig enp37s0 up" before adding it to br0; just like tap0.


Thank you. 

Ok, I have it to where it doesn't come up but I am still not having success. Here is what I did:

  ```
root@localhost:/home/one# brctl addbr br0root@localhost:/home/one# tunctl -u kvmuser -t tap0
Set 'tap0' persistent and owned by uid 999
root@localhost:/home/one# ifconfig tap0 up
root@localhost:/home/one# ifconfig enp37s0 up
root@localhost:/home/one# brctl addif br0 enp37s0
root@localhost:/home/one# ifconfig br0 192.168.3.57 netmask 255.255.255.0 up
root@localhost:/home/one# route add default gw 192.168.3.1
root@localhost:/home/one# ifconfig 
br0       Link encap:Ethernet  HWaddr 70:85:c2:7c:fa:ec  
          inet addr:192.168.3.57  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::7285:c2ff:fe7c:faec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16326 (16.3 KB)  TX bytes:9003 (9.0 KB)


enp37s0   Link encap:Ethernet  HWaddr 70:85:c2:7c:fa:ec  
          inet6 addr: fe80::7285:c2ff:fe7c:faec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:4 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19088 (19.0 KB)  TX bytes:9729 (9.7 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:189512 (189.5 KB)  TX bytes:189512 (189.5 KB)


tap0      Link encap:Ethernet  HWaddr ca:75:a8:f3:8b:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

------

```

root@localhost:/home/one# ip route list
default via 192.168.3.1 dev br0 
192.168.3.0/24 dev br0  proto kernel  scope link  src 192.168.3.57 
```

-------

```
 root@localhost:/home/one# cat /etc/network/interfaces# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
manual enp37s0
iface enp37s0 inet static 
address 192.168.3.57
netmask 255.255.255.0
gateway 192.168.3.1
dns-nameservers 8.8.4.4 8.8.8.8

```

---

### Post by TheFu on 2019-05-18
I configure my bridges in the "interfaces" file for 16.04.  That won't work for 18.04 and later.  I only deal with LTS, so don't know when the change happens.  Also, I don't keep up with release code words. Is Xen... 16.04?

This works - just change the device name for yours and leave the loopback device stanza in the file alone.
```
# ####################################
# The primary network interface
auto enp3s0
iface enp3s0 inet manual

# ####################################
auto br0
iface br0 inet static
  address 192.168.3.57 
  gateway 192.168.3.1
  netmask 255.255.255.0
  dns-nameservers 1.1.1.1 1.0.0.1
  bridge_ports enp3s0
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off
```

This doesn't use a tap interface.  When I was setting these up back in around 2010, tap had  performance issues.

---

### Post by tomh0665 on 2019-05-22
If you're setting all of your networking via ifupdown:


allow-auto lo
iface lo inet loopback


allow-auto enp37s0
iface enp37s0 inet manual
        bond-master br0


allow-auto br0
iface br0 inet static
        address 192.168.0.242/24
        gateway 192.168.0.1
        pre-up ip tuntap add dev tap0 mode tap user <user>
        pre-up ip link set tap0 up
        bridge_ports eth0 tap0
        post-down ip link set tap0 down
        post-down ip tuntap del dev tap0 mode tap

---

### Post by TheFu on 2019-05-23
Should 
```
bridge_ports eth0 tap0
```
be
```
bridge_ports enp37s0  tap0
```

And is 
```
address 192.168.0.242/24
```
supported in 16.04, with the netmask merged?  Ah - it is. 

Think
```
address 192.168.3.57/24
```
is what the OP would prefer.

---

### Post by dman7773 on 2019-05-26
> **TheFu said:**
> 
This doesn't use a tap interface.  When I was setting these up back in around 2010, tap had  performance issues.

Interesting.... What did you use instead of tap? Direct hardware pass through? Can that be done with a network card?

---

### Post by TheFu on 2019-05-26
> **dman7773 said:**
> Interesting.... What did you use instead of tap? Direct hardware pass through? Can that be done with a network card?

Neither are options in the ifupdown tools.  I've never used the 'ip' command for anything non-trivial and only for looking up data, never setting anything.

Tunnels and taps are related to VPNs.  In openVPN, tap interfaces have different limitations than tun interfaces, mainly performance.  I don't recall the specifics from a decade ago, but decided I never wanted to use tap interfaces in my networks because we didn't need to support the protocols that only work with tap and didn't want the performance hit.

Or perhaps my memory is gone and I'm wrong.  I can say that my 20 openvpn setups all use tun, not tap.

---

### Post by tomh0665 on 2019-05-26
Yes. I was just giving an example using the kernel name of a first detected NIC and a basic IP address.

---

