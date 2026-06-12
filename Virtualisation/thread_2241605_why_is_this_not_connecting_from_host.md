---
title: "why is this not connecting from host?"
date: 2014-08-27
forum: Virtualisation
---

### Post by mastablasta on 2014-08-27
I can not connect to server from host. I am not sure what I did wrong.

```
/etc/network/interfaces
auto eth1
iface eth1 inet static
        address 192.168.1.20
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
# dns...
dns-nameservers 192.168.1.1
dns-search org


```

attached are the pictures of ifconfig in server and vbox setup.

I am simply not sure what am I missing here. I am supposed to connect to server from host via browser [https://192.168.1.20](https://192.168.1.20)

edit I get this:[B]
Unable to connect
Firefox can't establish connection to the server at 192.168.1.20
[/B]
and I can't even ping it in this case.

---

### Post by TheFu on 2014-08-27
Dude - I can't understand what you are trying to do. Can you please step back and explain a little more clearly?

What is the hostOS IP?
What is the clientOS IP?
Is there a bridge on the hostOS or NAT?  Unless you are running a security lab, don't use host-only or NAT networking.  Make vbox faster: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

When you post files - please be extremely clear which machine it comes from too.

Oh - and no images please, please, please. Text only.  I can't copy/paste images to provide answers.

---

### Post by Tadaen_Sylvermane on 2014-08-27
I'm assuming the server is the virtual machine. You need to set the network interface to bridged for the server virtual machine. That will put it on your physical network and not the virtualized internal network for Virtual Box guests.

*EDIT* As a side note I don't know what the broadcast and network parts are for of the /etc/network/interfaces file. I have never bothered with them and find they add unnecessary complication when you are just setting a static ip. This is mine on my minecraft server.

```
# Static IP for eth0
auto eth0
iface eth0 inet static
        address 10.0.1.176
        netmask 255.255.255.0
        gateway 10.0.1.1
        dns-nameservers 10.0.1.1 8.8.8.8 8.8.4.4
```

---

### Post by mastablasta on 2014-08-28
> **TheFu said:**
> Dude - I can't understand what you are trying to do. Can you please step back and explain a little more clearly?

What is the hostOS IP?
What is the clientOS IP?
Is there a bridge on the hostOS or NAT?  Unless you are running a security lab, don't use host-only or NAT networking.  Make vbox faster: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

When you post files - please be extremely clear which machine it comes from too.

Oh - and no images please, please, please. Text only.  I can't copy/paste images to provide answers.

ha, ha... I didn't know how to copy in terminal in virtualbox... so I just made a screenshot.

I didn't have any external network connection at the time. I just set it up the same way that Turnkey Linux (debian) is setup. static IP on server and then host only adapter on host virtual box and then I just type IP in browser on host and get to sever OS. which is why I am puzzled as to why it is not working here.  

> **Tadaen_Sylvermane said:**
> I'm assuming the server is the virtual machine. You need to set the network interface to bridged for the server virtual machine. That will put it on your physical network and not the virtualized internal network for Virtual Box guests.

*EDIT* As a side note I don't know what the broadcast and network parts are for of the /etc/network/interfaces file. I have never bothered with them and find they add unnecessary complication when you are just setting a static ip. This is mine on my minecraft server.

```
# Static IP for eth0
auto eth0
iface eth0 inet static
        address 10.0.1.176
        netmask 255.255.255.0
        gateway 10.0.1.1
        dns-nameservers 10.0.1.1 8.8.8.8 8.8.4.4
```

yeah I don't think you can have it bridged and then DHCP if there is no router that will assigning the address. or am I understanding this concept wrong?

anyway I would say I have almost same setup except no external nameserver and not a bridged interface,

I am trying to connect a Host (with no internet or LAN connection as I am at work - don't ask) to virtualbox guest which is a zentyal server.


I've successfully set it up at home using bridged interface and DHCP - but then router/modem assigned an IP I believe.

edit: this is the ifconfig ran on host when no internet connection is active

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:1f:74:cd:3d:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13999 (13.9 KB)  TX bytes:13999 (13.9 KB)

```

---

### Post by TheFu on 2014-08-28
You can have bridged and set a static IP. Of course, if you take an IP that isn't yours, the network admin might be pissed.
The selected network model for a clientOS matters - HUGELY - **read the virtualbox manual so you understand the differences**.
DHCP is just about providing IP addresses - nothing more.

Host-only networking should be used for security research. I can't think of any other good reason for it.
NAT should be used if you don't want systems on the main LAN to access the VM.  I think there's a way to use NAT-forwarding through the vbox interface - never used it.

Go read the manual, please.

If you are running production servers - don't use virtualbox. For toy servers or development, it is fine.  IMHO.

---

### Post by Tadaen_Sylvermane on 2014-08-28
*EDIT* My idea to virtualize a router didn't work. But looking at the networking modes for virtual box host only networking as mentioned above is what you want. It took me a minute to figure it out though. Here it is in a nutshell.

In the VirtualBox preferences select network. Create a host only network, configure as you wish.
Once you have this then you can attach the network adapter of the virtual machine to the host only network. For a static Ip I disabled the DHCP server in the above location and set it the normal way inside of the VM.

I would love to know the reasons for avoiding host only networking when it is exactly the tool required here, security lab or not.

---

### Post by mastablasta on 2014-08-29
yeah from: 6.2. Introduction to networking modes
> 
**Network Address Translation (NAT)**
If all you want is to browse the Web, download files and view e-mail inside the guest, then this default mode should be sufficient for you, and you can safely skip the rest of this section. Please note that there are certain limitations when using Windows file sharing (see Section 6.3.3, “NAT limitations” for details).
**Bridged networking**
This is for more advanced networking needs such as network simulations and running servers in a guest. When enabled, VirtualBox connects to one of your installed network cards and exchanges network packets directly, circumventing your host operating system's network stack.
**Host-only networking**
This can be used to create a network containing the host and a set of virtual machines, without the need for the host's physical network interface. Instead, a virtual network interface (similar to a loopback interface) is created on the host, providing connectivity among virtual machines and the host.

The others are not really that interesting, bridged would work if I had router (that's how I understand it and it really does work). but host only networking should work when the there is only host and guest. and setting the static IP like I did with other server you can then connect to it from host.

which is why I am puzzled in this case as it doesn't seem to be working at all. it could be the Zentyal server software somehow set's it up differently. but on the other hand the settings seem to be ok. really not much different than on the debian servers. 

anyway after getting Zentyal to work on the other internet connected PC I saw that after installing a quite big server thing one still has to install and install and download and install, so I guess this no network host wouldn't be of much use... before I was under impression that this package will preinstall the necessary things nicely packaged on top of Ubuntu that would then just be enabled.

---

### Post by steeldriver on 2014-08-29
You should be able to use NAT so long as you forward the appropriate port(s) in the VirtualBox network settings - then use localhost:port to connect to it

The attached pic shows an example for SSH but the process should be the same for forwarding your webserver port

[ATTACH=CONFIG]255929[/ATTACH]

---

### Post by TheFu on 2014-08-29
[http://www.virtualbox.org/manual/ch06.html#network_hostonly](http://www.virtualbox.org/manual/ch06.html#network_hostonly)> 
... the virtual machines can talk to each other and the host as if they were connected through a physical Ethernet switch. Similarly, as with internal networking however, a physical networking interface need not be present, and the virtual machines cannot talk to the world outside the host since they are not connected to a physical networking interface.

Seems like he wants to have systems outside talk to this machine or did I misread something.  "host-only" is a great description ... only VMs under the host can talk between themselves. Nothing upstream, nothing on the real network will be available.

So either use port forwarding like steeldriver says or use a bridged network and get an IP from the network admin for your VM. if you want other machines on the real network to have network access to the VM.

---

### Post by Tadaen_Sylvermane on 2014-08-29
Its amazing how hard simple english is to understand for some people. He wants the host to talk to the guest vm. There is no external network, no other machines involved. Host only networking is what he needs here. You guys are abstracting all over the place. Just look at exactly what is being asked.

---

### Post by mastablasta on 2014-09-02
vboxnet0 set's up the net parameters (found in preferences). and i need to setup those and then server has to have the same setup as they are in those settings for the host only networking to work like it should. marking this as solved.

edit: in case someone else stumbles on this - I did this by checking the setup form other servers i set previously. but here is more explanation if one needs it: [http://askubuntu.com/questions/293816/in-virtualbox-how-do-i-set-up-host-only-virtual-machines-that-can-access-the-in](http://askubuntu.com/questions/293816/in-virtualbox-how-do-i-set-up-host-only-virtual-machines-that-can-access-the-in)

edit2: port forwarding NAT to host also works.

---

