---
title: "KVM - Windows guest can't connect Samba server"
date: 2022-01-27
forum: Virtualisation
---

### Post by satimis on 2022-01-27
Performed following steps

On Ubuntu 20.04 host
$ sudo apt install samba

$ sudo nano /etc/samba/smb.conf 
add following content at the bottom of the file```

[LinuxHost]
        comment = Host Share
        path = /home/satimis
        valid users = satimis
        public = no
        writable = yes
        printable = no

```

$ service smbd restart
-> login
no complaint

On Windows 10 guest
-> Windows/File Explorer

Tried
\\10.0.2.2

also
\\10.0.2.2\qemu

both unable to connect Samba server

Pls help.  Thanks

Regards

---

### Post by MAFoElffen on 2022-01-27
On your Windows 10 Machine, open Start, Turn on Windows Services and Features > SMB 1.0 Support > SMB 1.0 client Restart to finish the setup..

Then try again.

---

### Post by rsteinmetz70112 on 2022-01-27
If that doesn't work please post the results of```
 testparm -s
```

---

### Post by satimis on 2022-01-27
> **MAFoElffen said:**
> On your Windows 10 Machine, open Start, Turn on Windows Services and Features > SMB 1.0 Support > SMB 1.0 client Restart to finish the setup..

Then try again.
Turn Windows features on or off```

SMB1.0/CIFs File Sharing Service
```
already checked
-> OK

Tried
\\10.0.2.2

also
\\10.0.2.2\qemu

Still fail, both unable to connect Samba server

---

### Post by satimis on 2022-01-27
> **rsteinmetz70112 said:**
> If that doesn't work please post the results of```
 testparm -s
```

$ testparm -s > tp-output.txt```

Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE

```

tp-output.txt is attached here.

Regards

---

### Post by MAFoElffen on 2022-01-28
How about:
[https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/](https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/)

---

### Post by satimis on 2022-01-28
> **MAFoElffen said:**
> How about:
[https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/](https://www.techrepublic.com/article/how-to-connect-to-linux-samba-shares-from-windows-10/)
Performed following steps:-

Start -> Windows/File Explorer

Right-click -> This PC
Select -> Add a network location 

-> Next -> Next

Internet or network address
[\\10.0.2.2      ]
-> next 

Fail
\\10.0.2.2```

Windows requires a share to public to. Please try another location

```
(pls refer to screenshot attached)

\\10.0.2.2\qemu
still same result

Regards

---

### Post by TheFu on 2022-01-28
The correct name would be 
//10.0.2.2/LinuxHost

But I think you would be better off using the [homes] section. This does sharing of HOME directories for the specific user that logs in.  Sharing of a HOME directory in a different way is problematic. 
Use this instead:
```
[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

And don't forget to add the username to the samba passwd file.
```
sudo smbpasswd -a {username}
```

Also, use the highest smb protocol allowed by the clients.  Win7 supports vers=2.1 as the highest - that's a client-side setting.  Higher protocols are faster and more secure. In theory, this should be auto-negotiated by the client and server, but since the defaults changed in 20.04, there have been problems.  These settings are spelled out in the smb.conf manpage. There are dependencies in the options, so keeping the config file as short and simple as possible is a good idea.

---

### Post by satimis on 2022-01-28
> **TheFu said:**
> The correct name would be 
//10.0.2.2/LinuxHost

I have tried  \\10.0.2.2\LinuxHost 
but it still failed

> 
Also, use the highest smb protocol allowed by the clients.  Win7 supports vers=2.1 as the highest - that's a client-side setting.  Higher protocols are faster and more secure. In theory, this should be auto-negotiated by the client and server, but since the defaults changed in 20.04, there have been problems.  These settings are spelled out in the smb.conf manpage. There are dependencies in the options, so keeping the config file as short and simple as possible is a good idea.
Pls explain in more detail about "use the highest smb protocol allowed by the clients" before trying your suggestion.

Thanks

Regards

---

### Post by MAFoElffen on 2022-01-28
(My own frustration) I remember that this all worked great with Windows 7. Then between Windows 8.x and Windows 10, sharing Windows WorkGroups got weird and complicated on the Windows side... SMB Shares were the same though. Personally, I haven't done it with SAMBA in a few minutes. (At least for a few years)

Maybe I should spin up some Machines and try to recreate this, then verify what should work between. You say Ubuntu 20.04.3 host with SAMBA and a Windows 10 Guest of which Windows Edition level and build #?

---

### Post by MAFoElffen on 2022-01-28
Okay then... Two machines- Ubuntu Server 20.04.3 running SAMBA Server Services, Windows 10 Pro. Worked fine as I asked you to try.

Let me ask the obvious question... Did you open up UFW firewall on Ubuntu for the share to be seen?

---

### Post by satimis on 2022-01-28
> **MAFoElffen said:**
> Okay then... Two machines- Ubuntu Server 20.04.3 running SAMBA Server Services, Windows 10 Pro. Worked fine as I asked you to try.

Let me ask the obvious question... Did you open up UFW firewall on Ubuntu for the share to be seen?
$ sudo ufw status```

Status: inactive

```

I have 6 Windows 10 guests created on KVM, all having same problem.

I wonder which IP address I should fire up on Windows guest ?

10.0.2.2
192.168.1.164 (host static IP)
192.168.122.1 (virbr0)
192.168.254.1 (virbr1)

Regards

---

### Post by TheFu on 2022-01-28
If the windows guests are connected to a host bridge, then use them just like physical hosts on the same DHCP/static subnet as the host machine and forget they are VMs.

Connections between VMs and other systems of any sort work just like they were physical machines if you use the linux bridge setup. I always manually create this as br0.  I only use NAT or host-only for systems that won't communicate with any other system (real or VMs).

My LAN DNS knows about each VM, just like it knows about every physical computer. No difference at all.

Everything I've posted works with bridged VMs or physical hosts.

If your VMhost has an IP of 192.168.1.164/24, then all your guest machines would use that subnet too, if you configured a bridge correctly.
I find little use for any of the virbrX stuff. What's the point of a system that can't be seen by other systems?  Non-networked games?
help.ubuntu.com has a section on setting up a bridge on a host machine.  There are a few threads in these forums about netplan + KVM + bridges too.  These are all on the KVM host machine. Then when you setup each VM, make certain the setting for the Network uses the bridge device that you made up, not any of the virbrX junk.  It also is helpful if inside the guest VM, that you use a virtio NIC driver and inside the VM, there is a virtio NIC driver.  

Doing this, I get fairly great connection speeds between the guest and the host:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 33908 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.02   sec  2.55 GBytes  21.6 Gbits/sec    0   2.07 MBytes       
[  5]   1.02-2.00   sec  2.47 GBytes  21.5 Gbits/sec    0   2.44 MBytes       
[  5]   2.00-3.00   sec  2.56 GBytes  22.0 Gbits/sec    0   2.69 MBytes       
[  5]   3.00-4.00   sec  2.42 GBytes  20.8 Gbits/sec    0   2.82 MBytes       
[  5]   4.00-5.00   sec  2.26 GBytes  19.4 Gbits/sec    0   2.82 MBytes       
[  5]   5.00-6.00   sec  2.38 GBytes  20.5 Gbits/sec    0   3.11 MBytes       
[  5]   6.00-7.00   sec  2.24 GBytes  19.3 Gbits/sec    0   3.11 MBytes       
[  5]   7.00-8.00   sec  2.18 GBytes  18.7 Gbits/sec    0   3.11 MBytes       
[  5]   8.00-9.00   sec  2.10 GBytes  18.0 Gbits/sec    0   3.11 MBytes       
[  5]   9.00-10.00  sec  2.39 GBytes  20.5 Gbits/sec    0   3.11 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  23.6 GBytes  20.2 Gbits/sec    0             sender
[  5]   0.00-10.00  sec  23.6 GBytes  **20.2 Gbits/sec**                  receiver

iperf Done.
```
Similar speeds happen between different guests on the same host-KVM server with the virtIO NIC drivers.
20Gbps isn't bad for next to zero effort, right?
Of course, going across a real wire will be limited to whatever the network can support.  I have a GigE network with nearly 100% Intel NICs, so from a VM on one KVM host to a different system, I get 
```
[  5]   0.00-10.00  sec  1.09 GBytes   **937 Mbits/sec**                  receiver
```
Those pesky wires and switches have to slow everything down. ;)

---

### Post by satimis on 2022-01-28
> **TheFu said:**
> The correct name would be 
//10.0.2.2/LinuxHost

But I think you would be better off using the [homes] section. This does sharing of HOME directories for the specific user that logs in.  Sharing of a HOME directory in a different way is problematic. 
Use this instead:
```
[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```

And don't forget to add the username to the samba passwd file.
```
sudo smbpasswd -a {username}
```

-snip-

Performed following steps:-

$ sudo nano /etc/samba/smb.conf 
comment out the old code and add following code```

[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S

```

$ sudo service smbd restart

$ sudo smbpasswd -a {satimis}```

New SMB password:
Retype new SMB password:
Failed to add entry for user {satimis}.

```

Would there is a problem on the Samba server?

Regards

---

### Post by TheFu on 2022-01-28
Do you know of any command that actually puts brackets in the CLI interface options?  I can't think of any off the top of my head outside an awk script. Never for administrative commands.

```
$ sudo smbpasswd -a {username}
```

means to replace the "{username}"  is the username you want to add.  There's a manpage for smbpasswd which explains how to use it too. {brackets} are a very common way to say replace this stuff with what makes sense for your setup.  I'd use:

```
$ sudo smbpasswd -a thefu
```

---

### Post by satimis on 2022-01-28
Hi thefu,

$ sudo smbpasswd -a satimis```

New SMB password:
Retype new SMB password:
Added user satimis.

```

-> Windows/File Explorer
\\10.0.2.2\homes
\\192.168.1.164\homes
\\192.168.122.1\homes
\\192.168.254.1\homes

All unable to connect Host and never request for password

---

### Post by TheFu on 2022-01-28
You need to setup a KVM bridge, move all the VMs over to it as I post in #13 above.
Bridges are setup in the netplan.yaml file (it has a different name) in /etc/netplan/


And the name isn't "homes" ... it will be the IP/DNS-name of the guest machine that is on the same LAN as the host with the username.

For example, I use //hadar/thefu in a file manager.

---

### Post by satimis on 2022-01-29
> **TheFu said:**
> You need to setup a KVM bridge, move all the VMs over to it as I post in #13 above.
Bridges are setup in the netplan.yaml file (it has a different name) in /etc/netplan/


And the name isn't "homes" ... it will be the IP/DNS-name of the guest machine that is on the same LAN as the host with the username.

For example, I use //hadar/thefu in a file manager.
Performed following steps:-

$ apt policy iperf3```

iperf3:
  Installed: (none)
  Candidate: 3.7-3
  Version table:
     3.7-3 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```
$ ls /etc/netplan/```

01-network-manager-all.yaml

```
$ cat /etc/netplan/01-network-manager-all.yaml ```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  
```
  
$ sudo apt install iperf3
done

$ iperf3 -c hadar```

iperf3: error - unable to connect to server: No such device or address

```

$ sudo service smbd restart

$ sudo iperf3 -c hadar```

iperf3: error - unable to connect to server: No such device or address

```

Still the same

---

### Post by hortimech1 on 2022-01-29
It is quite possible you are looking in the wrong direction, guest access is turned off by default on Win10 pro

---

### Post by satimis on 2022-01-29
> **hortimech1 said:**
> It is quite possible you are looking in the wrong direction, guest access is turned off by default on Win10 pro
I have both Win10 Pro and Win10 Home guests.

If guest access is turned off by default on Win10, then how can I share files between it and Linux host ?

I can't expect it is so complicate?  On VirtualBox files sharing between Windows/Linux guests and Linux host is quite simple and straightforwards.

Regards

---

### Post by TheFu on 2022-01-29
Seems you are confused about following steps.  I didn't help much with that.

Step 1  **Setup a linux bridge on the host.**
Do that first.
[https://netplan.io/examples/](https://netplan.io/examples/) has examples. One of them is for a Linux bridge.  There are posts in these forums about it too, but no too many. Like most things, it is only hard when you don't understand the underlying networking or file format. YAML is picky. There is a thread just about YAML here with netplan ... mostly about indentations and spacing. Where it is allowed and where it is NOT allowed.

Step 2 **Change the networking for all your guest VMs to use the bridge device.** I'd do this in **virt-manager**.

Step 3 **Set the guest VMs networking to use static IPs that are on the same subnet as the KVM list system.**

Step 4 Verify connectivity between each system to all other systems. Use 'ping'.

Samba won't work until that is handled.

---

### Post by MAFoElffen on 2022-01-29
> **satimis said:**
> $ sudo ufw status```

Status: inactive

```

I have 6 Windows 10 guests created on KVM, all having same problem.

I wonder which IP address I should fire up on Windows guest ?
```

10.0.2.2/8
192.168.1.164/24 (host static IP)
192.168.122.1 /24(virbr0)
192.168.254.1/24 (virbr1)

```
Regards
You have 4 different Networks ID's there... Which means that they can only talk with other computers with the same Network ID, or they would have to go through a router or routing table to direct the traffic outside of that Network ID.

Do you have any routers to network routers or a routing table to get traffic between them? which would be only for your 10.0.2.2 guest to talk with your 192.168.1.164 host... The other two are not addressable from outside the host, except to the internet, because they are both NAT. From the outside of that Host, VM's on a NAT VSwitch appear with the Host's Network IP address, with a tag inside of the packets, that are handled for the NAT addressing. Other computers outside of that Network ID cannot directly address them.

A quick test would be to try to ping between. If you cannot ping between, then you surely cannot do smb file sharing between either. 

On a network bridge, what that means is that 'bridge' will be able to bridge between Networks with the same Network ID. So VM's will be on the same Network ID as the host. There are two different types of Bridges for LibVirt (KVM): Traditional, which you dedicated a NIC to be the bridge, or Open VSwitch, where you share a NIC with the host to also be a bridge. The second is harder to setup, than the first.

I use the Traditional Bridge on my Server, as I have lots of NIC's, where I can afford to dedicate one for the VM Host to be a bridge. On my laptop, I have Open VSwitch setup. Both let VM's appear on as just computers with IP addresses on the same Network ID's as my Hosts.

There are many type of virtual switches. NAT, Routing, Private, Open,Bridge, SR-IOV, etc, I also have Virtual router appliances setup to configure what network infrastructure I need to replicate.
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo virsh net-list
[sudo] password for mafoelffen: 
 Name               State    Autostart   Persistent
-----------------------------------------------------
 default            active   yes         yes
 Isolated_Net_192   active   yes         yes
 NAT_Network_172    active   yes         yes
 Routed_Net_172     active   yes         yes

mafoelffen@Mikes-ThinkPad-T520:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master ovs-system state UP group default qlen 1000
    link/ether 3c:97:0e:07:b8:df brd ff:ff:ff:ff:ff:ff
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 24:77:03:8a:42:38 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.170/24 brd 10.0.0.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 97705sec preferred_lft 97705sec
    inet6 2601:603:1f80:6dd0::9c3a/128 scope global dynamic noprefixroute 
       valid_lft 529707sec preferred_lft 529707sec
    inet6 2601:603:1f80:6dd0:5197:47ba:cfc:a01a/64 scope global temporary dynamic 
       valid_lft 295sec preferred_lft 295sec
    inet6 2601:603:1f80:6dd0:1444:56:b3e0:1a6b/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 295sec preferred_lft 295sec
    inet6 fe80::89c:61bc:17f4:2af1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: ovs-system: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 96:18:ac:79:e7:df brd ff:ff:ff:ff:ff:ff
5: br0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 3c:97:0e:07:b8:df brd ff:ff:ff:ff:ff:ff
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c6:12:69 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:c6:12:69 brd ff:ff:ff:ff:ff:ff
8: virbr3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:d1:7c:a6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.1/24 brd 192.168.100.255 scope global virbr3
       valid_lft forever preferred_lft forever
9: virbr3-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr3 state DOWN group default qlen 1000
    link/ether 52:54:00:d1:7c:a6 brd ff:ff:ff:ff:ff:ff
10: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:03:35:d0 brd ff:ff:ff:ff:ff:ff
    inet 172.16.99.1/24 brd 172.16.99.255 scope global virbr1
       valid_lft forever preferred_lft forever
11: virbr1-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr1 state DOWN group default qlen 1000
    link/ether 52:54:00:03:35:d0 brd ff:ff:ff:ff:ff:ff
12: virbr2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:01:52:ce brd ff:ff:ff:ff:ff:ff
    inet 172.16.98.1/24 brd 172.16.98.255 scope global virbr2
       valid_lft forever preferred_lft forever
13: virbr2-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr2 state DOWN group default qlen 1000
    link/ether 52:54:00:01:52:ce brd ff:ff:ff:ff:ff:ff

```
This "IS" where I see your problem is: Your implementation of your virtual networks, and your understanding of basic networking principles. These are all easy fixes.. And most all of that is free, depending on what hardware you have already. I can be done. It just needs to be configured (correctly).

---

### Post by TheFu on 2022-01-29
While you do need to dedicate a port on a NIC to the bridge, it can still be used by the host and all the guest VMs.
NetworkManager cannot be used as the renderer, at least not to my knowledge. You'll need to replace the netplan yaml file completely. Run a few netplan-specific commands.

Also, the KVM host needs a static IP on the LAN.  Not really, but for the displayed understanding, it is mandatory.

If the Ubuntu host IP is 192.168.1.164/24 - which looked like it is inside the DHCP range, move it to be outside that range to avoid issues. I put static IPs between .1 and .100.  My DHCP range is fairly small - above .240.
Anyway, say you make the KVM host IP 192.168.1.10/24
Then you'd setup static IPs on the new bridge for each KVM-guest as 
192.168.1.11/24
192.168.1.12/24
192.168.1.13/24
....
192.168.1.99/24

You get the idea, I hope.

---

### Post by satimis on 2022-01-29
> **MAFoElffen said:**
> You have 4 different Networks ID's there... Which means that they can only talk with other computers with the same Network ID, or they would have to go through a router or routing table to direct the traffic outside of that Network ID.

Do you have any routers to network routers or a routing table to get traffic between them? which would be only for your 10.0.2.2 guest to talk with your 192.168.1.164 host... The other two are not addressable from outside the host, except to the internet, because they are both NAT. From the outside of that Host, VM's on a NAT VSwitch appear with the Host's Network IP address, with a tag inside of the packets, that are handled for the NAT addressing. Other computers outside of that Network ID cannot directly address them.

- snip-.
192.168.1.164
is the host ip

$ ping 192.168.122.1```

64 bytes from 192.168.122.1: icmp_seq=4 ttl=64 time=0.126 ms
64 bytes from 192.168.122.1: icmp_seq=5 ttl=64 time=0.062 ms
64 bytes from 192.168.122.1: icmp_seq=6 ttl=64 time=0.042 ms
......

```

$ ping 192.168.122.1```

64 bytes from 192.168.122.1: icmp_seq=4 ttl=64 time=0.126 ms
64 bytes from 192.168.122.1: icmp_seq=5 ttl=64 time=0.062 ms
64 bytes from 192.168.122.1: icmp_seq=6 ttl=64 time=0.042 ms
....

```

I have router on the network.

$ sudo virsh net-list```

 Name       State    Autostart   Persistent
---------------------------------------------
 default    active   yes         yes
 isolated   active   yes         yes

```

$ ip addr show```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 04:d9:f5:7d:0e:40 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.164/24 brd 192.168.1.255 scope global dynamic noprefixroute enp3s0
       valid_lft 6585sec preferred_lft 6585sec
    inet6 fe80::5c3c:b0cb:323a:78d9/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: virbr1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:25:27:95 brd ff:ff:ff:ff:ff:ff
    inet 192.168.254.1/24 brd 192.168.254.255 scope global virbr1
       valid_lft forever preferred_lft forever
4: virbr1-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr1 state DOWN group default qlen 1000
    link/ether 52:54:00:25:27:95 brd ff:ff:ff:ff:ff:ff
5: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:74:d7:11 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
6: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:74:d7:11 brd ff:ff:ff:ff:ff:ff

```

I don't expect files sharing between Windows guest and Linux host on KVM is so complicate.  I have no problem on files sharing between Linux guests and Linux hosts on KVM.

Neither I have problem on files sharing between Windows drives and Linux drives in the same PC running "ext2 volume manager".  But it doesn't work on KVM for files sharing between Windows guests and Linux host.  I have tested it.

---

### Post by satimis on 2022-01-29
> **TheFu said:**
> Seems you are confused about following steps.  I didn't help much with that.

Step 1  **Setup a linux bridge on the host.**
Do that first.
[https://netplan.io/examples/](https://netplan.io/examples/) has examples. One of them is for a Linux bridge.  There are posts in these forums about it too, but no too many. Like most things, it is only hard when you don't understand the underlying networking or file format. YAML is picky. There is a thread just about YAML here with netplan ... mostly about indentations and spacing. Where it is allowed and where it is NOT allowed.

Step 2 **Change the networking for all your guest VMs to use the bridge device.** I'd do this in **virt-manager**.

Step 3 **Set the guest VMs networking to use static IPs that are on the same subnet as the KVM list system.**

Step 4 Verify connectivity between each system to all other systems. Use 'ping'.

Samba won't work until that is handled.
I don't expect files sharing between Windows guests and Linux host on KVM is so complicate, needing to treat them as server.  I don't have problem sharing files between Linux guests and Linux host on KVM.  I don't need Samba to do the job.

Is there another way to do it, instead of running Samba?

Regards

---

### Post by #&amp;thj^% on 2022-01-29
Not to add frustration here but this has worked for me on 18.04 and 20.04: [https://www.yodiw.com/install-samba-ubuntu-20-04-and-windows-10-sharing/](https://www.yodiw.com/install-samba-ubuntu-20-04-and-windows-10-sharing/)

---

### Post by TheFu on 2022-01-29
> **satimis said:**
> I don't expect files sharing between Windows guests and Linux host on KVM is so complicate, needing to treat them as server.  I don't have problem sharing files between Linux guests and Linux host on KVM.  I don't need Samba to do the job.

Is there another way to do it, instead of running Samba?


We aren't on the system, so we cannot really tell what you have setup.  I'd have posted a 100% working netplan file for you already, if any of my KVM hosts used netplan.  They do not. They are running 18.04 server still with ifupdown and the old "interfaces" file to control networking.

I haven't used network-manager in over a decade. Early versions were extremely buggy, so I've been purging every package nm-* and network-manager* from my systems.  I think of network-manager for places where trivial networking is needed - mainly laptops that will use DHCP.  Even on my laptops, I purge it and have been using static IPs for years with wicd-curses to manage wifi connections. This means I manually have to take down the normal, static, wired, connection before bringing up the wicd-curses tool. I wouldn't expect anyone else to do that - beginner or expert.  I just really, really dislike network-manager after losing weeks to bugs.  Linux is flexible and I take advantage of that flexibility.

But ... any server (for any network services) should have a static IP or effectively a static IP through DHCP Reservations (many routers allow this).  This is especially important for people who's networking knowledge isn't 100% solid.  Just do it.

If you setup bridge networking for all your VMs, running services on VMs is much easier.  You've been doing it the hard way.  VirtualBox has a "bridged connection" checkbox too, BTW.  But since the Linux bridge software is really quite excellent (openVswitch isn't necessary until we start talking about 10Gbps wired networks) and really easy to setup and forget for years, it is worth doing.

If you run any service on the LAN in a virtual machine, you need a Linux Bridge. Samba isn't anything special.  ssh would need this too. So would nextcloud or apache or nginx or .... any other network service.

Google found hundreds of good results for setting up a bridge using netplan.  Here's one:
[https://askubuntu.com/questions/1054350/netplan-bridge-for-kvm-on-ubuntu-server-18-04-with-static-ips](https://askubuntu.com/questions/1054350/netplan-bridge-for-kvm-on-ubuntu-server-18-04-with-static-ips)
I'm not thrilled with the first answer, but it does appear to be correct, though it forgets the netplan commands needed after any changes to the YAML files:
```
sudo netplan generate
sudo netplan apply --debug
```

I prefer NOT using Network-Manager as the renderer.

Something like this on the KVM host machine:
```
# #################################
#   [ for bridge + static - KVM ]
network:
  version: 2
  renderer: networkd
  ethernets:
     [COLOR="#FF0000"]eth0[/COLOR]:
       dhcp4: false
       dhcp6: false
  bridges:
      [COLOR="#FF0000"]br0[/COLOR]:
        interfaces: [[COLOR="#FF0000"]eth0[/COLOR]]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.1.[COLOR="#FF0000"]15[/COLOR]/24]
        gateway4: 192.168.1.1
        nameservers:
           addresses: [[COLOR="#FF0000"]192.168.1.80[/COLOR]]

```
I'd name that file /etc/netplan/01-br0-static.yaml, just to provide clarity for what it does.
eth0 is probably NOT the correct device on your system. enp3s0 looks like what you'd use. "br0" can be anything within reason. br0 is the common name. If multiple bridges are used, br1, br2, br3 ...   
br0 will be the active static IP for the hostOS.
The nameserver is whatever nameserver you normally use.  1.1.1.1,1.0.0.1 would be suggested if you don't run a DNS on your LAN already.   None of the settings are really any surprise, I hope.
Notice how I specifically don't set any IPv6 stuff?  That's my ignorance. Do what you like, but I cannot help.

Refer to my posts above for the libvirt settings to change for each guest VM.
Inside each guest VM, a NIC will be available with a name based on the fake driver used in libvirt. Inside an Ubuntu VM using the virtio NIC driver, I see ens3 as the wired ethernet device (it is really the bridge from the hostOS).

---

### Post by satimis on 2022-02-02
Problem solved : Files Sharing between Windows/Linux Guest and Linux Host on KVM.  My target is to copy files from Linux Host to Windows/Linux Guest without size restriction.

About 10 years ago I ran Samba sharing files between Linux servers.  New technologies are being developed daily.  I wonder whether there are new solutions developed in these 10 years, sharing files from Linux Host to Windows Guest on KVM.

Through postings and heavy searching on Internet, I found many suggestions.  Finally I targeted on following document as reference which helps me out.

How to Enable clipboard and folder sharing in Qemu/KVM on Windows Guest
[https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/](https://dausruddin.com/how-to-enable-clipboard-and-folder-sharing-in-qemu-kvm-on-windows-guest/)

Ubuntu 20.04 -- the Host
Windows 10 (Home and Pro) /Linux (Debian, Ubuntu, Linux Mint etc) -- the Guests

Steps performed as follows:-

1) Solution – Clipboard sharing
Step 1 – Download spice-guest-tools to Windows/Linus Guest
Step 2 – Run and install spice-guest-tools

After finish, shutdown the Guest

Download URLs :
Windows 10 Pro - [https://cutt.ly/SROqBqZ](https://cutt.ly/SROqBqZ)
Linux Mint Edge - [https://www.spice-space.org/download.html](https://www.spice-space.org/download.html)
Remark:
Ubuntu 20.04 - already installed as default


2) Solution – Folder sharing
using Cockpit Virtual Machines and Cockpit

On Ubuntu 20.04 Host Terminal:-
Step 1 – Install Cockpit and Cockpit Virtual Machines

$ sudo apt install cockpit cockpit-machines

Then enable and start cockpit
$ sudo systemctl enable cockpit.socket
$ sudo systemctl start cockpit.socket

Step 2
Start Google Chrome (on Host) and browse;
[http://localhost:9090](http://localhost:9090)

Login (using your PC user password and username)
(refers to screenshot_01)

After login
Select -> Virtual Machines
You'll find all guests there
(refers to screenshot_02)

Step 3 – Start virt-manager -> select win10pro_02, then hit the big “Open” button on the top.

Popup another screen (win10pro_02 on QEMU/KVM)
click -> Show virtual hardware details (the 2nd small icon on the top left corner)

Right-click -> Channel spice -> Add Hardware
(refers to screenshot_03)

Popup another screen
select -> Channel (on the left column)
(refers to screenshot_04)

then on the right column
on Name drop list, select -> org.spice-space.webdav.0
-> Finish

Close Virt-Manager (you don't need it anymore)

Come back to Web-UI on Google Chrome;
Click ">" (at the left of win10pro_02 guest) to popup [Run] [Delete] taps
(refers to screenshot_05)

Click -> [Run] -> Console to popup another screen
(refers to screenshot_06)

Click -> [Launch Remote Viewer]
Popup [download ] at the left bottom corner

Right-click [download ] -> Open
Starts win10pro_02 guest

Login win10pro_02

Click -> File (on the left top corner) -> Preferences
Check -> Share folder
close the small screen

Then files can be drap&drop onto the desktop of win10pro_02 guest from Ubuntu 20.04 Host.

RemarK-1: steps for Linux Guest are similar.

Remark-2: I have tried copying an .iso of 5G from Host onto the desktop of win10pro_02 guest without problem.  At present I don't need copying files from Windows guest to Linux host.

Remark-3
ext2 Volume Manager - a wonderful Win App for sharing files amongst Windows and Linux drives on the PC.

Cockpit and Cockpit Virtual Machines - wonderful Linux Apps for sharing files of large size from Linux host to Windows/Linux guests on KVM.

Remark-4
Pls play around selecting the itmes on the left column of screenshot-02.  You'll find many wonderful features.

Remark-5
Can't upload screenshot_06: You may only attach up to 5 files per post


Regards

---

### Post by TheFu on 2022-02-02
Cockpit is completely unnecessary.
Just run virt-manager or virt-viewer as needed.  Virt-viewer has a Windows client.

If you are using the host computer with a desktop and the VM is running on the same system:
```
/usr/bin/virt-viewer --attach --direct  {vm-name} &
```

If you want to connect over a network to the VM, use
```
/usr/bin/virt-viewer --connect qemu+ssh://{IP of host or DNS name}/system  {vm-name} &
```
ssh must be configured.
spice should be enabled to/from all Linux VMs by default.
On Windows VMs, there are Redhat SPICE tools which need to be loaded. The "spice" URL posted above has it.
I did get virt-viewer using ssh working on Windows, but it never worked with ssh-keys (always needed a password). Connecting remotely without ssh is a complete non-starter for me.

I'm not a fan of allowing Windows to mount ext2/3/4 storage directly. Seems like a good way to a corrupted file system.

Happy you figured out a solution.

---

### Post by satimis on 2022-02-03
> **TheFu said:**
>  - snip -

I'm not a fan of allowing Windows to mount ext2/3/4 storage directly. Seems like a good way to a corrupted file system.


I run Windows solely for testing, not for production.  Copying files from Linux host to Windows guest already caters my needs.

For curiosity I'm now looking for a way copying files from Windows guest to Linux host, making Copy&Paste(Drag&Drop) bidirectional.

Any suggestion?

Regards

---

### Post by precioufuentes on 2022-08-23
As far as I understand, Samba is a program that allows UNIX/Linux computers to mimic Windows machines. With Samba, computers can exchange files or manage print jobs as file servers or servers under Windows. To be honest, I have never heard of this server, let alone used it. But I could, in case you fail, suggest an alternative as [https://fastupload.io/en](https://fastupload.io/en). In this case, downloading and installing different servers is not needed. It will be much faster to exchange files using this method. You can also download multiple files at once without any delays and without having to register.

---

### Post by satimis on 2022-08-23
> **precioufuentes said:**
> As far as I understand, Samba is a program that allows UNIX/Linux computers to mimic Windows machines.
Thanks for your advice.

I ran Samba before and it works.

On a PC with multiple drives running Windows and Linux OSs, if installing virt2 on Windows drive I can retrieve data from Linux drives, one way only.  But I can't save data from Windows drive on Linux drive.  

I wonder whether there is another solution on KVM for both ways on Windows guest and Linux host?

Thanks

Regards

---

