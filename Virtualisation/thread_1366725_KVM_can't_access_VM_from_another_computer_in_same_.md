---
title: "KVM: can't access VM from another computer in same LAN"
date: 2009-12-28
forum: Virtualisation
---

### Post by carnicer on 2009-12-28
Hello, I am having a bit of trouble to access VMs from a computer in the same LAN.

I have 2 computers.

[LIST]
[*]a virtual server hosts, named srv-peat-vhs, IP 192.168.2.101, running ubuntu server 9.10
[*]a "client" computer, named petit, IP 192.168.2.102, running crunchbang linux 8.10 (a lightweigth ubuntu derivative)
[/LIST]

The IPs are delivered by my DSL router though DHCP. Netmask is 255.255.255.0.

On the virtual host server I have installed a VM, which is also ubuntu server 9.10, installed with bootime option "minimal VM". This has been smoothly successful. The IP of this VM is 192.168.122.20 (perhaps given by DHCP).

network accessibility status :


[LIST]
[*] The VM can access the internet, no problem, and also the other computers in the LAN, such as "petit", the client computer.
[*]The VM host computer (srv-peat-vhs) can access both the VMs and the "client" computer. It has an automatically created bridge interface virbr0 (192.168.122.1)
[*]The client computer (petit) can access only the virtual server host, but can't access the VMs inside it. That is the central point of my question.
[/LIST]

In order to solve this, I have searched for information and read the documentation provided at the ubuntu server page. Some manuals point me towards creating an VPN. I am quite a bit overwhelmed, I don't know what to do. My poor-man attempts have been creating a route to the VMs through the bridge interface in the virtual host server, as in the example below (comments start with #) :


```
bulma@petit:~$ sudo route add -net 192.168.122.0 netmask 255.255.255.0 gw 192.168.2.101
bulma@petit:~$ 
bulma@petit:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:18:f13:5c:15:ba  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe5c:15ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1209527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1697041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:398364230 (398.3 MB)  TX bytes:1694090339 (1.6 GB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14144 (14.1 KB)  TX bytes:14144 (14.1 KB)

bulma@petit:~$ 
bulma@petit:~$ 
bulma@petit:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0
192.168.122.0   192.168.2.101   255.255.255.0   UG    0      0        0 eth0
default         .               0.0.0.0         UG    0      0        0 eth0


# ---------------------------------------------------
# this is the virtual host server
# ---------------------------------------------------


marc@srv-peat-vhs:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:22:a3:ed  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fe22:a3ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:562590 errors:0 dropped:0 overruns:0 frame:0
          TX packets:407190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:723321344 (723.3 MB)  TX bytes:246273979 (246.2 MB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7549262 (7.5 MB)  TX bytes:7549262 (7.5 MB)

virbr0    Link encap:Ethernet  HWaddr 0a:df:29:0c:a2:e5  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:295371 (295.3 KB)  TX bytes:13516861 (13.5 MB)

vnet0     Link encap:Ethernet  HWaddr c2:6e:bc:de:a7:57  
          inet6 addr: fe80::c06e:bcff:fede:a757/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2915 (2.9 KB)  TX bytes:60816 (60.8 KB)

vnet1     Link encap:Ethernet  HWaddr 0a:df:29:0c:a2:e5  
          inet6 addr: fe80::8df:29ff:fe0c:a2e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:13900 (13.9 KB)  TX bytes:134361 (134.3 KB)

marc@srv-peat-vhs:~$ 
marc@srv-peat-vhs:~$ 
marc@srv-peat-vhs:~$ ssh vsvn@192.168.122.20
vsvn@192.168.122.20's password: 
Linux ethtest 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Mon Dec 28 23:54:03 2009 from 192.168.122.1
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

vsvn@ethtest:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 54:52:00:51:a6:24  
          inet addr:192.168.122.20  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::5652:ff:fe51:a624/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21122 (21.1 KB)  TX bytes:26019 (26.0 KB)
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vsvn@ethtest:~$ 
```

---

### Post by geekshlby on 2009-12-29
You mentioned that you have an automatically created bridge named virbr0.  I assume you are using libvirt with kvm as libvirt creates a bridge with such a name - just a guess on my behalf.

The bridge, virbr0, on a default install of libvirt, is configured to NAT to any physical device on the host machine.  This means your KVM based VMs would be able to talk outside the host, to one another, and to the host, yet no one external to the host would be able to access the VMs unless you did some tricky port forwarding with iptables on the host.

Anywho...

If you desire to have the VMs on the same physical network as your host, you will need to set up a bridge.  The following example adds eth0 to bridge 'br0'.  After you have your bridge created, you will need to modify your VMs and point the NICs to br0 instead of the default (NAT'd) virbr0.

Example /etc/network/interfaces with a bridge:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# The bridge
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 0
bridge_stp off

---

### Post by carnicer on 2009-12-29
Thank you very much for taking the time to read and reply to my question.


> **geekshlby said:**
> You mentioned that you have an automatically created bridge named virbr0.  I assume you are using libvirt with kvm as libvirt creates a bridge with such a name - just a guess on my behalf.

Yes, your assumption is correct.

> **geekshlby said:**
> The bridge, virbr0, on a default install of libvirt, is configured to NAT to any physical device on the host machine.  This means your KVM based VMs would be able to talk outside the host, to one another, and to the host, yet no one external to the host would be able to access the VMs unless you did some tricky port forwarding with iptables on the host.

Your assumption is correct again, this is a default installation of libvirt. What I want to achieve is to set up a VM that behaves as an internal corporate server, with services such as svn and trac.


> **geekshlby said:**
> If you desire to have the VMs on the same physical network as your host, you will need to set up a bridge.  The following example adds eth0 to bridge 'br0'.

I have applied this on the virtual server host. So far this server can still see the LAN and the internet. And it can also be see **from** the LAN. For reference, these are my interfaces (I have trimmed some lines to reduce verbosity):

```
marc@srv-peat-vhs:/var/lib/libvirt/network$ ifconfig 
br0       Link encap:Ethernet  HWaddr 90:e6:ba:22:a3:ed  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          ...

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:22:a3:ed  
          inet6 addr: fe80::92e6:baff:fe22:a3ed/64 Scope:Link
          ...

lo        Link encap:Local Loopback  
          ...

virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7676 (7.6 KB)  TX bytes:14364 (14.3 KB)

marc@srv-peat-vhs:/var/lib/libvirt/network$ 
```> **geekshlby said:**
> After you have your bridge created, you will need to modify your VMs and point the NICs to br0 instead of the default (NAT'd) virbr0.

I am sorry, this is where I get lost. Basically I don't know how to do what you say. I have found there is a file on the host server, that seems similar to a virt-manager option under menu Edit/Host Details, Virtual Network tab, which has the following content:

```
marc@srv-peat-vhs:/var/lib/libvirt/network$ sudo cat default.xml 
<network>
  <name>default</name>
  <uuid>821ac288-2016-74e4-b27a-e54973550ad8</uuid>
  <forward mode='nat'/>
  <bridge name='virbr0' stp='on' forwardDelay='0' />
  <ip address='192.168.122.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.122.2' end='192.168.122.254' />
    </dhcp>
  </ip>
</network>
marc@srv-peat-vhs:/var/lib/libvirt/network$ 
```> **geekshlby said:**
> Example /etc/network/interfaces with a bridge:

As said above, I have applied that example on the host server **only**, is that correct?

Regarding the VMs, can I change them now or I need to reinstall them? When installing a new VM, the GUI asks about network configuration, with NAT, etc but actually I remember I was not allowed to modify that option at pre-installation time.

Before sending this reply, I have tried rereading some of the links I found yesterday, like the following, but I still get lost.


[LIST]
[*][KVM manual]("http://www.linux-kvm.org/page/Networking"), (see **only** section public bridge)
[*][ubuntu manual]("https://help.ubuntu.com/9.10/serverguide/C/network-configuration.html#bridging")
[/LIST]
My main problem with those and other manuals is that they don't make clear whether the instructions have to be applied on the host server or on the VMs.

---

### Post by geekshlby on 2009-12-29
Now that you have created a bridge on the host, you can modify your VM to "talk" on that bridged interface.

Edit the configuration of your VM and change the interface to bridge.
You can accomplish this with:
virsh edit name_of_vm_to_edit

example:
<interface type='bridge'>
      <source bridge='br0'/>
etc
etc
etc
    </interface>

---

### Post by carnicer on 2009-12-29
It works.

Impressive. Thank you very much!

---

### Post by steyrguy on 2009-12-30
> **geekshlby said:**
> Now that you have created a bridge on the host, you can modify your VM to "talk" on that bridged interface.

Edit the configuration of your VM and change the interface to bridge.
You can accomplish this with:
virsh edit name_of_vm_to_edit

example:
<interface type='bridge'>
      <source bridge='br0'/>
etc
etc
etc
    </interface>


Hi guys, I've read this thread along with a few howtos on the basics of KVM. I've got the image built using the following:

vmbuilder kvm ubuntu --suite=karmic --flavour=virtual --arch=amd64 --mirror=http://192.168.10.30:9999/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=192.168.10.50 --part=vmbuilder.partition --templates=VMtemplates --user=administrator --name=user --pass=pass --addpkg=vim-nox --addpkg=unattended-upgrades --firstboot=boot.sh --mem=1024 --hostname=vm1 --bridge=br0

I'd like my VMs to be visible from the rest of my network. I have br0 setup to bridge with eth0:

br0       Link encap:Ethernet  HWaddr 00:30:48:c4:3f:ca  
          inet addr:192.168.10.30  Bcast:192.168.10.255  Mask:255.255.255.0

eth0      Link encap:Ethernet  HWaddr 00:30:48:c4:3f:ca  
          inet6 addr: fe80::230:48ff:fec4:3fca/64 Scope:Link


virbr0    Link encap:Ethernet  HWaddr f2:62:74:05:d4:f0  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0

vnet0     Link encap:Ethernet  HWaddr 9a:db:60:e6:3e:86  
          inet6 addr: fe80::98db:60ff:fee6:3e86/64 Scope:Link


My problem is that even with bridging enabled between br0 and eth0, my vnet0 does not come up with the IP I assigned it at build time. If need be, I can have it fetch a dhcp, but the question remains, how do I get it to do so?

Where can I configure a static IP for vnet0, or how do I get a DHCP for vnet0?

thanks in advance

---

### Post by carnicer on 2010-01-02
> **steyrguy said:**
> 
My problem is that even with bridging enabled between br0 and eth0, my vnet0 does not come up with the IP I assigned it at build time. If need be, I can have it fetch a dhcp, but the question remains, how do I get it to do so?

Where can I configure a static IP for vnet0, or how do I get a DHCP for vnet0?


I am having the same problem :).

I have cloned my first VM (with virt-clone). I've found out that the original VM uses vnet1, while the copy uses vnet0 (not because I changed it). The host server has a vnet1 interface, and not vnet0. I try to change the copy with virsh edit, without success.

The cloned copy can't get an IP, when I try network restart i see it says it does not have eth0. However, if I do dhclient it can properly get an IP on eth0.

---

### Post by geekshlby on 2010-01-02
Please forgive my lack of understanding, but could you please explain why you are assigning an IP address to vnet0 or vnet1?

vnet[0-infinity+1] is added by libvirt when the VM is started.  There is no need to modify it.

Consider the following:
VM eth0 -> vnet[0,1,etc] -> host br0 -> host eth0

start a single VM
VM1 eth0 -> vnet0 -> host br0 -> host eth0 -> network

start additional VM
VM2 eth0 -> vnet1 -> host br0 -> host eth0 -> network
VM3 eth0 -> vnet2 -> host br0 -> host eth0 -> network
etc

To configure a VM to communicate on the same physical network as the host:
1.  Configure bridge on host
2.  Update the VM's xml to use the bridge

---

### Post by steyrguy on 2010-01-02
ahh. This can be explained as a lack of understanding on my part. Thankfully it was resolved yesterday :D

I was able to bring up a VM using qemu, with bridging to br0 it managed to fetch an IP from my dhcp server and I was able to ssh in.

What I was not expecting was that there is no indication of the guest's IP on the host's ifconfig output. If I nmap my subnet, I see both host and guest just fine.

thanks for the help guys

---

### Post by carnicer on 2010-01-02
Thanks for your reply.


> **geekshlby said:**
> Please forgive my lack of understanding, but could you please explain why you are assigning an IP address to vnet0 or vnet1?

I was not assigning, I was describin how the system was assigning this. I was confused by the fact there was only one vnetN interface on the host server, but that was probably because there was only one machine running.



> **geekshlby said:**
>  vnet[0-infinity+1] is added by libvirt when the VM is started.  There is no need to modify it.

Thanks for explaining, it was good to know.

Now I've found out my cloned VM is working. However, I had to change [FONT=Courier New]eth0[/FONT] to [FONT=Courier New]eth2[/FONT] in [FONT=Courier New]/etc/networks/interfaces[/FONT].

I am a bit confused overall, available documentation is really not very comprehensive for KVM beginners like me. And I find there are some things to polish on the software.

---

### Post by carnicer on 2010-01-03
> **steyrguy said:**
> I was able to bring up a VM using qemu, with bridging to br0 it managed to fetch an IP from my dhcp server and I was able to ssh in.

Does anyone know how to configure the VM IP as being static? If I change [FONT=Courier New]/etc/network/interfaces[/FONT] on the VM to get a static address, the network interface does not go up, regardless of me restarting the service or even rebooting. If I set it back to dhcp, it works.

---

