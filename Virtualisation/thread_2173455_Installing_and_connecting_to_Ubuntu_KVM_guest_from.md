---
title: "Installing and connecting to Ubuntu KVM guest from a remote Windows 7 Desktop"
date: 2013-09-09
forum: Virtualisation
---

### Post by RyanRahl on 2013-09-09
I have an Ubuntu server 13.04 running KVM
```
uname -a
Linux server 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

This is a remote server and I want to access it from my work lab/office behind a proxy and be able to install and connect to a desktop OS that I will install as a VM guest. I haven't settled yet but it will be either Linux Mint or Fedora as the guest. I need to be able to install the guest remotely, from the CLI is fine, and I need to be able to connect to the remote desktop with my Windows 7 desktop. So KVM is set up and working and I just want to hear any opinions about what the best method to accomplish this is. I can already establish an SSH session and an OpenVPN connection to it so connectivity is fine. I just don't know how to properly utilize KVM from a Windows 7 desktop in order to install and use the guest OSs. Thanks!

---

### Post by TheFu on 2013-09-10
There are hundreds of ways to solve your issue. If you can already ssh from inside the place you need to remote desktop from, then let's stay with that method.

* Use virsh to install whatever linux desktop you like. I usually install Ubuntu Server, then add a DE later.
* On the new desktop, setup a static ip and forward parts for ssh to it.  Verify that you can ssh into the guest OS just installed.
* Install FreeNX using the Ubuntu guide for that. It works using ssh keys for an NX userid, plus either ssh keys or a password login for each userid that runs a desktop.
* On the client machines, install any NX client - qtnx or NoMachine are the most popular. I user the NoMachine client from Win7 all day long.

Profit.

NX works over ssh, so there is nothing else to setup from a network security or port standpoint.  I've used this NX connection from 5 continents to remote back home to a desktop there.  NX is one of the best remote desktops ... easily 2-3x faster than RDP or VNC.  However, it isn't fast enough for video and I've never used audio through it.  For something like that, then you'll need to research the Spice protocol.  I've never been successful with Spice for more than a few hours, then it locked up.

---

### Post by RyanRahl on 2013-09-10
This all sounds great and I planned on simply using VNC and port forwarding to access the guest OS once it is installed, the trouble is, I don't have physical access to the machine so I can not connect a keyboard and mouse to it for the install. In the past I have used virt-manager because I had an Ubuntu desktop but now, with being forced to use Win7 I am struggling for a solution. I think my best bet may be to automate the install then install the VNC service via SSH after the fact. I would like to do an interactive install but it does not appear to be possible with my current configuration. Unless of course anyone has a suggestion that would prove me otherwise, which would be awesome.

---

### Post by KillerKelvUK on 2013-09-10
I'm no expert and learning KVM as I type...

So I'm not sure if you're saying you can't open up your firewall for the VNC ports needed to access your host or not, if so then you could get around this by tunnelling VNC though your SSH connection.

Using something like ubuntu-vm-builder you can create your VM from the CLI to boot using your Windows ISO file (assuming this is local to the host?).  If the ISO location on your VNC client machine, you'd have to sftp it to the host unless someone cleverer has a suggestion on how to mount it remotely.

Once ubuntu-vm-builder has created the guest image/file-system you can simply start the guest up using virsh...as I understand it KVM/libvirt has a VNC server (by default) outside of the guest, i.e. host side so there is no need to install a VNC server inside your guest...just use your VNC client targeted at the host IP and you can pick up the install and click through as needed.

Best of luck,

K

---

### Post by TheFu on 2013-09-10
VNC is not secure and should never be used over the internet without a VPN, but FreeNX is 2-3x more bandwidth efficient AND uses ssh already.  I'm confused when people insist on using VNC when something easy, more efficient, stable and F/LOSS exists.  The only time I use VNC is when there is not any other choice.

virsh works over ssh too. ssh into the hostos and do a local connection to the hostOS hypervisor. You can install an OS with a pure CLI interface. [https://help.ubuntu.com/community/KVM/Virsh](https://help.ubuntu.com/community/KVM/Virsh)  If you can't handle that with virsh, then use vmbuilder as KillerKelvUK says.  I've never use vmbuilder.

A complete solution has been outlined here.

Win7 can run virt-viewer. [http://libvirt.org/windows.html](http://libvirt.org/windows.html) can help.
Win7 can run spice. [http://www.linux-kvm.org/page/SPICE](http://www.linux-kvm.org/page/SPICE)

---

### Post by RyanRahl on 2013-09-10
The VM host (ubuntu server) is also an OpenVPN server and that is how I  am getting an SSH connection to it. I prefer to not have any admin  services facing the internet so no worries about the security of the VNC  connection. I settled on Linux Mint as the guest and the ISO is already  on the system (retrieved via wget). The guest machine (Mint) will be  installed behind the virbr0 interface so do I have to create a route to  access the VNC? Does the VNC service start when I initiate the creation  of the VM? If that is the case I should be able to initiate the install  and then connect to the guest to finish it over VNC. Currently the exact  connection of the setup is me with a Win7 desktop behind a SOCKS proxy,  connecting to the host with a TCP OpenVPN connection, logging in to the  Ubuntu server host over SSH with PuTTY and I desire to use TightVNC to access the desktop of the Mint guest.

---

### Post by TheFu on 2013-09-10
> **RyanRahl said:**
> The VM host (ubuntu server) is also an OpenVPN server and that is how I  am getting an SSH connection to it. I prefer to not have any admin  services facing the internet so no worries about the security of the VNC  connection. I settled on Linux Mint as the guest and the ISO is already  on the system (retrieved via wget). The guest machine (Mint) will be  installed behind the virbr0 interface so do I have to create a route to  access the VNC? Does the VNC service start when I initiate the creation  of the VM? If that is the case I should be able to initiate the install  and then connect to the guest to finish it over VNC. Currently the exact  connection of the setup is me with a Win7 desktop behind a SOCKS proxy,  connecting to the host with a TCP OpenVPN connection, logging in to the  Ubuntu server host over SSH with PuTTY and I desire to use TightVNC to access the desktop of the Mint guest.

OpenVPN is smart.  Running ssh over that is redundant from a security perspective.  Securing ssh is easy.  Run fail2ban and only allow key-based logins.

I always create my own bridges - never used the automatic ones. I've seen a few troubleshooting issues posted here about the auto-created bridges.

I've never setup openvpn and have never used VNC outside the LAN - sorry, can't help you there.  The SOCKS proxy has ZERO to do with any connections to the server if you setup openVPN correctly.

Hopefully, someone will help you with the VNC things ... but NX really is 2-3x more efficient, seriously.

---

### Post by RyanRahl on 2013-09-10
I'm going to give the NX a shot. The SOCKS proxy however is the only way out of the network i'm on so that's why I set up the OpenVPN server to be a TCP connection, because it has to tunnel through the proxy to make a connection to the OpenVPN server. I realize the redundancy of ssh over OpenVPN but I only use it to run commands and setting up something like telnet for remote admin to reduce the encryption overhead is more work than it's worth, so I don't really mind running SSH over the VPN. When I do have an SSH service facing the internet I always use only key-based log ins and I always run the service on an alternate port way out of range of a normal port scan. I've never used an automatic bridge, so bridge creation is not an issue, I need to forward traffic from the virbr0 to the internal virtual interfaces vnet0, vnet1, etc that the VMs will use.
my net config currently looks like this:
```
ifconfig
br0       Link encap:Ethernet  HWaddr 00:30:48:53:d2:1f
          inet addr:192.168.49.1  Bcast:192.168.49.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe53:d21f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4673038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5238698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:812978992 (812.9 MB)  TX bytes:4356075871 (4.3 GB)

eth0      Link encap:Ethernet  HWaddr 00:30:48:53:d2:1e
          inet addr:***.***.***.***  Bcast:***.***.***.***  Mask:***.***.***.***
          inet6 addr: fe80::230:48ff:fe53:d21e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8239800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4356782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5556054987 (5.5 GB)  TX bytes:873946152 (873.9 MB)

eth1      Link encap:Ethernet  HWaddr 00:30:48:53:d2:1f
          inet6 addr: fe80::230:48ff:fe53:d21f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4889469 errors:2 dropped:0 overruns:0 frame:1
          TX packets:5394884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:930340241 (930.3 MB)  TX bytes:4595142823 (4.5 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2288 (2.2 KB)  TX bytes:2288 (2.2 KB)

tap0      Link encap:Ethernet  HWaddr 1a:de:3e:19:b8:cb
          inet6 addr: fe80::18de:3eff:fe19:b8cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:46061304 (46.0 MB)

virbr0    Link encap:Ethernet  HWaddr ba:32:ac:14:36:be
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

And I am connecting to the machine's br0 device from the OpenVPN

---

