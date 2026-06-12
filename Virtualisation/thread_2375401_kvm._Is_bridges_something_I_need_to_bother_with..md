---
title: "kvm. Is bridges something I need to bother with."
date: 2017-10-24
forum: Virtualisation
---

### Post by philp1863 on 2017-10-24
I have never used VM's before, I am using Ubuntu 17.04.
I have installed the virtual machine manager.  I would first like to load and run windows 10 using it.
Then I read that it was recommended that I setup a network bridge before installing the virtual machine manager.
In simple language what advantage does that give me?  The VM's that I will want to run will always be on this same machine (different hard drives).
Will it be faster?
Will it be more secure (i.e. help prevent window viruses from infecting my linux disks?
Advantages?
Thanks

---

### Post by Dennis N on 2017-10-24
You may already have it. In host, test with **ifconfig**:

In the output on my system, it shows as **virbr0** (other connections are omitted here):

```
dmn@Sydney:~$ ifconfig

 virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:1f:b8:85  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
In 17.10 a few days ago, all I had to install was virt-manager (including the dependencies it brought with it) and no other packages to have this. 

It's a different story for 17.04 and 16.04. In 17.04, I recall I installed virt-manager and qemu-system. 16.04 needed several additional packages.

I'n not a technical expert on networking, just an ordinary user, but the bridge gives vm its own ip address on your network. That's important.

---

### Post by TheFu on 2017-10-24
Yes, you need a bridge.

VMM is just a GUI. You need libvirt and kvm and qemu to make use of it.

The default bridges that came with libvirt weren't stable and were slow when first provided yrs ago.  Most people got into a habit of manually making their own bridges which provide near-native network performance for GigE connections.  For 10Gbps networking, you really need to use openswitch to get good performance.  I've never trusted the automatically created bridges and simply never bothered to see if they were better in recent years.  The auto-bridges are NAT, which isn't useful to me either.  I want my VMs to be on the same subnet just like every other physical machine here.

Windows sucks in viruses. Nothing you can do about that. It is the nature of Windows.  A bridge won't impact that good or bad.  The only way I know to make Windows secure enough to be used is to disable all networking on Windows machines. Anything less leaves a door for security issues.

---

### Post by philp1863 on 2017-10-24
Thank you Dennis N and TheFu. 
Your help was brilliant.
  I have a virbr0, so I will just carry on with that and see how it goes.  So basically the bridge will enable VM's to have unique separate IP addresses on the network.  I did not realize that when I installed the virtual manager that it also installed a bridge. I now understand why some web pages also tell you to use the network manager to create a bridge, basically because the default one might not historically work well enough or not fit into your user requirements.
Thank You for helping me very simply to understand what a bridge is. I will for now go along with the default and see how it goes.

---

### Post by TheFu on 2017-10-24
The 192.122.x.x bridge is a NAT bridge (which isn't a real term).  It will require extra effort to allow inbound connections into the VMs from other systems.

I would purge network-manager.  It gets confused by non-trivial network setups, like bridging.

Also, running a VM host on a host-OS with DHCP (non-static) IPs is a non-trivial thing when you don't really understand networking.  Best not to do that and also best to avoid using wifi on the host as well.

---

### Post by fosol on 2017-11-16
@TheFu I recently posted a question about an issue I'm having with setting up static ip on guest VM.  I have a bridge so that the VMs are on the same subnet.  But the guest VMs don't appear to have a networking service, so when I edit the /etc/network/interfaces to set a static IP, it doesn't do anything.  Would you have any experience configuring this?

[https://ubuntuforums.org/showthread.php?t=2377680&highlight=static+ip](https://ubuntuforums.org/showthread.php?t=2377680&highlight=static+ip)

---

### Post by KillerKelvUK on 2017-11-16
So I've a slightly different take on this thread...

In simple terms if all you need your Windows virtual machine to be able to do is connect out to the internet for browsing pages etc then you do not need a bridge (as provided by the bridge-utils package), the default installation of libvirt provides a networking feature that will give you all you need for Windows in a basic configuration.  This is what @Dennis_N was pointing to in his reply...the IP address your Windows virtual machine is issued comes from a process that libvirt sets up which is technically referred to as Network Address Translation or NAT which is what @TheFu mentioned.

If however you require remote access to your Windows virtual machine or you have external processes that require connectivity to a process that runs on the inside of your Windows virtual machine then a bridge is a simpler way to allow this.  Making some assumptions here but as an example if you are a home user and your internet is accessed via a Wifi router that connects to your phone line or cable service then likely this device is also responsible for providing IP addresses to all your PC's, laptops, mobile phones, tablets etc in your home.  A bridge would allow your Windows virtual machine to get an IP address from this same Wifi router which means that it is then more accessible on your local network as libvirt and this NAT process is no longer in the way as it isn't being used.  Getting access to this from over the internet then also becomes simple to accomplish and so on.

---

