---
title: "[SOLVED] Guest unable to connect to http - KVM, ubuntu16, NAT"
date: 2017-03-28
forum: Virtualisation
---

### Post by drewbun2 on 2017-03-28
Hello,

I'm fairly new to Ubuntu (and linux). I'm attempting to do a very basic VM setup using KVM to create a centos7 box. This machine is unable to connect to the internet. Pretty much every site says "it should just work auto-magically!" I've been banging my head against a wall trying to figure out why its not for me. ](*,)

About the only thing I can do from the guest is ssh to the host. However, the host cannot ssh to guest (no open-ssh installed yet).

guest = app02@localhost
host = drew@drewbuntu


**Solution Update**
----------------------------------------------------------------------------------------------------------------------------------------
Issue Summary: when creating a guest, virbr0 is default taking the IP of the NAT server address, preventing traffic from routing back to the host.

Can be fixed 2 different ways:
1. When creating a guest, enable eth0 from the installer. This option is on the first screen during installation; the same screen you choose installation device, image specifications, etc.
2. To fix a guest that is already spun up:

1. connect to guest
2. run virsh net-edit default (as root)
  
[LIST]
[*]update IP to any non-host IP. I also updated the dhcp but i dont think this is necessary 
[/LIST]
 3. cd /etc/sysconfig/network-scripts/
  
[LIST]
[*]vim ifcfg-eth0 (as root and assuming eth0 is your default interface) 
[*]change line: ONBOOT=no to yes
[*]save + exit 
[/LIST]
 4. reboot machine

Machine should reboot with eth0 enabled and virbr0 set to a new IP!

Thanks for all the help! Should I report his as a bug?

----------------------------------------------------------------------------------------
**Resume Original Post**


**GUEST INFO**
ifconfig
```
 
[app02@localhost ~]$ ifconfig -a
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.122.146  netmask 255.255.255.0  broadcast 192.168.122.255
        inet6 fe80::1349:eb5b:fa83:2e06  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:d6:36:a8  txqueuelen 1000  (Ethernet)
        RX packets 109  bytes 8255 (8.0 KiB)
        RX errors 0  dropped 5  overruns 0  frame 0
        TX packets 51  bytes 8422 (8.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 648  bytes 54472 (53.1 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 648  bytes 54472 (53.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:be:14:6e  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0-nic: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 52:54:00:be:14:6e  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

iptables -L on guest
```

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24     ctstate RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere            

```


Attempt to ssh to guest
```
 drew@drewbuntu:~$ ssh 192.168.122.146
ssh: connect to host 192.168.122.146 port 22: No route to host
```

**HOST INFO**

ifconfig
```

drew@drewbuntu:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr 00:22:4d:56:8a:70  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::16b3:8a58:d76a:a654/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2407664 (2.4 MB)  TX bytes:470768 (470.7 KB)
          Interrupt:20 Memory:fba00000-fba20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:43528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:913836544 (913.8 MB)  TX bytes:913836544 (913.8 MB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:d6:36:a8  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7921 (7.9 KB)  TX bytes:1965 (1.9 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:d6:36:a8  
          inet6 addr: fe80::fc54:ff:fed6:36a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8663 (8.6 KB)  TX bytes:19177 (19.1 KB)


```

cat /proc/sys/net/ipv4/ip_forward  ```

sudo cat /proc/sys/net/ipv4/ip_forward
[sudo] password for drew: 
1
```

/etc/network/interfaces on host
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

iptables -L on host ```

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24     ctstate RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere            

```


kernal: 4.8.0-44-generic
I have attempted these troubleshooting steps already: [https://help.ubuntu.com/community/KVM/Networking#Troubleshooting](https://help.ubuntu.com/community/KVM/Networking#Troubleshooting)

I've got to be missing something stupid-easy...

---

### Post by karthick87 on 2017-03-29
So where is this http service running? I assume that it is running in your Guest Machine (which is a CentOS).

- Are you able to ping your Guest Machine (CentOS) from Host (Ubuntu 16) ?
- Are you trying to access the http service from the Host Machine?
- Try whether firewalld or iptables service is running on the server. If running, try to flip the services (just for troubleshooting purpose) and then retry.
- Also check whether selinux is in enforcing mode, set it to permissive mode and retry.

---

### Post by drewbun2 on 2017-03-29
So where is this http service running? I assume that it is running in your Guest Machine (which is a CentOS).
What I meant was that I cannot connect to the web via http; as in a web browser. Did i say that wrong or confusing?

- Are you able to ping your Guest Machine (CentOS) from Host (Ubuntu 16) ?
no. this is from host to guest```

drew@drewbuntu:~$ ping 192.168.122.146
PING 192.168.122.146 (192.168.122.146) 56(84) bytes of data.
From 192.168.122.1 icmp_seq=1 Destination Host Unreachable

```

- Are you trying to access the http service from the Host Machine?
see upper comment

- Try whether firewalld or iptables service is running on the server. If running, try to flip the services (just for troubleshooting purpose) and then retry.
good idea - didnt help though :/

- Also check whether selinux is in enforcing mode, set it to permissive mode and retry.
changed to permissive but didnt fix it

GUEST
```

[app02@localhost ~]$ sestatus
SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   permissive
Mode from config file:          permissive
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      28

```



HOST - was always disabled
```
drew@drewbuntu:~$ sestatus
SELinux status:                 disabled

```

---

### Post by Doug S on 2017-03-29
There are inconsistencies in your original post. It looks to me as though, at least sometimes, you have "guest" and "host" reversed in your descriptions.
For your "guest IP info:", which looks to me like it is actually "host IP info:", you should not have eth0 on the same sub-net as virbr0.
For your "/etc/network/interfaces on host" that makes no sense, however it does make sense if it is actually for the guest.
For your "iptables -L on guest" it looks like what I would expect on the host not on the guest.

---

### Post by drewbun2 on 2017-03-29
I updated OP to clarify and organize what is host, what is guest, and clarified that im trying to connect to the internet (not a local httpd service). But, i double checked and all values prior to the edit were correct (however disorganized!).

> **Doug S said:**
> 
For your "guest IP info:", which looks to me like it is actually "host IP info:", you should not have eth0 on the same sub-net as virbr0.
whatever is there was autopopulated by the kvm creation process... only thing ive done on the VM is turn on the network connection (it starts off)
> **Doug S said:**
> For your "/etc/network/interfaces on host" that makes no sense, however it does make sense if it is actually for the guest.
OP was correct, that is the contents of interfaces file... guest is centos and idk where that file is in that distro but i confirmed the machine is using dhcp

> **Doug S said:**
>  For your "iptables -L on guest" it looks like what I would expect on the host not on the guest.
OP was correct, both have similar rules regarding the x.x.122.0 subnet. included output from both for clarify. i can link the ENTIRE output if that will help.

---

### Post by KillerKelvUK on 2017-03-30
Have you installed any virt packages inside the guest/does the centos image you've install come with prepackaged virt?  As Doug is saying for your guest to have virbr0 adapters is unusual as these are typically created by libvirt on the host as the devices to support NAT.  I'm guessing the reason you cant access the web is because your guest doesn't have a default route that actually gets back to the hosts NAT interface, this is because virbr0 on your guest has an IP of 192.168.122.1 which I'm betting is the same address the nameserver listed in guests /etc/resolv.conf file or the centos equivalent.  I've just span up a kvm ubuntu guest and switched the interface to nat, using the default libvirt configurations on the host the guest has an IP allocation in the 192.168.122.0 /24 subnet and a default gateway address of 192.168.122.1, no reason to suspect why your defaults would be any different.

---

### Post by drewbun2 on 2017-03-30
wow. this problem is about to get a lot weirder.

I'm not sure why  the default setup messed up for my PC (open for ideas). But once i  set a static ip it fixed, but only for about 10 seconds!:

adapter: eth0
ip:          192.168.122.146
mask:     255.255.255.0
gateway: 192.168.122.1

DNS:       8.8.8.8
              192.168.122.1

**Evidence: starts download then fails when it loses Internet connection!**
```
[app02@localhost ~]$ sudo yum update
Loaded plugins: fastestmirror, langpacks
base                                                     | 3.6 kB     00:00     
extras                                                   | 3.4 kB     00:00     
updates                                                  | 3.4 kB     00:00     
extras/7/x86_64/primary_db     FAILED                                           
http://repo1.dal.innoscale.net/centos/7.3.1611/extras/x86_64/repodata/82e6f284e772607a560959e4d4aef6a6a3522cfc7570b0c46aad71e9f6dd3b19-primary.sqlite.bz2:  [Errno 12] Timeout on  http://repo1.dal.innoscale.net/centos/7.3.1611/extras/x86_64/repodata/82e6f284e772607a560959e4d4aef6a6a3522cfc7570b0c46aad71e9f6dd3b19-primary.sqlite.bz2:  (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last  30 seconds')
Trying other mirror.

```

**Attempt with DNS 8.8.8.8 & 8.8.4.4**
```
[app02@localhost proc]$ sudo yum update
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
 * base: centos.mirror.nac.net
 * extras: mirror.datto.com
 * updates: mirror.steadfast.net
updates/7/x86_64/primary_db    FAILED                                           
http://mirror.sigmanet.com/centos/7.3.1611/updates/x86_64/repodata/777a8e916abbbd45a2daaa57ed46a5b9235ff591503bedd37ebf63e0bf2fccd8-primary.sqlite.bz2: [Errno 12] Timeout on http://mirror.sigmanet.com/centos/7.3.1611/updates/x86_64/repodata/777a8e916abbbd45a2daaa57ed46a5b9235ff591503bedd37ebf63e0bf2fccd8-primary.sqlite.bz2: (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.

```

My best guess is  that you guys are right about the virbr0 getting in the way. Somehow,  even after i set a static route, the PC defaults back to virbr0 after a  couple seconds. I've disabled libvirtd but that doesnt prevent the  issue.

```
[app02@localhost proc]$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Red Hat, Inc. QXL paravirtual graphic card (rev 04)
**00:03.0 Ethernet controller: Red Hat, Inc Virtio network device**
``` *bold added by me*

4 questions, if i may be so bold:
1. how do I change eth0 to default? assuming this will fix the problem.
2. did your vm create virbr0? 
3. does your VM start with the connection turned OFF?
4. could you please explain how the DNS is different than the gateway in this NAT setup?

---

### Post by KillerKelvUK on 2017-03-31
virbr0 is typically created by libvirt as the default NAT interface on the host, it serves no purpose inside a vm unless you have a specific networking requirement for it.  On the guest please can you run the following commands and post back the output.

```

virsh net-list
*if the above returns as a network device add the name to end of the next command but if the command doesn't return anything skip the next one

virsh net-info [I]put-the-network-name-from-above-here

[/I]route

cat /etc/resolv.conf

```

---

### Post by drewbun2 on 2017-03-31
**virsh net-list**
```
[app02@localhost ~]$ virsh net-list
 Name                 State      Autostart     Persistent
----------------------------------------------------------

```

> **KillerKelvUK said:**
> virsh net-info *put-the-network-name-from-above-here*No value, didnt run


**route**
```
[app02@localhost ~]$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         localhost.local 0.0.0.0         UG    100    0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.122.0   0.0.0.0         255.255.255.0   U     100    0        0 eth0

```


**cat /etc/resolv.conf**
```
[app02@localhost ~]$ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 8.8.8.8
nameserver 8.8.4.4

```

---

### Post by drewbun2 on 2017-04-01
Discovered a work around!

When creating a new guest, if I enable the eth0 from the first screen of centos installer application, the issues experienced above are avoided. This is because, when done this way, the virbr0 is set to 192.168.**124**.1 I tested this twice, it definitely works.

is this a bug (should it be reported)?

```
[nettest2@localhost ~]$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.122.36  netmask 255.255.255.0  broadcast 192.168.122.255
        inet6 fe80::a376:159f:ee35:d2a5  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:0a:59:8d  txqueuelen 1000  (Ethernet)
        RX packets 1525  bytes 2724285 (2.5 MiB)
        RX errors 0  dropped 4  overruns 0  frame 0
        TX packets 1272  bytes 150936 (147.3 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6  bytes 438 (438.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6  bytes 438 (438.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.124.1  netmask 255.255.255.0  broadcast 192.168.124.255
        ether 52:54:00:32:c2:b4  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

It seems KillerKelvUK had me on the right path! I'm going to try and change the IP for virbr0 on my app02 guest to see if that solves the issues there too.

----------------------------------------------------------------------------------------------------------------------------------------
**update: **this does **not** fix it. Any idea what would still be blocking the app02 from connecting to the outside after i changed the virbr0 ip?

**app02 ifconfig**
```
[app02@localhost ~]$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.122.146  netmask 255.255.255.0  broadcast 192.168.122.255
        inet6 fe80::5054:ff:fed6:36a8  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:d6:36:a8  txqueuelen 1000  (Ethernet)
        RX packets 253  bytes 15890 (15.5 KiB)
        RX errors 0  dropped 4  overruns 0  frame 0
        TX packets 79  bytes 6083 (5.9 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 682  bytes 61154 (59.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 682  bytes 61154 (59.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.11  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:be:14:6e  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by KillerKelvUK on 2017-04-01
Which release of Centos was it out of interest?

---

### Post by drewbun2 on 2017-04-01
[app02@localhost ~]$ cat /etc/centos-release
CentOS Linux release 7.3.1611 (Core) 

Latest from their site! Not sure if this would be a bug in centos or KVM (if its a bug at all)?

---

