---
title: "Ubuntu Server 18.04 partial network access"
date: 2018-12-19
forum: Server Platforms
---

### Post by nicolas-rietsch on 2018-12-19
Hi,

I recently installed Ubuntu server 18.04.

I'm using a static IPv4 address (a bond actually) with networkd as the renderer.
My proxy server is a pass-through appliance so no proxy has been set.
the ufw firewall is disabled.

I can run apt update with no issue.
I can ping internal systems by their fqdn without issue either.

Here are the issues though:
- ping [www.google.com](www.google.com) does resolve but never pings
- running apt install -y realmd sssd sssd-tools libnss-sss libpam-sss krb5-user adcli samba-common-bin returns: 
E: Package 'realmd' has no installation candidate
E: Package 'krb5-user' has no installation candidate
E: Package 'adcli' has no installation candidate
- running snap install canonical-livepatch hangs for a minute and then returns: error: unable to contact snap store
- running add-apt-repository ppa:ondrej/php just hangs and never goes anywhere

The network settings look good, the DNS are good, the forwarders on the DNS are good, the proxy plays no role and the firewall is disabled.

Can someone please tell me what is going on here?

---

### Post by LHammonds on 2018-12-19
Did you install using the Live DVD or the alternative / traditional installer?

---

### Post by nicolas-rietsch on 2018-12-19
I used the LiveDVD: [https://www.ubuntu.com/download/server/thank-you?country=US&version=18.04.1&architecture=amd64](https://www.ubuntu.com/download/server/thank-you?country=US&version=18.04.1&architecture=amd64)

The server is a Dell PowerEdge 1950 Mk3

---

### Post by nicolas-rietsch on 2018-12-21
Does anyone would have some troubleshooting ideas or provide guidance?

---

### Post by volkswagner on 2018-12-22
Can you ping 8.8.8.8?
Can you ping us.archive.ubuntu.com (or whatever mirror is in /etc/apt/sources.list)?
Can you ping 91.189.91.23?

What's the output of:
```
route
```

---

### Post by nicolas-rietsch on 2018-12-23
root@dns1:~# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

and it just sits there

cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main

ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.149) 56(84) bytes of data.

Same thing, it just sits there

route
Kernel IP routing table
Destination     Gateway             Genmask           Flags   Metric   Ref    Use    Iface
default            fw.domain.com   0.0.0.0              UG      0          0       0       bond0
192.168.0.0    0.0.0.0               255.255.255.0   U        0          0       0       bond0

ping fw.domain.com
PING fw.domain.com (192.168.0.1) 56(84) bytes of data.
64 bytes from fw.domain.com (192.168.0.1): icmp_seq=1 ttl=64 time=0.462 ms
64 bytes from fw.domain.com (192.168.0.1): icmp_seq=2 ttl=64 time=0.323 ms
64 bytes from fw.domain.com (192.168.0.1): icmp_seq=3 ttl=64 time=0.303 ms

ifconfig bond0
bond0: flags=5187<UP,BROADCAST,RUNNING,MASTER,MULTICAST>  mtu 1500
        inet 192.168.0.5  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::302d:30ff:feab:99b3  prefixlen 64  scopeid 0x20<link>
        ether 32:2d:30:ab:99:b3  txqueuelen 1000  (Ethernet)
        RX packets 3737289  bytes 561711718 (561.7 MB)
        RX errors 0  dropped 425882  overruns 0  frame 0
        TX packets 726579  bytes 64321500 (64.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[COLOR=#000000]
[/COLOR]

---

### Post by volkswagner on 2018-12-23
Well it seems there is a gateway issue, but it could also be a NAT issue.
Can you post your network config for static ip?

I have zero experience with networking in 18.04 and less than
zero experience with netplan (hopefully someone with more experience can chime in).

Additionally, testing with ping (ICMP) while ICMP is being blocked by an upstream firewall can
be an issue. If you think ping requests/replies may be blocked, you can try the following to see if you get a connection:
```
telnet smtp.gmail.com 25
```

With the old /etc/network/interfaces method, one thing that would commonly
be missed is setting the "network 192.168.0.0" stanza. This missed entry
would give similar symptom.

---

### Post by nicolas-rietsch on 2018-12-23
telnet smtp.gmail.com 25
Trying 74.125.198.109...

and, as usual, it just sits there.

Here is the network config:
cat /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: networkd
  ethernets:
    eports:
      match:
        name: eno*
  bonds:
    bond0:
      interfaces: [eports]
      addresses: [192.168.0.5/24]
      gateway4: 192.168.0.1
      nameservers:
        search: [domain.com]
        addresses: [192.168.0.5, 192.168.0.2, 192.168.0.3, 8.8.8.8, 8.8.4.4]    
      
      parameters:
        mode: 802.3ad
        lacp-rate: fast
        mii-monitor-interval: 100

I do not believe that I have a network issue as such; there are some outputs from another Linux server:

 ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.161) 56(84) bytes of data.
64 bytes from keeton.canonical.com (91.189.88.161): icmp_seq=1 ttl=45 time=129 ms
64 bytes from keeton.canonical.com (91.189.88.161): icmp_seq=2 ttl=45 time=125 ms
64 bytes from keeton.canonical.com (91.189.88.161): icmp_seq=3 ttl=45 time=131 ms
64 bytes from keeton.canonical.com (91.189.88.161): icmp_seq=4 ttl=45 time=133 ms

route
Kernel IP routing table
Destination     Gateway             Genmask            Flags   Metric  Ref     Use   Iface
default            fw.domain.com   0.0.0.0               UG      0         0        0      ens160
192.168.0.0    *                        255.255.255.0    U        0         0        0      ens160





telnet smtp.gmail.com 25
Trying 74.125.198.108...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 smtp.gmail.com ESMTP c132sm9184602oia.41 - gsmtp

---

### Post by LHammonds on 2018-12-25
yaml is EXTREMELY sensitive to spacing.  Please be sure to enclose CODE tags around your yaml configs so it will preserve the spacing so we can see if there are any issues in that area.

Is this a physical server or does it exist inside a virtual environment?

Is this other Linux server on the same subnet?  Is it 192.168.0.4 with a gateway of 192.168.0.1?

Once I learned that the default "live" install media did not support LVM or RAID, I have not used it.  I only install using the traditional (a.k.a. alternative) installer.

I started a thread long ago trying to document some of the important [differences between the two resultant servers](https://ubuntuforums.org/showthread.php?t=2390785) that went beyond what was mentioned (lvm+raid).  I do not see anything about networking differences.  The name of the netplan config files are different but I don't think that matters at all.

LHammonds

---

### Post by nicolas-rietsch on 2018-12-29
```

root@dns1:~# cat /etc/netplan/50-cloud-init.yaml
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
  version: 2
  renderer: networkd
  ethernets:
    eports:
      match:
        name: eno*
  bonds:
    bond0:
      interfaces: [eports]
      addresses: [192.168.0.5/24]
      gateway4: 192.168.0.1
      nameservers:
        search: [rietsch.us]
        addresses: [192.168.0.5, 192.168.0.2, 192.168.0.3, 8.8.8.8, 8.8.4.4]    
      parameters:
        mode: 802.3ad
        lacp-rate: fast
root@dns1:~#

```

This server is a Physical server Dell PowerEdge 1950; the other server, actually 4 of them, are all virtual running 16.04 and never had such issues.
All the servers are on the same subnet and same vlan.

There are two differences between this servers and the other ones (apart from the packages installed):
- This is a physical server, the other servers are virtual
- This server is running 18.04, all the other ones are 16.04

I don't have to run 18.04 on this one but wanted to have a more recent version to be more in sync with the rest of the Windows environment.

If my issue is uncommon and/or does not appear to have an easily resolution, I'll just reinstall the system with 16.04...

---

### Post by nicolas-rietsch on 2019-01-01
Thanks for your help guys.
Decided to go back to the good old 16.04.............

---

