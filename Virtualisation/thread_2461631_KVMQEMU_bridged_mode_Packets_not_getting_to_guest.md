---
title: "KVM/QEMU bridged mode Packets not getting to guest"
date: 2021-05-04
forum: Virtualisation
---

### Post by Doug S on 2021-05-04
Hi All,

This question, and a lot more detail, is also over on [askubuntu.com]("https://askubuntu.com/questions/1333453/bridged-networking-in-kvm-qemu-lan-addressed-packets-dropped"). I know several users from here also frequent askubuntu.com, but for those that don't...

I prefer to run my VM's on my LAN, and therefore want to to use bridged mode. I have never been able to make this work properly on my 20.04 Ubuntu test server. It works fine on my systemd/networkd Debian server and used to work fine on pre-netplan (pre systemd/networkd) Ubuntu servers.

Packets that should be sent onwards to the vnet NICs are not. They don't even appear on tcpdump on the host bridge. The packets just seem to get dropped from the link layer. The behaviour seems much like non-promiscuous mode, but I have done specific tests ensuring everything is in promiscuous mode with the same results.

I never run containers (lxc, lxd, docker) and do not have the br_netfilter module loaded, nor any iptables rules at all, and I want it that way.

I have tried pretty much everything from every reference I have found.

---

### Post by Doug S on 2021-05-07
At this point, I have tossed netplan and trying via systemd-networkd directly.
This issue has been driving me crazy for some time now.

---

### Post by Doug S on 2021-05-07
For my 20.04 test server host, the up to date kernel is:

5.4.0.72 , as I do not run HWE.

That kernel and various predecessors that I still have installed do not work for this application.
The next Development kernel I still have installed, is 5.8.0, and it works fine for this application, as does any others I have installed and tried up to and including 5.12-rc6.

While I pretty much never run the stock kernel, I was doing so for this work on purpose and out of caution. I so wish I had tried another kernel weeks ago.

---

### Post by TheFu on 2021-05-07
So - no chance of posting the working netplan.yaml file?
This is on of the last reasons I haven't moved our VM servers to 20.04.

---

### Post by Doug S on 2021-05-08
> **TheFu said:**
> So - no chance of posting the working netplan.yaml file?
This is on of the last reasons I haven't moved our VM servers to 20.04.It is also the reason I waited so long to move away from my 16.04 servers and the reason my main server is now Debian. I actually think my yaml file posted over on ask might work, but not sure if I re-install netplan to see. I actually prefer to use systemd-networkd directly. It is late in my time zone, I'll pick this up in the morning.

EDIT: Bear with me, TheFu. I am pretty dense at times. It turns out my hardware is too new to be running 20.04 without the HWE stack, but I only figured that out about 3/4 of the way through bisecting the kernel in an attempt to determine what needed to be backported to the kernel 5.4 series. I moved my NVME drive from my previous test server to my new one, but didn't think about perhaps needing the HWE stack. Well, I paid a big price in terms of wasted time. However, I can not install the HWE stuff, because I have un-installed netplan, upon which it depends. So, I need some time to roll back some of my changes, re-install netplan and re-test to be sure. Then I'll come back here and post what I did. Eventually I will delete my question over on askubuntu (no need to advertise my stupidity).

---

### Post by TheFu on 2021-05-08
If I don't do something dumb at least once a day, I start to worry. ;)
When I hit 10x in 1 day, it is time for a beer and sleep.

---

### Post by Doug S on 2021-05-08
O.K. I am now using netplan again, moved to the HWE stack, rolled back my systemd-networkd related changes, and cleaned up some other garbage from this saga. So, this is what I did to make my libvirt/QEMU VMs work on my LAN via a host bridge. There are a great many references that I should list and give credit to, but I didn't keep track.

First, I wanted to get rid of the libvirt default stuff for the NAT method that uses iptables rules. Why? 
[LIST=1]
[*]Because I want complete control of the host iptables rules for myself.
[*]Because I never ever want any VM to be the NAT way.
[/LIST]
So first, keep a copy of the default.xml file in /etc/libvirt/qemu/networks, just in case there is ever a need to go back and because it gets deleted:
```
sudo cp default.xml default.xml.original
```
Now,
```
virsh net-destroy default
virsh net-undefine default
```
Edit your netplan .yaml file to define the bridge. On my system the default .yaml file was called 01-netcfg.yaml in /etc/netplan. This is after edit:

```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: no
  bridges:
    br0:
      interfaces: [ enp3s0 ]
      dhcp4: yes
#      dhcp4: no
#      addresses: [192.168.111.136/24]
#      gateway4: 192.168.111.1
#      nameservers:
#        addresses: [192.168.111.1]
#      dhcp6: no
#      link-local: [ ]
#      parameters:
#        stp: true
#        forward-delay: 4
```
Where I have commented out a static host address version and couple of other things. Some references say one needs stp, but I disagree.

In /etc/libvirt/qemu/networks create an xml file to define the bridged network for the VMs. The file prefix name can be whatever is desired. It will get re-written later, so suggest to keep an original copy:

```
doug@s19:/etc/libvirt/qemu/networks$ ls -l
total 24
drwxr-xr-x 2 root root 4096 Apr 30 07:11 autostart
-rw------- 1 root root  367 Apr 30 06:54 br0.xml.original
-rw-r--r-- 1 root root   96 Apr 18 15:09 bridge.xml.original
-rw------- 1 root root  576 Apr 23 13:08 default.xml.original
-rw------- 1 root root  383 Apr 30 07:10 [COLOR="#FF0000"]host-bridge.xml[/COLOR]
-rw-r--r-- 1 root root  104 Apr 30 07:10 [COLOR="#FF0000"]host-bridge.xml.original[/COLOR]

doug@s19:/etc/libvirt/qemu/networks$ cat /etc/libvirt/qemu/networks/host-bridge.xml.original
<network>
    <name>host-bridge</name>
    <bridge name='br0'/>
    <forward mode="bridge"/>
</network>
doug@s19:/etc/libvirt/qemu/networks$ [COLOR="#FF0000"]sudo cp host-bridge.xml.original host-bridge.xml[/COLOR]
virsh net-define host-bridge.xml
virsh net-autostart host-bridge
virsh net-start host-bridge
virsh net-list --all
 Name          State    Autostart   Persistent
------------------------------------------------
 host-bridge   active   yes         yes

```
Probably want to re-boot here.

For VMs being converted from the NAT method, use "virsh edit" and change the network area to, for example, this:

```
    <interface type='[COLOR="#FF0000"]bridge[/COLOR]'>
      <mac address='52:54:00:60:ea:0e'/>
      <source [COLOR="#FF0000"]bridge[/COLOR]='[COLOR="#FF0000"]br0[/COLOR]'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
```And for creating a new VM, at least the way I do it:

```
virt-install -n desk-ii -r 8192 \
--disk path=/home/doug/vm/desk-ii.img,bus=virtio,size=50 \
-c impish-desktop-amd64.iso \
[COLOR="#FF0000"]--network bridge=br0,model=virtio,mac=52:54:00:60:ea:5e[/COLOR] \
--video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole -v --vcpus=4
```

Tested on 4 VMs. two old ones converted from the NAT method and 2 brand new ones, defined to use the host bridge to start with.

Note: I still have to double check some things, so there might yet be edits.

---

### Post by TheFu on 2021-05-08
That seems much harder than I would have thunk. I don't do anything special inside the libvirt config. Hummmm. Sometimes, I'll want to bring up a toy desktop and NAT is good for that type of system - or for Try Ubuntu online banking purposes.

I've never touched the **virsh net-edit default** tool. Ah ... it is just like the way we had to "define" new VMs using XML in 2009.

I just make the bridge available on the system, then under virt-manager type in br0 for the network device to be used. Sometimes I'll change the MAC address so that last 2 digits map 1-for-1 to the IP of that system.  

I don't use DHCP inside any of my VMs beyond the first 5 minutes.
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

STP is a network protection capability.  Best to have it enabled if you have multiple switches that might be cross connected.

---

### Post by Doug S on 2021-05-09
> **TheFu said:**
> Sometimes, I'll want to bring up a toy desktop and NAT is good for that type of system - or for Try Ubuntu online banking purposes.You can keep the default.xml stuff or reinstate it if you want the NAT stuff. (note, I did not test reinstating it.)

> **TheFu said:**
> I just make the bridge available on the system, then under virt-manager type in br0 for the network device to be used.I do not use virt-manager. I am a server type and rarely have a linux desktop running.

> **TheFu said:**
> Sometimes I'll change the MAC address so that last 2 digits map 1-for-1 to the IP of that system.Good idea. Currently I have no correlation. 

> **TheFu said:**
> I don't use DHCP inside any of my VMs beyond the first 5 minutes.
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)I first start with a DHCP address from my pool, but then assign IP via MAC address and add it to my DNS (bind) stuff. Although, I admit, I get behind and never get to it sometimes, so the VM continues with the address from the pool.

---

### Post by TheFu on 2021-05-09
> **Doug S said:**
> You can keep the default.xml stuff or reinstate it if you want the NAT stuff. (note, I did not test reinstating it.)
Hummm. I figured there was a way to do this, just never became an issue since only 10 VMs get created / year here.

> **Doug S said:**
> I do not use virt-manager. I am a server type and rarely have a linux desktop running.
virt-manager connects to different hypervisors from a workstation using ssh+qemu:// connect strings.  Also, for desktops using Spice, it is handy to have a remote desktop that 2% when I actually want a desktop.

**MAC-to-IP Relationship**
> **Doug S said:**
> Good idea. Currently I have no correlation. 
It has to be consistent or it will cause issues, but when doing DHCP reservations, it certainly does make creating the MAC -to- IP table easy to quickly check for problems and if a system isn't on the network, but the arp table still has the MAC entry ... 

> **Doug S said:**
> I first start with a DHCP address from my pool, but then assign IP via MAC address and add it to my DNS (bind) stuff. Although, I admit, I get behind and never get to it sometimes, so the VM continues with the address from the pool.
My DHCP pool is 2x the number of expected guest devices. That's basically 10. I consider it a security design choice.  Having too many random devices allowed on a subnet just seems like a bad idea. There is a trade-off between convenience and security, again. Seems that always happens. ;(

---

