---
title: "Can't get &quot;Bridged Adapter&quot; to work in VirtualBox Network Settings"
date: 2013-05-20
forum: Virtualisation
---

### Post by dragonfly41 on 2013-05-20
I'll start in this forum but may have to take the question to VirtualBox forum.

re: VirtualBox network configuration of VM Ubuntu-12.04.2 LTS server.


My problem is that I can't get Bridge Adapter to work in VirtualBox VM Ubuntu-12.04.2-i386-server.

I have the following configuration:


[LIST]
[*]Ubuntu-12.04.1 LTS desktop as the host OS. 
[*]Wired connection to cable modem. 
[*]Installed the latest version of VirtualBox,  4.2.12. 
[*]Installed on VirtualBox a guest VM Ubuntu-12.04.2 32bit server. 
[/LIST]

My problem is in setting up VirtualBox network so that I can access the guest server from my host desktop.

In VirtualBox Network Settings I have set Bridged Adapter (eth0).

However when booting up the VM a network connection isn't found. 

When I login to the guest OS on VM and run ifconfig iI don't see an IP address against eth0.

If I try to run ping 8.8.8.8 from the guest OS I get ..
connect: Network is unreachable.

I cannot ping the guest server from the host OS.

If I then shut down the guest server and change network settings to NAT (instead of Bridged Adapter) 
and then startup again I can ping from guest to host using ping 10.0.2.2.  But in reading this chapter on virtual networking ...

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

NAT is not recommended when running guest OS as a VM server.


So what steps must I take to ensure that Bridged Adapter works?

...

I've read these threads ...

[http://ubuntuforums.org/showthread.php?t=1945029](http://ubuntuforums.org/showthread.php?t=1945029)

[https://forums.virtualbox.org/viewtopic.php?f=7&t=43090](https://forums.virtualbox.org/viewtopic.php?f=7&t=43090)


Note .. I've looked in 
 /etc/udev/rules.d/70-persistent-net.rules

but the file is empty.

...

Other files in host OS

/etc/network/interfaces

auto lo
iface lo inet loopback




and in guest OS (the VM)
/etc/network/interfaces

# the loopback network interface
auto lo
iface lo inet loopback

# the primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by dino99 on 2013-05-20
is the guest-addition package installed (from oracle) ?

---

### Post by dragonfly41 on 2013-05-20
Thanks for the suggestion.

I hadn't read the manual as far as guest-additions.

[https://www.virtualbox.org/manual/ch04.html#idp12039536](https://www.virtualbox.org/manual/ch04.html#idp12039536)

Reading the manual further I see that the command 

$ sudo apt-get install dkms

has to be run in the guest terminal.

I didn't see any reference to a "guest-additions package (from Oracle)".
I did find an Extensions package which I installed.

Since this command requires network access I had to setup network to be NAT.

Applied this command $ sudo apt-get install dkms

After successful installation shut down the VM.

Set Network Settings back to Bridge Adapter.

Restarted the VM.

But $ ifconfig continues to show no IP address.

What have I missed?

---

### Post by wildmanne39 on 2013-05-20
*Thread moved to **Virtualisation**.*

---

### Post by Morbius1 on 2013-05-21
I'll admit that I have a problem in that I tend to read posts literally so this may be a silly observation but:
> I have the following configuration:
    Ubuntu-12.04.1 LTS desktop as the host OS.
    [COLOR=#0000cd]**Wired connection to cable modem.**[/COLOR]
    Installed the latest version of VirtualBox, 4.2.12.
    Installed on VirtualBox a guest VM Ubuntu-12.04.2 32bit server. 
In Bridged Mode the guest machine makes an independent connection to ( via a "bridge" to the hosts network card ) and receives it's IP address from the same router the host machine does. If you in fact have a "cable modem" and not a modem/router combination there is no router.

---

### Post by dragonfly41 on 2013-05-21
Thanks.  I think you may have hit the nail on the head.
I do only have a cable modem and not a router.

From reading this chapter ...

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

> Bridged networking

This is for more advanced networking needs such as network simulations and running servers in a guest. When enabled, VirtualBox connects to one of your installed network cards and exchanges network packets directly, circumventing your host operating system's network stack.


It is was not clear to me that bridged networking only works with routers and not cable modems?

Reading further posts I read that I should try to setup _two_ Network Adapters in the guest OS:
[LIST]
[*]NAT 
[*]Host-only 
[/LIST]

as described here ..

[http://superuser.com/questions/384719/how-do-i-set-permanent-ip-for-my-virtualbox-using-bridge-adapter](http://superuser.com/questions/384719/how-do-i-set-permanent-ip-for-my-virtualbox-using-bridge-adapter)

I'll keep tweaking but stop trying Bridged Networking.   However the manual (above) does suggest that a Bridged Adapter is needed for guest server testing and that is why I was persisting down this path.

Also the ultimate goal is to export from VirtualBox an image of the (tested) guest OS to be placed in the cloud.

---

### Post by CharlesA on 2013-05-22
If you need to access the guest, you can still use NAT and then set port forwarding on the VM properties so you can access it.

---

### Post by dragonfly41 on 2013-05-23
Thanks .. with two network adapters (NAT and host-only .. in that order  .. it seems there is a difference if order is changed)  
I'm now able to ping  in both directions host <--> guest.
IP addresses: host 192.168.56.1 and guest 192.168.56.101

I can access guest LAMP from host via [http://192.168.56.101/](http://192.168.56.101/)

This blog was helpful.  

[http://christophermaier.name/blog/2010/09/01/host-only-networking-with-virtualbox](http://christophermaier.name/blog/2010/09/01/host-only-networking-with-virtualbox)


**Host**
The contents of /etc/network/interfaces in host:-

```
# the loopback network interface
auto lo
iface lo inet loopback

# the primary network interface
auto eth0
iface eth0 inet dhcp
```


**Guest**
The contents of /etc/network/interfaces in guest:

```
# the loopback network interface
auto lo
iface lo inet loopback


# the primary network interface
auto eth1
iface eth1 inet static
address 192.168.56.101
netmask 255.255.255.0
network 192.168.56.0
broadcast 192.168.56.255

# note: gateway and dns-nameservers are not defined here .. should they be?
 

```

**Cannot connect from guest to Internet**
My current issue is I'm not not able to ping from guest to external Internet .. e.g. getting updates into the guest OS.

What must I now setup to get Internet access?  

It seems that with only a cable modem (no router) I can't use Bridged Networking as a third adapter type.

I'm now reading up on VBoxManage scripts so I can better dump relevant troubleshooting information.

my ultimate requirement:
ping host to guest (this now works) ping -c 4 192.168.56.101
ping guest to host (this now works) ping -c 4 192.168.56.1
ping guest to Internet (this has yet to work) ping -c 4 8.8.8.8 (Network Unreachable)

I'm not sure if changing NAT type under File > Preferences > Network might help.

---

### Post by CharlesA on 2013-05-23
You would need to use NAT instead of Host-only. It will give the guest a 10.2.x.x IP address.

---

### Post by dragonfly41 on 2013-05-23
> You would need to use NAT instead of Host-only.

But I am using NAT as Adapter1 *and* Host-only as Adapter2.

Are you suggesting disabling Host-only and using only NAT?

Thanks.

---

### Post by CharlesA on 2013-05-23
> **dragonfly41 said:**
> But I am using NAT as Adapter1 *and* Host-only as Adapter2.

Are you suggesting disabling Host-only and using only NAT?

Thanks.

Correct.

---

### Post by dragonfly41 on 2013-05-24
I did try with only NAT adapter and could ping from guest to Internet .. but that meets only part of my requirement.

I then found this video which explains how to configure Internet <--> Host <--> Guest <--> Internet.

[http://www.youtube.com/watch?v=Jk5Kfm2-Muk](http://www.youtube.com/watch?v=Jk5Kfm2-Muk)

But note that the two adapters are setup in this sequence:-

Adapter 1 Host-only
Adapter 2 NAT

---

### Post by astoutj on 2013-10-28
I was struggling with a very similar issue for hours.

My situation:
Host: 32-bit Windows 7 Professional
VirtualBox v:4.2.18
Guest: 64-bit Ubuntu 12.04 server / bitnami redmine 2.3.3 virtual appliance (don't worry too much about the appliance part)

I also have a 32-bit 12.04 Desktop Guest.
The desktop guest had the bridge adapter network setting and could host servers like a champ.

The 64-bit server however couldn't ever establish the network config and I got the "Waiting for network Configuration....waiting 60 seconds..." etc message on boot. 
It would boot and I had no network capabilities.

I tried the poster's recommendations and also followed the video to no avail.  Finally I came to [this link]("http://virtualboximages.com/%5BSolved%5D+Waiting+for+network+configuration.+Waiting+up+to+60+seconds+for+network+configuration").

I'll summarize here:

- Let it boot up without the network config.
- run: [FONT=courier new]ifconfig -a
[/FONT]- note the first adapter mentioned (It will be of the form "eth#") 
- [FONT=courier new]cd[/FONT] to [FONT=courier new]/etc/network/[/FONT]
- use an editor with root privileges and open the "interfaces" file. (i.e. [FONT=courier new]sudo nano interfaces[/FONT][FONT=arial])[/FONT]
[FONT=arial]- enter your password if necessary.
[/FONT]
[FONT=arial]Under "[/FONT][FONT=courier new]# The primary network interface[/FONT][FONT=arial]", you'll see two lines starting with: "[/FONT][FONT=courier new]auto[/FONT][FONT=arial]" and "[FONT=courier new]i[/FONT][/FONT][FONT=courier new]face[/FONT][FONT=arial]".[/FONT]
- If the adapters listed after "[FONT=courier new]auto[/FONT]" and "[FONT=courier new]iface[/FONT]" are different from the one you noted from [FONT=courier new]ifconfig -a [FONT=arial]then change them to the adapter you noted.
- save the file and reboot.

Your server should now be able to configure the network via "Bridged Adapter".

If the adapters in the [FONT=courier new]/etc/network/interface[/FONT] file were not different from your [FONT=courier new]ifconfig -a,[FONT=arial]then I am sorry. I do not how to help you there.

Hope this helps a few more people with similar issues.[/FONT][FONT=arial][/FONT][/FONT][/FONT][/FONT]

---

### Post by stellar_mass on 2014-05-14
Thanks astoutj, your solution worked for me.

---

