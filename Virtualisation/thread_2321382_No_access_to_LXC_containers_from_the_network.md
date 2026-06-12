---
title: "No access to LXC containers from the network"
date: 2016-04-22
forum: Virtualisation
---

### Post by mmg4 on 2016-04-22
Following the steps described in [https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/](https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/) and some other tutorials, I set up a bridged configuration to make my LXC containers visible in the network. So far, I'm able to ping the containers from the host and vice versa, but not from the network. The host can be pinged from the network. Tests were performed under a fresh installation of Ubuntu Server 16.04, bridge-utils installed, lxdbr0 disabled, no firewall rules. All IPs are static. 

```

# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        bridge_ports ens160
        bridge_stp on
        bridge_fd 0
        bridge_waitport 0
        address 172.16.1.10
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.254
        dns-nameservers 172.16.1.2
        dns-search mydomain.de

# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:50:56:af:1c:0a brd ff:ff:ff:ff:ff:ff
    inet6 fe80::250:56ff:feaf:1c0a/64 scope link
       valid_lft forever preferred_lft forever
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:50:56:af:1c:0a brd ff:ff:ff:ff:ff:ff
    inet 172.16.1.10/24 brd 172.16.1.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:feaf:1c0a/64 scope link
       valid_lft forever preferred_lft forever
5: veth4LJE6P@if4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0 state UP group default qlen 1000
    link/ether fe:6e:1d:4e:99:36 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::fc6e:1dff:fe4e:9936/64 scope link
       valid_lft forever preferred_lft forever

# brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.005056af1c0a       yes             ens160
                                                        veth4LJE6P

# cat /etc/default/lxd-bridge
USE_LXD_BRIDGE="false"
LXD_BRIDGE=""
...

# lxc info tc1
Name: tc1
Architektur: x86_64
Created: 2016/04/21 13:26 UTC
Status: Running
Type: persistent
Profiles: bridge
Pid: 3639
Ips:
  eth0: inet    172.16.1.20   veth4LJE6P
  eth0: inet6   fe80::216:3eff:febb:b5da        veth4LJE6P
  lo:   inet    127.0.0.1
  lo:   inet6   ::1
Resources:
  Processes: 18
  Disk usage:
    root: 62.23MB
  Memory usage:
    Memory (current): 70.39MB
    Memory (peak): 116.78MB
  Network usage:
    eth0:
      Bytes received: 6.35MB
      Bytes sent: 16.29kB
      Packets received: 74256
      Packets sent: 387
    lo:
      Bytes received: 9.14kB
      Bytes sent: 9.14kB
      Packets received: 116
      Packets sent: 116

# lxc profile show bridge
name: bridge
config:
  environment.http_proxy: http://[fe80::1%eth0]:13128
  user.network_mode: link-local
description: ""
devices:
  eth0:
    name: eth0
    nictype: bridged
    parent: br0
    type: nic

# lxc exec tc1 -- cat /etc/network/interfaces.d/eth0.cfg
auto eth0
iface eth0 inet static
        address 172.16.1.20
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.254
        dns-nameservers 172.16.1.2
        dns-search mydomain.de

```

I also tested the macvlan setup described in the link mentioned before. In the macvlan setup just the containers can ping each other.

Did I forget something? Any help would be appreciated, thanks!

---

### Post by MAFoElffen on 2016-04-22
Out the door and will be back. Meantime hint... in interfaces, you forgot to bring up ens160 as auto, manual... Will post my own file when I get back home tonight...

---

### Post by mmg4 on 2016-04-23
I already tried that with no effect.

```

# cat /etc/network/interfaces
auto ens160
iface ens160 inet manual

auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        bridge_ports ens160
        bridge_stp on
        bridge_fd 0
        bridge_waitport 0
        address 172.16.1.10
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.254
        dns-nameservers 172.16.1.2
        dns-search mydomain.de

```

---

### Post by MAFoElffen on 2016-04-23
Have you installed the bridge-utils package already?

---

### Post by mmg4 on 2016-04-25
Yes, bridge-utils are installed.

BTW, network access to container works fine when container's nictype is set to "physical". But that's not what I wanted...

```

# lxc profile show physical
name: physical
config:
  environment.http_proxy: http://[fe80::1%eth0]:13128
  user.network_mode: link-local
description: ""
devices:
  eth0:
    name: eth0
    nictype: physical
    parent: ens192
    type: nic

# lxc profile apply tc1 physical

```

---

### Post by MAFoElffen on 2016-04-25
Is that from LXC conf or the specific container template conf?

---

### Post by mmg4 on 2016-04-25
I defined a new profile "bridge" by copying it from "default", changed it's settings with "lxc profile edit brigde" and applied it to my container with "lxc profile apply tc1 bridge". So, it's container specific, right? The LXC default conf hasn't been changed.

---

### Post by Plecebo on 2016-04-25
I'm having similar issues accessing web servers on guest containers setup with bridged networking. 

I'll be looking closer at my configuration to see if I missed something. 

I've been roughly following the LXD 2.0 guide: [http://insights.ubuntu.com/2016/03/14/the-lxd-2-0-story-prologue/](http://insights.ubuntu.com/2016/03/14/the-lxd-2-0-story-prologue/) and most things work ok, except accessing the container from other machines.

Any specific troubleshooting that might help identify where the issues are?

---

### Post by MAFoElffen on 2016-04-26
> **mmg4 said:**
> I defined a new profile "bridge" by copying it from "default", changed it's settings with "lxc profile edit brigde" and applied it to my container with "lxc profile apply tc1 bridge". So, it's container specific, right? The LXC default conf hasn't been changed.
Yes, sort-of. Not really how you do that.

Think of the template profile as what your "Preferred Preferences" are. For example, if you were using something else, such as VirtualBox or AMware Player, this would be your program preferences. When yopu go to download, insall and configure an image... on install of that image file, for anything were you do not say you want something "different", it uses the template file for the options. For instance, for which ntwrk, netword IP range to assign for containers spawned from that image, etc.

When someone refers to "Bridge" itself, usually that word denotes that there was a network bridge installed and configures so that there is a virtual network path to the host's external network, using the same network ID. Default external connection is using tne brlxc, which is a NAT, Network Address Translation. Most people do not understand, that is goes through the same host NIC card, but is in another ntework address range than the Host. Has internet, but cannot talk to Host network without further tweaking...)

So, I go back to ask if you actually installed a network bridge, and what steps did you use to create it? On your container type mage that you are calling "Bridge" ... how did you install that again" (What besides just creating a profile from the default template profile.)

---

### Post by MAFoElffen on 2016-04-26
> **Plecebo said:**
> I'm having similar issues accessing web servers on guest containers setup with bridged networking. 

I'll be looking closer at my configuration to see if I missed something. 

I've been roughly following the LXD 2.0 guide: [http://insights.ubuntu.com/2016/03/14/the-lxd-2-0-story-prologue/](http://insights.ubuntu.com/2016/03/14/the-lxd-2-0-story-prologue/) and most things work ok, except accessing the container from other machines.

Any specific troubleshooting that might help identify where the issues are?
Would you like me to split your post out to your own thread for support?

This new, sudden influx of threads, all on virtual networking questions... Mostly having to do with LXC/LXD > Becuase of it being released as a default package of 16.04 LTS Server... I'm thinking if a thread explaining virtual networking on Ubuntu Server would help with this.

---

### Post by mmg4 on 2016-04-26
> **MAFoElffen said:**
> 
So, I go back to ask if you actually installed a network bridge, and what steps did you use to create it? On your container type mage that you are calling "Bridge" ... how did you install that again" (What besides just creating a profile from the default template profile.)

I installed the bridge by installing bridge-utils and adding a bridge in /etc/network/interfaces.

All installation steps in detail:
1. Installed Ubuntu Server 16.04 + bridge-utils + zfsutils-linux; static IP
2. Executed lxd init, set up ZFS store
3. Disabled lxdbr0 by setting USE_LXD_BRIDGE="false" and LXC_BRIDGE="" in /etc/default/lxd-bridge
4. Added bridge in /etc/network/interfaces:
```

auto ens160
iface ens160 inet manual
auto br0
iface br0 inet static
        bridge_ports ens160
        bridge_stp on
        bridge_fd 0
        bridge_waitport 0
        address 172.16.1.10
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.254
        dns-nameservers 172.16.1.2
        dns-search mydomain.de

```
5. Created container "tc1" with ```
lxc launch ubuntu:x tc1
``` and afterwards stopped container
6. Created copy of profile "default": ```
lxc profile copy default bridge
```
7. Modified profile "bridge": ```
lxc profile device set bridge eth0 nictype bridged
``` and 
```
lxc profile device set bridge eth0 parent br0
```
8. Applied profile "bridge" to container "tc1": ```
lxc profile apply tc1 bridge
```
9. Started container "tc1", opened shell in container "tc1" with ```
lxc exec tc1 bash
``` and changed container's IP config to static:
```

# cat /etc/network/interfaces.d/50-cloud-init.cfg
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

# cat /etc/network/interfaces.d/eth0.cfg
auto eth0
iface eth0 inet static
        address 172.16.1.20
        netmask 255.255.255.0
        network 172.16.1.0
        broadcast 172.16.1.255
        gateway 172.16.1.254
        dns-nameservers 172.16.1.2
        dns-search mydomain.de

```
10. Rebooted host

---

### Post by Plecebo on 2016-04-26
> Would you like me to split your post out to your own thread for support?
Thank you for the offer but I was able to figure out my problem and it was not related to containers it was application configuration, so I don't need support for this issue anymore. 

> This new, sudden influx of threads, all on virtual networking questions... Mostly having to do with LXC/LXD > Becuase of it being released as a default package of 16.04 LTS Server... I'm thinking if a thread explaining virtual networking on Ubuntu Server would help with this.
I would guess that is exactly the reason for the influx. I had been using privileged lxc containers before but i'm trying out unprivileged LXD containers in my new build. A guide would be very helpful.

---

### Post by Plecebo on 2016-04-26
> gateway 172.16.1.254

this looks strange to me. Is your gateway/router really 172.16.1.254

On my network the gateway is 192.168.100.1 and my ip's are all > gateway. Not sure this will fix your issue but this would be where I look.

---

### Post by mmg4 on 2016-04-27
OK, the IPs in my post are not the real ones. Our network is class B and the gateway in my subnet lies in fact at xxx.xxx.xxx.254. Anyway - the container can't even be pinged from the same subnet.

---

### Post by MAFoElffen on 2016-04-27
> **mmg4 said:**
> OK, the IPs in my post are not the real ones. Our network is class B and the gateway in my subnet lies in fact at xxx.xxx.xxx.254. Anyway - the container can't even be pinged from the same subnet.
That is understandable, and common sense... Thanks for mentioning that, so we know. 

Just glanced at your output last night. <> But also had a final paper due for this morning. (i'm not young, but back in college documenting my skillset.) Promise I'll go through it tonight in more detail. 


Briefly about post #11: And you installed the package "bridge-utils" right?

---

### Post by mmg4 on 2016-04-27
> **MAFoElffen said:**
> 
Briefly about post #11: And you installed the package "bridge-utils" right?

Well, I just executed "apt install bridge-utils". Are the more steps to perform, besides adding a bridge to /etc/network/interfaces?

---

### Post by MAFoElffen on 2016-04-28
Just one of two things...

In one dierection (if took), doing what you did in your interfaces file, which was to set one NIC to manual, then map a bridge to that NIC.

The other would be to create and/or edit the individual network device files... which you didn't.

Third is to use brctl commands to create a bridge, which you didn't.

So, getting this straight in my head:
1. br0 is your dedicated network bridge (bridge-utils and defined in interfaces)
2. bridge is a template profile, that you copied/created from the default template.
3. tr1 is your container using the "bridge" profile as a template...

and br0 is the network bridge we are having troubles with?

Am I /understanding/following that correctly?
--> but explain where you saw that

---

### Post by mmg4 on 2016-04-28
> **MAFoElffen said:**
> 
1. br0 is your dedicated network bridge (bridge-utils and defined in interfaces)
2. bridge is a template profile, that you copied/created from the default template.
3. tr1 is your container using the "bridge" profile as a template...

and br0 is the network bridge we are having troubles with?

Am I /understanding/following that correctly?


You're right, that's the situation. The bridge br0 was created automatically after adding it to /etc/network/interfaces, so I supposed there was no need for "brctl addbr br0". The bridge seems to be set up correctly:

```

# brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.005056af1c0a       yes             ens160
                                                        vethNAF6QJ

```


> **MAFoElffen said:**
> --> but explain where you saw that

I've been inspired by [https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/](https://insights.ubuntu.com/2016/04/07/lxd-networking-lxdbr0-explained/).

---

### Post by MAFoElffen on 2016-05-01
Okay... through testing a bridge trough a single host NIC...

The simplest way to as a default fopr containers you build would be 
```

lxc profile device set default eth0 parent eth0
lxc profile device set default eth0 nictype macvlan

```
For just your old container, as a test, edit your container config file for your container and set the network settings to:
```

lxc.network.type = macvlan
lxc.network.macvlan.mode = bridge
lxc.network.hwaddr = 00:16:3c:4F:05:d1
lxc.network.flags = up
lxc.network.link = [COLOR=#000000][FONT=Ubuntu Mono]ens160[/FONT][/COLOR]
lxc.network.ipv4 = [COLOR=#000000][FONT=Ubuntu Mono]172.16.1.101[/FONT][/COLOR]/24

```
And set your host etc/network/interface file back to stock, with dhcp or static for ens160 ... that way macvlan is sharing a different layer of that NIC...

---

### Post by mmg4 on 2016-05-02
> **MAFoElffen said:**
> 
For just your old container, as a test, edit your container config file for your container and set the network settings to:
```

lxc.network.type = macvlan
lxc.network.macvlan.mode = bridge
lxc.network.hwaddr = 00:16:3c:4F:05:d1
lxc.network.flags = up
lxc.network.link = [COLOR=#000000][FONT=Ubuntu Mono]ens160[/FONT][/COLOR]
lxc.network.ipv4 = [COLOR=#000000][FONT=Ubuntu Mono]172.16.1.101[/FONT][/COLOR]/24

```


Where can I edit these settings? Google tells me to look at /var/lib/lxc/<containername>/config, but in Ubuntu 16.04 the folder /var/lib/lxc doesn't exist any more. Maybe that's the configuration method for lxc-only systems?
So I created a new profile named "mvlan" by copying it from the default profile, edited its settings as follows and applied it to my container.
```

lxc profile device set mvlan eth0 parent ens160
lxc profile device set mvlan eth0 nictype macvlan
```

The result is the same: No access to the container from the network and vice versa.
I also edited the default profile as described in your last post, launched a new container and set up the container's network - also the same problem.

As already mentioned before: Network access to containers works fine if I set nictype to "physical".

---

### Post by MAFoElffen on 2016-05-04
But setting to "physical" takes over the whole nic for that container, right? meaning your host and other containers can no longer use that NIC... no sharing of that NIC right?

On file location... remind me, yours is "LXD"? Privileged or un-privileged container? (created as a user or as root?)

---

### Post by mmg4 on 2016-05-04
> **MAFoElffen said:**
> But setting to "physical" takes over the whole nic for that container, right? meaning your host and other containers can no longer use that NIC... no sharing of that NIC right?


Yes, that's right. I just tried the "physical" configuration to ensure that the connection problem is not caused by the network or the container network config.

> **MAFoElffen said:**
> 
On file location... remind me, yours is "LXD"? Privileged or un-privileged container? (created as a user or as root?)

My system has LXD only, no LXC config files as far as I can see. The containers are unprivileged.

---

### Post by MAFoElffen on 2016-05-04
will look for this in one of my new servers... when I get back home tonight.

---

### Post by mmg4 on 2016-06-08
Is there anyone who successfully set up linux containers with bridged network?
What were your configuration steps?

---

### Post by votsalo on 2016-08-17
shorewall and pound are two useful packages to enable incoming network  access to containers with a single public ip address.  I have used them  in various container platforms, such as openvz, LXC, LXD.

Shorewall  is a package for configuring iptables.  It works as a  firewall but also as a port mapper between host ports and container  ports.

Pound lets me route incoming HTTP and HTTPS traffic to different containers, according to the hostname in the URL that the user wants to access.  It  works with HTTPS too (thanks to SNI -- Server Name Indication).  I  used to install pound using "apt-get install pound", but lately I  compiled it and installed it from source, in order to get the latest SSL  changes.  So, while shorewall does one-to-one port mapping, pound does one-to-many port mapping specifically for HTTP and HTTPS.

I use Shorewall to do things like:
* Map incoming requests to host  port 7020 to container a.b.c.20 port 22.  This gives me direct ssh  access to a container from outside the host.
* Map incoming requests to host port 80 to container a.b.c.d port 80.  This routes web traffic to a web server container.
*  Map incoming requests to host port 80 to container a.b.c.d port 8080.   This routes HTTP traffic to an HTTP reverse proxy container which in  turn routes web traffic to several other containers.  I use pound for  the reverse proxy.
* Map incoming requests to host port 443 to  container a.b.c.d port 8443.  This routes HTTPS traffic to a reverse  proxy container which in turns routes requests to several other  containers.  I use the same container for HTTP and HTTPS, with pound.
* Map any other port I like to any container, for development/testing.
* Drop access to all other ports, that I did not explicitly map or allowed to reach the host.  This protects the host from various attacks.

Shorewall can also route outgoing network traffic from containers, with NAT, but LXC/LXD also do that, by default.

You can install shorewall like this:  apt-get install shorewall
Two very quick tips about using shorewall:
1.   It has various configuration templates.  Use the 2-interface template  to start with.  You can easily add a 3rd interface if you want it to  work with both the LXC and LXD interfaces.
2.  Use "shorewall  safe-start" and "shorewall safe-restart" after any reconfiguration, so  that you do not accidentally lock yourself out of a remote system.   Before answering "yes" to accept the changes, verify that you can still  ssh to the host.  It also helps to not have shorewall start  automatically, so you can reboot out of a bad iptables configuration.

---

### Post by mmg4 on 2016-10-05
Problem solved! My host runs as a VM under ESX. I had to set the vSwitch's Promiscuous Mode to "Accept" - et voilà, bridged networking between my containers and the network outside the VM works fine.
Thanks for all replies!

---

### Post by TheFu on 2016-10-08
> **mmg4 said:**
> Problem solved! My host runs as a VM under ESX. I had to set the vSwitch's Promiscuous Mode to "Accept" - et voilà, bridged networking between my containers and the network outside the VM works fine.
Thanks for all replies!

In the future, would be kind to mention that the host is running under ESX. Might have saved lots of time. Might not, but I bet nobody else saw that twist.  Even if running under a KVM VM, then LXD/LXC, would be good to mention that.  BTW, running a container host under a VM **is** a best practice to aid in isolating the containers from the OS running on the physical HW.

Also, thank you very much for telling us the root cause and solution and marking the thread solved. Each of those is extremely helpful for the community.

---

