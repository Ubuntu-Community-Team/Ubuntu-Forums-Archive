---
title: "Help me make ubuntu router"
date: 2023-03-29
forum: Server Platforms
---

### Post by hansyulian on 2023-03-29
Hi, I'm new to configuring home server and need help to configure my home server to add additional function as router + dhcp server + dns server + and switch. I use `dnsmasq` as the dhcp and dns server.
I need help for the configuration of `netplan`, `iptables`, and `dnsmasq`.
I have 5 interfaces: 
  - eno1 (to the router)
  - enp4s0 (to access point)
  - enp5s0 (to main pc)

here is my current config:

```
netplan:
```
network:
  version: 2
  renderer: networkd
  ethernets:
    lo:
      match:
        name: lo
      addresses:
        - 127.0.0.1/8
    eno1:
      dhcp4: yes
      optional: yes
    enp3s0:
      addresses:
        - 192.168.0.1/24
      optional: true
    enp4s0:
      addresses:
        - 192.168.1.1/24
      optional: true
```
dnsmasq
```
port=53
no-resolv
server=1.1.1.1
server=1.0.0.1
domain-needed
bogus-priv
local=/local/
domain=local
listen-address=127.0.0.1,192.168.1.1,192.168.0.1
expand-hosts
dhcp-range=192.168.0.100,192.168.0.200,255.255.255.0,24h
dhcp-range=192.168.1.100,192.168.1.200,255.255.255.0,24h
dhcp-option=option:router,0.0.0.0
dhcp-option=option:ntp-server,0.0.0.0
dhcp-option=option:dns-server,0.0.0.0
dhcp-option=option:netmask,255.255.255.0
dhcp-authoritative
cache-size=10000
min-cache-ttl=600

```
iptables:
```
*filter
:INPUT ACCEPT [1636:146818]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [989:130997]
-A FORWARD -i enp4s0 -o eno1 -j ACCEPT
-A FORWARD -i enp5s0 -o eno1 -j ACCEPT
-A FORWARD -i eno1 -o enp4s0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i eno1 -o enp5s0 -m state --state RELATED,ESTABLISHED -j ACCEPT
COMMIT
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o eno1 -j MASQUERADE
COMMIT

```


```

As the current config, i have 2 different ip address for each interface, 192.168.0.* and 192.168.1.*
As for now, my machine works as router well, but it still seems to be imperfect
I would like to make it to only use 192.168.0.* even for my machine that is connected to `enp4s0`, so i need help for the config to achieve this.

Thank You

---

### Post by TheFu on 2023-03-29
[https://www.kernel.org/doc/html/latest/networking/bridge.html](https://www.kernel.org/doc/html/latest/networking/bridge.html)

Basically, install the bridge-utils package and configure it in your netplan files.  Bridge setups are at netplan.io/examples

Seems you are confusing routing and bridging.  Routers require different subnets to know which interface to send packet.  Bridging doesn't.

I'd caution you against putting lots of services onto a single OS instance.  That way you can expect issues. The world used to do that in the 70s, 80, 90s, and we were constantly dealing with incompatible software stacks between the different services.  Better to logically split each service into a virtual machine or a linux container.  That way, they won't interfere with each other.

The way I address these needs is to have
ISP WAN Router - It is a Cisco thing with bridging to pass the static IPs to my WAN router.  It manages a 10.x.x.x subnet for untrusted devices. This is "outside" my network and treated like internet traffic. All WIFI is here too.
WAN Router - running OPNSense on dedicated hardware. Nothing fancy. Internet-WAN(red), trusted-LAN(green) subnets.
LAN Router - running OPNSense inside a VM with 3 NICs passed thru. This provides a few DHCP addresses for each subnet, but not enough that guests can be joined by plugging into open ports. DHCP reservations are provided for all normal mobile devices that change networks (laptops, tablets, phones) and for devices that do not provide any method of setting a static IP.
DNS - running on dual Linux containers (lxd/lxc) running pi-hole software for both DNS filtering and DNS caching. These are static IPs.

A well-managed network is a good thing.
[https://blog.jdpfu.com/2010/06/16/wireless-bridging-with-security-in-a-home-or-small-business](https://blog.jdpfu.com/2010/06/16/wireless-bridging-with-security-in-a-home-or-small-business) has a diagram for your consideration. Note how there a different subnets.  192.168.0/24 is untrusted.  192.168.50/24 is trusted.

So some untrusted devices can access the trusted network, I run a VPN server and have 1 port open to it.

---

### Post by SeijiSensei on 2023-03-29
Before you do anything, you have to edit (as root with sudo) /etc/sysctl.conf and remove the hash mark ("#") from the beginning of
```
#net.ipv4.ip_forward=1
```
That enables the kernel to pass packets between interfaces. That facility is blocked by default as a security measure. Run the command "sudo sysctl -p" or reboot to make the change take effect.

I know from nothing about netplan, etc., since I've always built routers from scratch using the traditional tools like ifconfig and route.

---

### Post by TheFu on 2023-03-29
> **SeijiSensei said:**
> Before you do anything, you have to edit (as root with sudo) /etc/sysctl.conf and remove the hash mark ("#") from the beginning of
```
#net.ipv4.ip_forward=1
```
That enables the kernel to pass packets between interfaces. That facility is blocked by default as a security measure. Run the command "sudo sysctl -p" or reboot to make the change take effect.

I know from nothing about netplan, etc., since I've always built routers from scratch using the traditional tools like ifconfig and route.

I think the OP really wants a bridge, not a router. He has routing working already, but wants the same subnet used on both sides.

---

### Post by hansyulian on 2023-03-30
i have done this

---

### Post by hansyulian on 2023-03-30
i just want a same ip for every internal interface: enp3s0 and enp4s0
so they can use 192.168.0.x address pool
i'm newbie in configuring router, so i would like to be able to learn to make one

---

### Post by TheFu on 2023-03-30
> **hansyulian said:**
> i just want a same ip for every internal interface: enp3s0 and enp4s0
so they can use 192.168.0.x address pool
i'm newbie in configuring router, so i would like to be able to learn to make one

And that isn't a router.  It is a bridge.  Use the bridge-tools to create a bridge.  Calling it a "router" is wrong and you'll get bad advice.

---

### Post by hansyulian on 2023-03-30
ok i managed to made it. so the final config are as follow:

[B]dnsmasq:
[/B]port=53
no-resolv
server=1.1.1.1
server=1.0.0.1
domain-needed
bogus-priv
local=/local/
domain=local
listen-address=127.0.0.1,192.168.0.1
expand-hosts
dhcp-range=192.168.0.100,192.168.0.200,255.255.255.0,24h
dhcp-option=option:router,0.0.0.0
dhcp-option=option:ntp-server,0.0.0.0
dhcp-option=option:dns-server,0.0.0.0
dhcp-option=option:netmask,255.255.255.0
dhcp-authoritative
cache-size=10000
min-cache-ttl=600[B]netplan:
[/B]network:
  version: 2
  renderer: networkd
  ethernets:
    lo:
      match:
        name: lo
      addresses:
        - 127.0.0.1/8
    eno1:
      dhcp4: yes
      optional: true
    enp3s0:
      dhcp4: false
    enp4s0:
      dhcp4: false
  bridges:
    br0:
      dhcp4: false
      addresses:
        - 192.168.0.1/24
      interfaces:
        - enp3s0
        - enp4s0
      parameters:
        stp: true[B]iptables:
[/B]*filter
:INPUT ACCEPT [1636:146818]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [989:130997]
COMMIT
*nat
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o eno1 -j MASQUERADE
COMMIT

---

### Post by TheFu on 2023-03-30
If you want anyone to look over the configs above, you'll need to edit the post and wrap them in 'code tags', which will retain the correct indentation.  YAML files are indentation sensitive, meaning, wrong indentation and it doesn't work.

Choose Edit Post, then Go Advanced, then use the "#" button just like any other bold/italic/quote tool - select the text to be rapped and click '#" from the editor toolbar.

And once the solution has been found, please, please, mark the thread as SOLVED using the thread tools button near the page top.  Only the person who created the thread can do that. It toggles a specific flag in the forum DB and others can search on 'solved' threads only.

---

