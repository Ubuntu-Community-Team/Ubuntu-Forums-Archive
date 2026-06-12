---
title: "Configuring ubuntu server as a home network router"
date: 2008-06-12
forum: Server Platforms
---

### Post by Garyu on 2008-06-12
I have installed 8.04 server edition today because I want to try and setup my own server with html and mail support as well as using it as a local router. The server has 2 ethernet cards installed. Installation went great, and most things seem to work, but I can't access the internet from my desktop station. This is, in short, what I have done:

Edited /etc/network/interfaces to contain the second ethernet card (only eth0 was added by default). 

Edited /etc/resolv.conf to contain the following:
nameserver [IP of server]
nameserver [IP of router-box]
nameserver [IP of ISP DNS-server]

Checked output from route command, which seems OK (both network cards represented).

Setup DHCP for one of the ethernet cards (192.168.0.1) while the other ethernet card gets its IP address from DHCP in the router-box.

Configured bind9 to be caching nameserver and primary DNS.

I have not installed a firewall.

Through all this, I followed the guides here:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

------------------------------

A basic layout of my home network is something along the lines of this:
Inet -> router-box -> desktop1
Inet -> router-box -> server -> desktop2

router-box = 192.168.2.1
desktop1 = 192.168.2.101
server = 192.168.2.102
server = 192.168.0.1
desktop2 = 192.168.0.2

------------------------------

When on desktop2, I can ping server.mydomain.com and get the correct IP adress with response (192.168.0.1) so no problems with DNS there. I can also ping desktop2.mydomain.com (192.168.0.2) without problems. I can also get apache to display the "It works" page from the server. But I can't access the Internet.

When on server, I can ping 192.168.0.2 but if I try to ping desktop2.mydomain.com it gives some weird IP which doesn't respond. So the DNS doesn't seem to work on the server itself. That would not be a problem if I only got Internet connectivity from desktop2. From server, I can also ping [www.ubuntu.com](www.ubuntu.com) without problems, so there are no issues with the internet connection there. I can also install software with aptitude from the Internet, so no problems in that area. 

So, since I believe I followed the above mentioned guides to the point, and I have internet connectivity on the server, and I have connectivity between desktop2 <-> server... Where should I look to solve this?

It seems to me that the routing isn't working properly. But like I said, when I enter route at the prompt I get the following output:
```
Kernel IP routing table
Destination Gateway     Genmask       Flags Metric Ref Use Iface
192.168.2.0 *           255.255.255.0 U     0      0   0   eth0
192.168.0.0 *           255.255.255.0 U     0      0   0   eth1
default     192.168.2.1 0.0.0.0       UG    100    0   0   eth0
```
I don't know anything about routing, since this is my first try at this, but it does look OK to me. 

Any suggestions on what I could do to forward my desktop2 calls to the Internet through the server?

---

### Post by turinglabs on 2008-06-12
You need to check two things:

1) IP forwarding has to be enabled on the server. You can check this with 'sysctl net.ipv4.ip_forward' (you don't need root access for this). If it returns zero, you need to enable forwarding with 'sudo sysctl -w net.ipv4.ip_forward=1', then uncomment the similar line in /etc/sysctl.conf so forwarding is enabled at boot.

2) Think about the return path packets take on the way back to your desktop from the router. The router will have a packet destined for 192.168.0.2, but may not have a route for that network, as it is not directly connected. As a result, reply packets that *should* be routed internally to your server are getting sent out your router's default gateway, to the internet. Add a static network route on your router so that traffic destined for 192.168.0.0/24 goes via the server at 192.168.2.102.

Doug

---

### Post by cdtech on 2008-06-12
I have the same setup. You need to configure your interfaces file as such:
```

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
```

Your first card needs DHCP set for your ip provider and your gateway for your network will be the second card.

My route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
xx.xx.xx.x      0.0.0.0         255.255.248.0   U     0      0        0 eth0
0.0.0.0         xx.xx.xx.x      0.0.0.0         UG    100    0        0 eth0
```

x's are my ip provided address...

---

### Post by Garyu on 2008-06-13
> **turinglabs said:**
> You need to check two things:

1) IP forwarding has to be enabled on the server. You can check this with 'sysctl net.ipv4.ip_forward' (you don't need root access for this). If it returns zero, you need to enable forwarding with 'sudo sysctl -w net.ipv4.ip_forward=1', then uncomment the similar line in /etc/sysctl.conf so forwarding is enabled at boot.

Thanks, you were right. IP-forwarding was set to 0. So one problem fixed. Now, when I'm on desktop2 and type 
```
$ ping www.ubuntu.com
Pinging www.ubuntu.com [91.189.94.249] with 32 bytes of data:

Request timed out.
```
I get the correct IP showing, which means DNS resolving works fine now. BUT I get requests timed out, so no traffic is coming through... 

I assume this has to do with your number 2... But I don't understand how to do it. I tried a few additions with the route command, but those only made the network die completely :(

It's my first time here, so I'd appreciate some more specific help. Thanks. :P

PS. Thanks cdtech, but you posted the exact same setup I have and it's not working. I think Doug is closer to a solution for me here.

---

### Post by turinglabs on 2008-06-13
> **Garyu said:**
> 
I assume this has to do with your number 2... But I don't understand how to do it. I tried a few additions with the route command, but those only made the network die completely :(

It's my first time here, so I'd appreciate some more specific help. Thanks. :P


No problem! The route I'm talking about has to be added to your router-box, not the Ubuntu server. To see this, think about the path a packet takes going out from your desktop2 and coming back. It's the path coming back where your packets are getting mis-routed, because your router-box doesn't know where to find desktop2, so it sends stuff destined there out the internet.

You don't say what kind of router it is; if it were a linux box, you could add the route with a route command, something like this:

```

 sudo route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.2.102

```

If it's a wireless router of some sort, you will be able to add the static route through the web GUI.

---

### Post by Garyu on 2008-06-13
Found the solution. I didn't have NAT / ipmasq installed. Installing it fixed the problem. Here is what I did:

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo aptitude install ipmasq

Don't know if both of those are needed or not, and I haven't figured out what exactly happened with iptables after that command... But at least it's up and running. :D

Apparently, my desktop2 was broadcasting it's IP past the server, which wasn't liked by the router-box. Hence the desktop2 wouldn't be allowed on the network where the router-box was ruling. At least, that's how I understand it. 

Was a good learning experience. Thanks a lot for the help Doug, your ip-forwarding was the thing that put me on the right track to find the solution. :)

---

### Post by turinglabs on 2008-06-13
Glad you got it working. 

> **Garyu said:**
> Found the solution. I didn't have NAT / ipmasq installed. Installing it fixed the problem. Here is what I did:

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo aptitude install ipmasq


The ipmasq package isn't needed, just the iptables statement will do (AFAIK ipmasq will enable forwarding for you, and do some other stuff appropriate for a masquerading firewall/router). You could also add the route on your router-box, and leave out the NAT here, it would still work. The NAT fixes the issue because now packets from your desktop2 now look like they are coming from the Ubuntu server, and the router-box knows how to get back to the Ubuntu server, since the two are directly connected.

---

### Post by Garyu on 2008-07-10
Coming back to this thread with a new problem...

I got an error after rebooting my server:
```
SIOCADDRT: No such device
```
So I thought my network card maybe burnt. I installed a second, identical, card but left the old card in there. Added configurations copied from the old card, but with eth1 instead of eth0. My motherboard ethernet is now called eth2. Connected to the new installed ethernet card, and everything worked fine.

After a while, I rebooted my server again. Then I got the above error on both cards; eth0 could not be installed and eth1 could not be installed. Strange. I dabbled around with settings, rebooted, and it started to work again. Great I though, problem solved. Until next time I rebooted. Same error again. Searched this forum and googled up some things saying it might be a gateway thing (but if it was, how come it worked to begin with?) and then someone saying there was a bug, but I didn't understand quite what it was. So a few reboots later, things started working. 

Today, I rebooted again. Only to find both network cards down again with the same error about SIOCADDRT. So following the talk about gateway in different posts, I changed my /etc/network/interfaces from
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        gateway 192.168.2.1
to 
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
Then the SIOCADDRT error disappeared. I can do
```
sudo /etc/init.d/networks restart
```
and everything looks fine. If I then do
```
ifconfig
```
everything looks fine, and there is data being recieved and transferred at the right places (RX > 0, TX > 0). 

When I go to my windows box, it says it is connected locally to my network but with no internet access. I tried a "dmesg|grep eth" but no errors are shown. 

Some help please? Why is this a more or less random occurance to begin with, and why is it now totally refusing to work? I must have rebooted my server a hundred times by now to try and get the random working thing back, but to no avail.

---

### Post by OldGaf on 2008-07-10
I you want a router, checkout pfsense:

[pfsense]("http://www.pfsense.com/")

Download iso, burn, boot and install.

You can do TON's of stuff with this!

---

### Post by Garyu on 2008-07-10
> **OldGaf said:**
> I you want a router, checkout pfsense:

You can do TON's of stuff with this!

Thanks for the suggestion, but 
1) I also run postfix, apache, php, postgres, R, GRASS, FTP, SSH, etc on this server
2) I'm sticking with Ubuntu

---

### Post by cariboo on 2008-07-10
Checkout arno-iptables-firewall it will do what you want and is available in the repositories.

```
sudo apt-get install arno-iptables-firewall
``` 

Jim

---

### Post by Garyu on 2008-07-11
Thanks Jim, but does that really handle my SIOCADDRT (and following) issues, or did you just look at my original post? I solved my original issue and had some more problems, if you read the entire thread. AIF looks like a nifty tool, but putting down a few hours to learn how to configure and use it isn't really much worth if it deals with my original problem which is now solved...

---

### Post by OldGaf on 2008-07-11
> **Garyu said:**
> Thanks for the suggestion, but 
1) I also run postfix, apache, php, postgres, R, GRASS, FTP, SSH, etc on this server
2) I'm sticking with Ubuntu

I prefer to keep my router as just a router and run my server (web, mail, print, file, download) seperate.

---

### Post by Highspade on 2008-07-12
> **OldGaf said:**
> I prefer to keep my router as just a router and run my server (web, mail, print, file, download) seperate.

Many would agree with you. pfsense is a great product, but this doesn't help the OP

---

### Post by cariboo on 2008-07-12
Refering to your SIOCADDRT problem it didn't see in your interfaces list if you were using:

```
Auto eth0
```

Change the eth0 to your interface. If you aren't that might be part of your problem.

Jim

---

### Post by Garyu on 2008-07-12
> **cariboo907 said:**
> Change the eth0 to your interface. If you aren't that might be part of your problem.
My /etc/network/interfaces contains the line
Auto eth0 eth1 eth2

I think that is the same as what you are suggesting.

---

