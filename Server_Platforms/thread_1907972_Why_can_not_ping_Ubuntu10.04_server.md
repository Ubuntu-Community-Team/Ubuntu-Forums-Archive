---
title: "Why can not ping Ubuntu10.04 server"
date: 2012-01-12
forum: Server Platforms
---

### Post by deepakdeshp on 2012-01-12
I am running multi boots on my server like Ubuntu 10.04server, Mint12 etc. When I ping my server from my WIndows client it gives time out. I can ping my Windows desktop from the server. 

When I ping the Windows desktop from the other multiboot partitions I can ping it . The Ubuntu os on the 10.04 server is created from a clonezilla image from another server with different hardware.

---

### Post by rubylaser on 2012-01-12
Your network interface has likely changed.  You can verify this by looking at this file...

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If you see two eth devices in there, Ubuntu has created a new eth device for your new hardware.  The easiest way to fix it, is to just delete the both subsystem lines, and reboot the server.  They'll look like this.

```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:ab:5d:01:0e:10", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

At that point, if you're /etc/network/interfaces file contains an entry for eth0, it should come up fine.

---

### Post by bab1 on 2012-01-12
> **rubylaser said:**
> Your network interface has likely changed.  You can verify this by looking at this file...

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If you see two eth devices in there, Ubuntu has created a new eth device for your new hardware.  The easiest way to fix it, is to just delete the both subsystem lines, and reboot the server.  They'll look like this.

```
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:ab:5d:01:0e:10", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

At that point, if you're /etc/network/interfaces file contains an entry for eth0, it should come up fine.

That seems like a lot of effort to find out what name (label) is used on the target machines the physical device.  I would think that the think that in the most basic terms the name is irrelevant.  More pertinent would be the IP address of the NIC; right?

In other words, wouldn't it better to determine if the IP address has changed.  To the OP -- have you checked to see what the the target host's IP address is (locally -- from that host)?  How does the target host obtain it's IP address?.

---

### Post by rubylaser on 2012-01-12
> **bab1 said:**
> That seems like a lot of effort to find out what name (label) is used on the target machines the physical device.  I would think that the think that in the most basic terms the name is irrelevant.  More pertinent would be the IP address of the NIC; right?

In other words, wouldn't it better to determine if the IP address has changed.  To the OP -- have you checked to see what the the target host's IP address is (locally -- from that host)?  How does the target host obtain it's IP address?.

The OP said this was a Clonezilla restore from a different host and a server, so it's likely it's using a static IP and as result, is not an IP.  This is a very [common problem]("http://www.orzeszek.org/blog/2010/07/25/fix-missing-eth0-when-cloning-ubuntu-vmware-virtual-machines/") in virtualization if migrating or cloning hosts (I see it in VMware and Hyper-V).

Since this was migrated from a functioning box, and this takes literally 10 seconds to do, I'm not sure how you think this is a lot of effort?!?  I guess, I could have provided a sed statement to remove those lines automatically for the OP, or just mentioned that you can remove the file and it's automatically regenerated, but it's so simple to do, why bother?

---

### Post by bab1 on 2012-01-12
> **rubylaser said:**
> The OP said this was a Clonezilla restore from a different host and a server, so it's likely it's using a static IP and as result, is not an IP.  This is a very [common problem]("http://www.orzeszek.org/blog/2010/07/25/fix-missing-eth0-when-cloning-ubuntu-vmware-virtual-machines/") in virtualization if migrating or cloning hosts (I see it in VMware and Hyper-V).

Since this was migrated from a functioning box, and this takes literally 10 seconds to do, I'm not sure how you think this is a lot of effort?!?  I guess, I could have provided a sed statement to remove those lines automatically for the OP, or just mentioned that you can remove the file and it's automatically regenerated, but it's so simple to do, why bother?

Maybe you missed the point.  The OP said nothing about VM's.  Just that it was an image from differing hardware.  I say that it is more appropriate to check the basic IP addressing on the interface(s) first before you go the exotic route using sed, awk. perl, C, python, etc,etc,etc.  Over the last 25 years I have found it best to start with the simple things first.

---

### Post by rubylaser on 2012-01-12
Thanks for sharing your great knowledge... I'll let you handle this.  Since, this is a restore from a previously working SERVER (static ip), I doubt that's the issue.  Since the OP is dual booting and running various Linux distros, I doubt he'd be baffled by a simple networking issue. When the IP route fails, maybe the OP can follow the simple directions I posted and fix their problem.  Thanks for your constructive remarks.

---

### Post by CharlesA on 2012-01-12
> **bab1 said:**
> Maybe you missed the point.  The OP said nothing about VM's.  Just that it was an image from differing hardware.  I say that it is more appropriate to check the basic IP addressing on the interface(s) first before you go the exotic route using sed, awk. perl, C, python, etc,etc,etc.  Over the last 25 years I have found it best to start with the simple things first.

ruby mentioned VMs since hardware changes if you create a new one, which can be a problem if you have something such as firewall rules set for eth0 and the machine is using eth1.

I'd still check to make sure that /etc/udev/rules.d/70-persistent-net.rules only has one entry.

---

### Post by deepakdeshp on 2012-01-13
I am not using Vmware or any virtual machines. I am yet to check the solutions provided by the members , I will give update once I do. I am experienced unix user , I love the power of the command line hence I will not need any sed scripts to simplify the solution.

I changed the interfaces file and changed the static ip from x.x.1.9 to x.x.1.7 . When the machine boots it is getting this static ip 1.7 as I boot the server but I cant ping it from my x.x.1.6 windows box.Nor does the server go on the internet. The resolv.conf and interfaces files look good.

---

### Post by deepakdeshp on 2012-01-13
It had only one entry for eth0 as suggested in 70-persistent-net.rules . I commented it out and rebooted and same line was re-generated. But it hasnt helped, the problem persists.I cant ping it from my lan, while the server does ping my router. ssh service is on on the server. The error is "server unexpectedly closed connection" from putty. Where as I can see the Apache page of the server in the browser.


I had also queried in a separate post that the CLonezilla image works fine from one hardware to different hardware for Ubuntu, both servers and desktops. But it doesnt work for Centos 5.4 . Any idea why it does work for Ubuntu and not for Clonezilla? Its a great way to port machines to a different hardware for Ubuntu.

---

### Post by bab1 on 2012-01-13
> **deepakdeshp said:**
> I am not using Vmware or any virtual machines. I am yet to check the solutions provided by the members , I will give update once I do. I am experienced unix user , I love the power of the command line hence I will not need any sed scripts to simplify the solution.

I changed the interfaces file and changed the static ip from x.x.1.9 to x.x.1.7 . When the machine boots it is getting this static ip 1.7 as I boot the server but I cant ping it from my x.x.1.6 windows box.Nor does the server go on the internet. The resolv.conf and interfaces files look good.

If I understand you correctly you're saying that the host comes up with the IP address of x.x.1.7 consistently.  Have you verified this with ```
ifconfig
```

If so, can the host ping itself.  From *that host itself* can you successfully do this ```
ping x.x.1.7
```

---

### Post by deepakdeshp on 2012-01-13
Server pings to x.x.1.6 my windows machine. Only thing I cant do is putty to the server at x.x.1.7 . Rest all is fine.

---

### Post by bab1 on 2012-01-13
> **deepakdeshp said:**
> Server pings to x.x.1.6 my windows machine. Only thing I cant do is putty to the server at x.x.1.7 . Rest all is fine.

That still doesn't tell me that the server can ping the number x.x.1.7 (e.g ping itself).

Edit:  In my environment I have no firewalls other than at the edge of the network so I don't think of that.  Do you have a host based firewall (on the server)?

---

### Post by deepakdeshp on 2012-01-13
It does ping itself that is x.x.1.7

---

### Post by CharlesA on 2012-01-13
> **deepakdeshp said:**
> It had only one entry for eth0 as suggested in 70-persistent-net.rules . I commented it out and rebooted and same line was re-generated. But it hasnt helped, the problem persists.I cant ping it from my lan, while the server does ping my router. ssh service is on on the server. The error is "server unexpectedly closed connection" from putty. Where as I can see the Apache page of the server in the browser.

Sounds like networking is working, but some services aren't working? Do you have a firewall in place? Can you ping sites on the internet?

> I had also queried in a separate post that the CLonezilla image works fine from one hardware to different hardware for Ubuntu, both servers and desktops. But it doesnt work for Centos 5.4 . Any idea why it does work for Ubuntu and not for Clonezilla? Its a great way to port machines to a different hardware for Ubuntu.

There shouldn't be much difference between the two. Outside of having to configure networking in a different location.

> **bab1 said:**
> If I understand you correctly you're saying that the host comes up with the IP address of x.x.1.7 consistently.  Have you verified this with ```
ifconfig
```

If so, can the host ping itself.  From *that host itself* can you successfully do this ```
ping x.x.1.7
```

It sounds like networking is coming up, but it's not able to get outside the local network.

---

### Post by bab1 on 2012-01-13
> **deepakdeshp said:**
> It does ping itself that is x.x.1.7

To me this means the interface is functional.  The problem is somewhere other than the server.  Are all of these hosts on the same segment (LAN)?  Are you sure there are no firewalls on the XP host?

Edit: Missed the Internet connectivity issue.  Edit 2:  I didn't look to see that it was CharlesA responding.  Too many cooks here.  :-)  Still...

From the server post the output of```
route -n
```

And the contents of ```
/etc/network/interfaces
```

---

### Post by deepakdeshp on 2012-01-13
From the windows host I can ping yahoo.com. No firewall issue. 


As for the centos issue I mentioned, it doesnt boot when restored to a different h/w platform while the the Ubuntu always does.

---

### Post by bab1 on 2012-01-13
> **deepakdeshp said:**
> From the windows host I can ping yahoo.com. No firewall issue.

I think it's best if we stick to the XP to Ubuntu (server) connectivity here.  Do we know that the XP host is actually passing packets to the Ubuntu host?  Are they being blocked, or maybe dropped?

I would turn off the firewall on the XP machine and sniff packets on the Ubuntu machine with Wireshark while pinging. > 

As for the centos issue I mentioned, it doesn't boot when restored to a different h/w platform while the the Ubuntu always does.
Interesting, but it doesn't apply to this issue.  The interface is up and working.  We need to see if if packets are get there and are dropped or if packets are being blocked.

It would help if you would send the info I requested so we can confirm the the interface and routing is configured correctly.

---

### Post by CharlesA on 2012-01-13
> **deepakdeshp said:**
> From the windows host I can ping yahoo.com. No firewall issue. 

Windows host? You said that you weren't using any virtual machines.

Is the machine is question running on a stand-alone box or on another machine?

---

### Post by bab1 on 2012-01-13
> **CharlesA said:**
> Windows host? You said that you weren't using any virtual machines.

The Windows host doesn't have to be in a VM.  It still is referred to as a host and it can be running a Windows OS.  The term *host *is not specific to VM's.> 

Is the machine is question running on a stand-alone box or on another machine?

I'll let the OP answer this definitively, but I'll ask; Why do you ask?

---

### Post by CharlesA on 2012-01-13
> **bab1 said:**
> 
I'll let the OP answer this definitively, but I'll ask; Why do you ask?

If it's running in a VM (which I think they said it wasn't) it might mess with the network settings a bit.

In any case, it doesn't make sense why everything but one service is working unless that service is either not running correctly or is firewalled.

As for a host being called a host.. maybe I deal with virtual machine hosts too much. :p

---

### Post by bab1 on 2012-01-13
> **CharlesA said:**
> If it's running in a VM (which I think they said it wasn't) it might mess with the network settings a bit.
I agree.  Either way that's why I asked to see the conf files for the interface.> 

In any case, it doesn't make sense why everything but one service is working unless that service is either not running correctly or is firewalled.
And that is why I asked for the network topology and whether there are any firewalls (either host based or in the network).> 

As for a host being called a host.. maybe I deal with virtual machine hosts too much. :p
Actually this is a an issue in this thread and elsewhere.  Defining the terms we use, and actually determining the real issues at hand.  All of us are guilty at one time or another of only looking at problem through our own experience.  Diagnoses means seeing the problem as it really exists and apart from the correction.

---

### Post by deepakdeshp on 2012-01-14
The interfaces files is attached. I copied it and renamed it as .txt

---

### Post by CharlesA on 2012-01-14
Here's the contents of the interfaces file, is someone doesn't want to open an attachment.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.7
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search kokan.com

```

If you use dhcp instead of static does it work?

Change iface eth0 inet static to iface eth0 inet dhcp

---

### Post by bab1 on 2012-01-14
> **deepakdeshp said:**
> ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.7
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search kokan.com
```

This looks okay as far as it goes.  We still need the output from ```
route -n
```

I'm curious; can you ping the gateway IP (1921.168.1.1)?  Can you get to the admin page on the router from the server?

Do you own the domain *kokan.com*?

---

### Post by deepakdeshp on 2012-01-15
I can ping the gateway., I can even ping the Windowsdesktop from the server. And the domain is defined just on the intranet. Thesame problem though I am not connected to the internet.

---

