---
title: "Multipass Networking, how do I bridge from Network to Network?"
date: 2022-04-23
forum: Virtualisation
---

### Post by ctrl-alt-delete on 2022-04-23
Please bare with me as I am new to this!

I have a few multipass VM's running on Ubuntu 20.04 LTS and want to make this machine headless and control everything from Mac OS X.

my main network is 192.168.178.0

I can ssh to the Ubuntu Server on the same network 192.168.178.0 and run the multpass shell command to do Command-line admin but I want to use other tools on my Mac OS X.

My question is how can I configure to go directly to the 192.168.122.0 network from my Mac on network 192.168.178.0 or other hosts on the network?  

I want to use JetBrains tools such as DataGrip to administer a Postgres DB and want to be able to have a browser to have access to the VM's and any software deployed.

My UBUNTU VM's:

Name State IPv4 Image
db-server Running 192.168.122.207 Ubuntu 20.04 LTS


I also have a microK8s cluster with 3 nodes:


node1                   Running           192.168.122.176  Ubuntu 20.04 LTS
                                          10.1.166.128

node2                   Running           192.168.122.55   Ubuntu 20.04 LTS
                                          10.1.104.0

node3                   Running           192.168.122.97   Ubuntu 20.04 LTS
                                          10.1.135.0

How would I configure network to access the web portal to manage microK8s from the Mac OSX?


The reason I set this up is to learn DEVOPs, Kubernetes, docker and containers.

Would I be better off using OpenShift or sticking with the above?

I also have Microsoft Remote Desktop on the Mac to connect remotely to the Ubuntu server, I could also install the JetBrains Dev products on the Ubuntu server and remote to dev locally but that just feels wrong.  I should be able to have all admin tools local and be able to connect to any VM's.

---

### Post by Doug S on 2022-04-23
I do not know about some of the things you are doing, but would it make sense to put your VMs directly on your 192.168.178.0 sub-net? I always do my VMs that way. Exactly how depends a little on the host VM stuff hypervisor, but the bridging should be the same. Example:

```
doug@s19:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.136/24 brd 192.168.111.255 scope global dynamic br0
       valid_lft 56651sec preferred_lft 56651sec
8: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:22:2f:dc brd ff:ff:ff:ff:ff:ff
9: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:3e brd ff:ff:ff:ff:ff:ff
10: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:5e brd ff:ff:ff:ff:ff:ff

doug@s19:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
[COLOR="#FF0000"]br0[/COLOR]             8000.3c7c3f0d9983       no              [COLOR="#FF0000"]enp3s0[/COLOR]
                                                        [COLOR="#FF0000"]vnet0[/COLOR]
                                                        [COLOR="#FF0000"]vnet1[/COLOR]
                                                        [COLOR="#FF0000"]vnet2[/COLOR]

``` and on one of the 3 the VMs:
```
doug@desk-ff:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 52:54:00:22:2f:dc brd ff:ff:ff:ff:ff:ff
    inet [COLOR="#FF0000"]192.168.111.19/24[/COLOR] brd 192.168.111.255 scope global dynamic noprefixroute enp1s0
       valid_lft 86210sec preferred_lft 86210sec
    inet6 fe80::205d:ae9c:1583:7116/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```

---

### Post by TheFu on 2022-04-23
If 192.168.178.0/24 is the main subnet and multipass (which I've never gotten to work, ever) is using 192.168.122.0/24, then I suspect the .122.x subnet is a NAT subnet only accessible by the Linux host.  In short, you can't get there from the Mac.  It might be possible to setup routing from the main network to the NAT subnet, but that seems overly complex.  Just put the VMs on a bridge, which will share the same LAN.  If you care about security, then you'll want a separate PCIe passthru NIC for each VM's exclusive use.  Normal, shared bridges have been found to be less secure, allowing different client VMs or containers access to traffic meant for a different VM/container or by the host. It ain't good for security.

I don't know enough to comment about the other stuff. I've been doing virtualization since the 1990s, but never jumped to K8 or docker. My employers don't use those. We use KVM for full VMs and lxd for containers with fewer than 20 physical hosts, it is just starting to become complex enough to want something else.  Most of my clients have under 5 physical servers these days, so openshift would be overly complex.

And I haven't touched a MacOS machine since the 3 weeks of terrible experience around 2011.
Ubuntu Server doesn't have any GUI, so ssh is how they are managed ... or using a devops tool, which works .... over ssh.

The way that I do remote VM management beside ssh (used 99.9999% of the time) is using virt-manager which makes an ssh-tunnel to the remote KVM host and connects to either server or desktop instances using the SPICE protocol.  On Windows, the tool used to connect to SPICE is **virt-viewer**. I think there's a MacOS version, but since this is used extremely seldom, it is only useful if you have your main desktop running inside a VM - which is what I do.  Alas, I use virt-viewer from my Linux workstation to access my main desktop from the LAN and use x2go to access it over the internet where performance is expected to be massively less.

From a different system, the connection command looks like this (it is in a script):
```
 /usr/bin/virt-viewer --connect qemu+ssh://hadar/system regulus &
```
regulus is a 20.04 desktop running fvwm as the window manager, but it also has Mate desktop, if I need something bloated. Really, I haven't bothered to clean off all the mate-* packages.  'regulus' is the VM name within libvirt, but it is also the hostname.  'hadar' is the VM host machine.  So, if I'm on a laptop downstairs - named 'posc', that's the command to connect to hadar, request a SPICE connections over an ssh tunnel to regulus to access a full desktop. It is fast enough for video playback, but not fast enough for fps gaming.

CloudDev means 10,000 different things to 10,000 different people.  Hard to know where you are going with that term.  I suspect it is a dog whistle term for controlling systems on the big vps/container providers and has very little to do with actual programming.

---

### Post by DuckHook on 2022-04-25
@OP

Please use default fonts and styles when posting. Odd fonts and styles render improperly on some browsers and are difficult to read.

---

