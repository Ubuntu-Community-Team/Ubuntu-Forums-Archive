---
title: "VMware can't access internet"
date: 2011-07-12
forum: Virtualisation
---

### Post by rafaelvidal on 2011-07-12
Hello everybody,

I have an issue with my Debian 4 installation.
I was searching Google and it bring me here.

I'm using Windows WebServer 2008 and I installed vmware workstation to run a vm with Debian 4.

But the virtual machine don't have internet access.

_/etc/netword/interfaces_
[B]auto eth0
iface eth0 inet static
       address 192.168.5.10
       netmask 255.255.255.0
       network 192.168.5.0
       broadcast 192.168.5.255
       gateway 192.168.5.150[/B]

I tried to ping the gateway, but it says "host unreachable".

Thank you

---

### Post by fjgaude on 2011-07-12
Have noticed where your Network Adapter in VMware (Player?) is set: Host Only, NAT, Bridges, or disconnected?

---

### Post by rafaelvidal on 2011-07-12
NAT.

I tried to use Bridged, but didn't worked (also I don't know if I setted it up right, so I went back to NAT).

---

### Post by fjgaude on 2011-07-13
Are you using the latest VMware Player 3.1.4?

If you are using Server I think it is no longer supported by VMware.

---

### Post by rafaelvidal on 2011-07-13
I use VMware Workstation 7.1 (latest version), downloaded from the vmware site.

---

### Post by fjgaude on 2011-07-13
The Workstation is running under Windows Server, yea? And you have created a VM of Debian, yes? The console for the workstation installed without error?

I don't know anything about Debian as an OS. Maybe someone else can jump in here and offer some help.

---

### Post by rafaelvidal on 2011-07-13
Yes.
Local System: Windows WebServer 2008
Virtual System: Etch (Debian 4)

Installed VMware program without any error.
Installed Etch (Debian 4) without any error.

---

### Post by rafaelvidal on 2011-07-13
I guess you can help me.

Give me some personal contact such as:
MSN
Skype
Facebook
QQ

where we can talk instantly.

---

### Post by fjgaude on 2011-07-13
> **rafaelvidal said:**
> I guess you can help me.

Give me some personal contact such as:
MSN
Skype
Facebook
QQ

where we can talk instantly.

No where except here, I'm not on any of the social networks, sorry.

---

### Post by rafaelvidal on 2011-07-15
I restored VMware to it's deafult configuration.
Then setted IP to DHCP.

Now I have internet access.

Anyway I need **static** IP.

It semms that when I put static IP, it stop to works.

Any hints?

---

### Post by haqking on 2011-07-15
> **rafaelvidal said:**
> I restored VMware to it's deafult configuration.
Then setted IP to DHCP.

Now I have internet access.

Anyway I need **static** IP.

It semms that when I put static IP, it stop to works.

Any hints?


you need bridged networking with a IP that is valid for your lan.

---

### Post by rafaelvidal on 2011-07-15
It's a dedicated server you know?
It has a fix IP.

I tried to make bridged network, but didn't worked too.

So I tried to make it DHCP and worked.

If you have any tip or trick, tell me.
If you want to try to configure, it will be appreciated too.


Thanks

---

### Post by haqking on 2011-07-15
> **rafaelvidal said:**
> It's a dedicated server you know?
It has a fix IP.

I tried to make bridged network, but didn't worked too.

So I tried to make it DHCP and worked.

If you have any tip or trick, tell me.
If you want to try to configure, it will be appreciated too.

Thanks

Enter the DHCP details it gets as static then

---

### Post by rafaelvidal on 2011-07-20
The DHCP gave me this IP:

address 192.168.21.129
netmask 255.255.255.0
network 192.168.21.0
broadcast 192.168.21.255
gateway 192.168.21.2

The only difference between this and the IP I setted as static before is the end 5.10...nothing else is different.

Hints please.

---

### Post by rafaelvidal on 2011-07-20
I have found the problem.

I can set IP via DHCP or static. It doesn't matter.

It just stop to works (lose internet access) when I forward ports on "Manager Virtual Network" of VMware.

Who can help me to find out WHY the ports forward is doing that?

---

### Post by rafaelvidal on 2012-06-13
> **haqking said:**
> Enter the DHCP details it gets as static then

Haqking, please do me a favor.
Remove my personal info from your quote.
Reply #13 ([http://ubuntuforums.org/showthread.php?p=11052314](http://ubuntuforums.org/showthread.php?p=11052314))

Thanks

---

