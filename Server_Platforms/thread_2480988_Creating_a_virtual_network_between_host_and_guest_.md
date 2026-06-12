---
title: "Creating a virtual network between host and guest OS (libvert)"
date: 2022-11-16
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2022-11-16
I have 3 physical gigabit network plugs:
[LIST]
[*] 1 onboard
[*]2 on a addon card, this card is attached to the guest os via PCIe pass-through
[/LIST]
these are the physical connections

[LIST]
[*]modem -> addon card port 1
[*]addon card port 2 -> switch
[*]onboard -> switch
[/LIST]

I want to create a virtual network for the host and guest to talk directly with as it is quite inefficient for the host to go over my switch to get to the guest, i want the host to use this as the gateway so it only uses the onboard for local network stuff

[FONT=courier new]virsh net-list --all[/FONT] is empty

This is my netplan file:
```
[FONT=monospace][COLOR=#000000]network: [/COLOR]
  version: 2 
  ethernets: 
    #PCIe pfsense LAN port 
    enp16s0f0: 
      dhcp-identifier: mac 
      dhcp4: false 
      dhcp6: false 
      optional: true 
    #PCIe pfsense WAN port 
    enp16s0f1: 
      dhcp-identifier: mac 
      dhcp4: false 
      dhcp6: false 
      optional: true 
    # Onboard 
    enp27s0: 
      dhcp-identifier: mac 
      dhcp4: true 
      dhcp6: true 
      optional: true
[/FONT]
```

i have this in my guest's xml file ([FONT=monospace][COLOR=#000000]/etc/libvirt/qemu/pfsense.xml)[/COLOR][/FONT]:
```

[FONT=monospace][COLOR=#000000]    <hostdev mode='subsystem' type='pci' managed='yes'> [/COLOR]
      <source> 
        <address domain='0x0000' bus='0x10' slot='0x00' function='0x0'/> 
      </source> 
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/> 
    </hostdev> 
    <hostdev mode='subsystem' type='pci' managed='yes'> 
      <source> 
        <address domain='0x0000' bus='0x10' slot='0x00' function='0x1'/> 
      </source> 
      <address type='pci' domain='0x0000' bus='0x00' slot='0x07' function='0x0'/> 
    </hostdev>[/FONT]

```
this is in my grub file
```
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt vfio-pci ids=8086:105e"[/COLOR][/FONT]
```
```

[FONT=monospace][COLOR=#000000]lspci |grep -i net [/COLOR]
10:00.0 Ether[COLOR=#ff5454]**net**[/COLOR][COLOR=#000000] controller: Intel Corporation 82571EB/82571GB Gigabit Ether[/COLOR][COLOR=#ff5454]**net**[/COLOR][COLOR=#000000] Controller D0/D1 (copper ap[/COLOR]
plications) (rev 06) 
10:00.1 Ether[COLOR=#ff5454]**net**[/COLOR][COLOR=#000000] controller: Intel Corporation 82571EB/82571GB Gigabit Ether[/COLOR][COLOR=#ff5454]**net**[/COLOR][COLOR=#000000] Controller D0/D1 (copper ap[/COLOR]
plications) (rev 06) 
1b:00.0 Ether[COLOR=#ff5454]**net**[/COLOR][COLOR=#000000] cont[/COLOR][/FONT][FONT=monospace][COLOR=#000000]roller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ether[/COLOR][COLOR=#ff5454]**net**[/COLOR]
[COLOR=#000000] Controller (rev 15)[/COLOR][/FONT]

```

---

### Post by MAFoElffen on 2022-11-16
I read your first post. After I read it, I was confused and hesitant to respond. 

I mean, I've done a few things. I have a few skills. I even went back to school at Cisco Academy for CCENT and CCNA. I took other courses for Linux and Microsoft Windows Administration. I have created many virtual and physical networks. I have used pfsense as a virtual firewall/router/switch appliance. I have also used other virtual networking appliances. I even once was interviewed as a VMware VNet Engineer, as a consultant for Microsoft...

I read that post and didn't respond, thinking maybe you were doing something new and different. I don't claim to know everything.

So I am curious enough to ask:
1.) Was there a question in your post?
2.) What is your goal?
3.) Is this something new?

Because this seems to be a lot more work than you would need to "do anything" with pfsense... You know that right? Or not?

EDIT: I think you are trying to use pfsense as your edge router to your Local LAN network, right? You do not need to do an IOMMU pass-through to do that... And neither of those matches what the title of the thread describes. So, yes, I am confused. Could you please explain what you are trying to do?

---

### Post by pqwoerituytrueiwoq on 2022-11-16
I have PCIe pass though working, for the preformance

i just want to add a virtual NIC that bypasses the physical networking hardware between the host and guest for the sake of efficiency (it would be right?), then i can add this as a vlan in pfsense

really seems like a lot (relatively) of extra work/cpu cycles/power usage for my server (host) to proxy data (apt-cache-ng) from the internet for a client when it could cost go to the router over virtual network that runs at ram speed

i was just trying to describe what i have setup already, i'm sure my post could be ordered better

---

### Post by pqwoerituytrueiwoq on 2022-11-17
i think i got it (or not...)

```

chad@niceserver:~$ cat kvm/host-bridge.xml
<network>
  <name>host-bridge</name>
  <bridge name="br0"/>
</network>
chad@niceserver:~$ virsh net-define kvm/host-bridge.xml
chad@niceserver:~$ virsh attach-interface --domain pfsense --type bridge --source br0 --model virtio --config --live

```
```

chad@niceserver:~$ cat /etc/netplan/00-installer-config.yaml
# This is the network config written by 'subiquity'
network:
  version: 2
  ethernets:
    #PCIe pfsense LAN port
    enp16s0f0:
      dhcp-identifier: mac
      dhcp4: false
      dhcp6: false
      optional: true
    #PCIe pfsense WAN port
    enp16s0f1:
      #match:
      #  macaddress: 52:54:00:95:04:64
      #macaddress: c0:c1:c0:01:46:0a
      dhcp-identifier: mac
      dhcp4: false
      dhcp6: false
      optional: true
    # Onboard
    enp27s0:
      dhcp-identifier: mac
      dhcp4: true
      dhcp4-overrides:
        use-routes: false
      dhcp6: false
      optional: true
  bridges:
    br0:
      macaddress: 00:1a:3e:c9:20:03
      dhcp4: true
      dhcp6: true
      optional: true
      parameters:
        stp: true
        forward-delay: 1

```
```
chad@niceserver:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
4: enp27s0: [stripped]
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:1a:3e:c9:20:03 brd ff:ff:ff:ff:ff:ff
    inet 172.16.69.2/24 metric 100 brd 172.16.69.255 scope global dynamic br0
       valid_lft 4966sec preferred_lft 4966sec
    inet6 [stripped] scope link 
       valid_lft forever preferred_lft forever
6: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:c7:79:2d brd ff:ff:ff:ff:ff:ff
    inet6 [stripped] scope link 
       valid_lft forever preferred_lft forever
```

no idea where vnet0 came from, does that need to be there? if not how do i remove it?
```

chad@niceserver:~$ virsh net-list --all
 Name          State      Autostart   Persistent
--------------------------------------------------
 host-bridge   inactive   no          yes

```
inactive... i think i did something wrong, maybe this is something i do not need since it is in net plan?

this is why i wanted to do this:
```

chad@niceserver:~$ ping 127.16.69.1 -c 4 && ping 10.0.0.1 -c 4
PING 127.16.69.1 (127.16.69.1) 56(84) bytes of data.
64 bytes from 127.16.69.1: icmp_seq=1 ttl=64 time=0.024 ms
64 bytes from 127.16.69.1: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 127.16.69.1: icmp_seq=3 ttl=64 time=0.055 ms
64 bytes from 127.16.69.1: icmp_seq=4 ttl=64 time=0.040 ms

--- 127.16.69.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3057ms
rtt min/avg/max/mdev = 0.024/0.039/0.055/0.011 ms
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=0.422 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.413 ms
64 bytes from 10.0.0.1: icmp_seq=3 ttl=64 time=0.369 ms
64 bytes from 10.0.0.1: icmp_seq=4 ttl=64 time=0.375 ms

--- 10.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3070ms
rtt min/avg/max/mdev = 0.369/0.394/0.422/0.023 ms
chad@niceserver:~$ iperf -c 172.16.69.1
------------------------------------------------------------
Client connecting to 172.16.69.1, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  1] local 172.16.69.2 port 47640 connected with 172.16.69.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  1] 0.0000-10.0113 sec  4.35 GBytes  3.73 Gbits/sec
chad@niceserver:~$ iperf -c 10.0.0.1
------------------------------------------------------------
Client connecting to 10.0.0.1, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  1] local 10.0.0.69 port 42978 connected with 10.0.0.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  1] 0.0000-10.0315 sec  1.10 GBytes   939 Mbits/sec

```
Not only is this significantly faster but it frees up resources on the physical hardware layer

---

### Post by TheFu on 2022-11-17
I don't know what was hoped to be achieved, but within the same host, I'm seeing 20-25Gbps network speeds using virtio network drivers for the guest.
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 58564 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  2.77 GBytes  23.8 Gbits/sec    0   3.31 MBytes       
[  5]   1.00-2.00   sec  2.63 GBytes  22.6 Gbits/sec    0   3.31 MBytes       
[  5]   2.00-3.00   sec  2.67 GBytes  22.9 Gbits/sec    0   3.31 MBytes       
...
```
I doubt any cheap NIC would come close to that.

When it comes to a WAN router, I want a stand alone, hardware device, not connected to any virtualization. There have been all sorts of bugs in virtualization software since the beginning.  For my sanity, I don't want to risk that when it matters.

---

### Post by pqwoerituytrueiwoq on 2022-11-17
now try iperf3 on pfsense, i do not understand why, but it hits a cpu bottleneck very hard, also i am sure your cpu is a lot faster than this one i am using (4 1st gen ryzen cores at 3.2-3.6 Ghz)

i have a router i can drop in if i am having down time, but that router hits a cpu bottleneck just doing speedtest and that is not even a gigabit router

i started off with pfsense on bare metal and wanted to do more with my hardware if i am gonna run x86 for my router

this is known as a forbidden router for a reason and mine is very forbidden (the PSU also powers my network switch which i mounted to a PCI slot cover so it lives in the server)

---

### Post by TheFu on 2022-11-18
> **pqwoerituytrueiwoq said:**
> now try iperf3 on pfsense, i do not understand why, but it hits a cpu bottleneck very hard, also i am sure your cpu is a lot faster than this one i am using (4 1st gen ryzen cores at 3.2-3.6 Ghz)


[https://wiki.freebsd.org/NetworkPerformanceTuning](https://wiki.freebsd.org/NetworkPerformanceTuning)
Be certain to follow the links for router-specific tuning.  Note that hyperthreading seems to be bad.

---

