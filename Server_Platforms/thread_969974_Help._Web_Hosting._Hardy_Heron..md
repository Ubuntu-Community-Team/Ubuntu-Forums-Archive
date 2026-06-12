---
title: "Help. Web Hosting. Hardy Heron."
date: 2008-11-03
forum: Server Platforms
---

### Post by lensark on 2008-11-03
Hi guys/girls,

Just a moth ago I switched completely to Ubuntu 8.04 Desktop Edition. Main reason is that I planned to set up my own server at home, learn PHP and create web applications, and be able to run it on the web.

I have already installed LAMP and openssh server. And just this past week I finished coding a log-in and sign-up program, everything is fine I able to run it locally.

Now, next step would be to put it up and running on the web. I've been reading here and there about web hosting, web server, domain names, IP's just trying to get a good understanding about how to put this very simple web application up and running on the web.

I have heard about dyndns.com and it offers a free hostname. So what I did was sign-up for an account and created this: neftali.homelinux.net

I am still stuck at this point. I was looking for a good set of instructions on what to do next...

Looking forward for any help I can get I would really appreciate it..


neftali,

---

### Post by cariboo on 2008-11-04
Basically  you need to set up your server with a static ip address then port forward from that ip address to your router. To set a static ip address you will need to edit /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

then add the following lines to the  file:

```
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Press Ctrl-o to save and Ctrl-x to exit

You will have to substitute your ip address and gateway ip address.

Next setup port forwarding on your router. Forward the ip addressd of the server to port 80 on the router. Every manufacturer does  it differently, so consult your router manual on how to do it.

Next go to [canyouseeme]("http://www.canyouseeme.org/") to check if port 80 is open on your router, or if your ISP is blocking port 80.

Many routers will not let you access your domain name from inside the network, so you will have to be outside your network to try your new web app.

Jim

---

### Post by lensark on 2008-11-04
Thanks Jim, I will try it out =)


But as an update, a friend of mine and I are working on it just few hrs ago and I successfully set it up. Only problem is the rest of the world can't see my site.

Here's how we did it.

sudo apt-get install ddclient

just with this single line and waited for few minutes, and there [http://neftali.homelinux.net](http://neftali.homelinux.net) displays It Works! and [http://neftali.homelinux/net/home.php](http://neftali.homelinux/net/home.php) displays my log-in page.

But that's just it, I'm the only one who can access that, the rest can't. -(


I read articles that talk about internal and external IP addys. I guess it has something to do with those stuff, but i am not that so sure.... got to need more researching....

---

### Post by lensark on 2008-11-04
... and by the way, Jim, I have no physical router. I get my internet connection directly from the antenna. The cable from the antenna is directly plugged-in into my laptop.. But I am not completely sure if I get the internet directly from their base station, perhaps I get it from a router.. But as I said I don't have a physical router here...

---

### Post by davidshere on 2008-11-04
Neftali: (is that your name?)

Looking up the IP address for your site:
```
david@raptor:~$ nslookup neftali.homelinux.net
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	neftali.homelinux.net
Address: 192.168.235.253

```
That's not a publicly routable address.  So, when you look at it, you find it just fine, but when I look at it, I get nothing. 

[www.davidshere.com](www.davidshere.com) points to 166.82.96.21.  The computer that hosts my website doesn't have that for an IP address, though.  The router at my ISP (actually the router here at work) re-directs requests for webpages (through port 80) to the computer that hosts my website.  It could be 192.168.235.253 -- same as yours!  Because we can both have the same internal address, but not the same external address.

You need to do two things:  
1.  Find out your publicly routable address.  One way to do this is to go to whatismyipaddress.com.  Then change your DNS so that it points to this address.
2.  Get the router between your laptop and the internet (wherever that is) to redirect web traffic from the public address to your private address.  This router has to be somewhere; otherwise your laptop wouldn't work with a private address.


EDIT:  I just read cariboo907's post more closely, and he does make a good point that you'll probably have to make sure your laptop has a static address.  192.168.235.253 appears to be a valid one -- but your ISP may prefer you use a different range for statics.  You will need to know your gateway address before doing that, though, otherwise you won't have internet until you go back to DHCP.

Does ddclient manage your dyndns/ipaddress information?  If so, it's doing it just fine -- only problem is that the ip address it's giving their DNS server is a private one.

---

### Post by jv13613 on 2008-11-04
try [http://freedns.afraid.org/]("http://freedns.afraid.org/") free dns

---

### Post by lensark on 2008-11-04
> **davidshere said:**
> Neftali: (is that your name?)

Looking up the IP address for your site:
```
david@raptor:~$ nslookup neftali.homelinux.net
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	neftali.homelinux.net
Address: 192.168.235.253

```
That's not a publicly routable address.  So, when you look at it, you find it just fine, but when I look at it, I get nothing. 

[www.davidshere.com](www.davidshere.com) points to 166.82.96.21.  The computer that hosts my website doesn't have that for an IP address, though.  The router at my ISP (actually the router here at work) re-directs requests for webpages (through port 80) to the computer that hosts my website.  It could be 192.168.235.253 -- same as yours!  Because we can both have the same internal address, but not the same external address.

You need to do two things:  
1.  Find out your publicly routable address.  One way to do this is to go to whatismyipaddress.com.  Then change your DNS so that it points to this address.
2.  Get the router between your laptop and the internet (wherever that is) to redirect web traffic from the public address to your private address.  This router has to be somewhere; otherwise your laptop wouldn't work with a private address.


EDIT:  I just read cariboo907's post more closely, and he does make a good point that you'll probably have to make sure your laptop has a static address.  192.168.235.253 appears to be a valid one -- but your ISP may prefer you use a different range for statics.  You will need to know your gateway address before doing that, though, otherwise you won't have internet until you go back to DHCP.

Does ddclient manage your dyndns/ipaddress information?  If so, it's doing it just fine -- only problem is that the ip address it's giving their DNS server is a private one.


hi david,

first of all, yep neftali is my name :)

"publicly routable address" == external IP address? 

things I need to do:

1.) my external IP address is 125.60.235.215 and I made my dns to point to this address.. so we can say that from neftali.homelinux.net, neftali == 125.60.235.215, is this correct?

2.) 
when I googled "private address" I read this...

"Devices with private IP addresses cannot connect directly to the Internet. Likewise, computers outside the local network cannot connect directly to a device with a private IP. Instead, access to such devices must be brokered by a router or similar device that supports Network Address Translation (NAT). NAT hides the private IP numbers but can selectively transfer messages to these devices, affording a layer of security to the local network."

192.168.235.253 is a private address so you are correct that I am behind a router. But the problem is I never bought a router. So it has got to be from my ISP... I sent an email to my isp customer service with regards to this and I hope I can get a helpful feedback very soon..


"Does ddclient manage your dyndns/ipaddress information?  If so, it's doing it just fine -- only problem is that the ip address it's giving their DNS server is a private one."

Most probably that is the case.






Thanks much david :)

---

### Post by davidshere on 2008-11-04
What is the device on the other end of the network cable connected to your laptop?  Most likely the router is in that device.  Many/most consumer grade "cable modems" have routers/firewalls in them now.  You may or may not be able to access it and configure it.

It's also likely that if you have residential internet service, they won't want you running a webserver on it.  YMMV.

---

### Post by lensark on 2008-11-04
> **cariboo907 said:**
> Basically  you need to set up your server with a static ip address then port forward from that ip address to your router. To set a static ip address you will need to edit /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

then add the following lines to the  file:

```
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Press Ctrl-o to save and Ctrl-x to exit

You will have to substitute your ip address and gateway ip address.

Next setup port forwarding on your router. Forward the ip addressd of the server to port 80 on the router. Every manufacturer does  it differently, so consult your router manual on how to do it.

Next go to [canyouseeme]("http://www.canyouseeme.org/") to check if port 80 is open on your router, or if your ISP is blocking port 80.

Many routers will not let you access your domain name from inside the network, so you will have to be outside your network to try your new web app.

Jim




Yep, I understood that my internal and external IP addresses have to be static. My problem now is when it comes to port forwarding, since I still don't know how to locate my router as I posted above....and this is why I am currently stuck..

---

### Post by lensark on 2008-11-04
> **davidshere said:**
> What is the device on the other end of the network cable connected to your laptop?  Most likely the router is in that device.  Many/most consumer grade "cable modems" have routers/firewalls in them now.  You may or may not be able to access it and configure it.

It's also likely that if you have residential internet service, they won't want you running a webserver on it.  YMMV.


It is a small box like the size of a normal wireless router, so  that is most likely the router. And yes, i have a residential internet service -_-

I will visit my ISP's office tomorrow and ask them questions with regards to setting up a web server. 


nef

---

### Post by lensark on 2008-11-05
Update:

Last night before I headed to bed I emailed SMARTs(ISP) Customer Service, here is the reply:

"We understand you wish to know why you do not have a permanent IP address.

Firstly, Smart Bro is a residential account and the system address being used is DHCP (Dynamic Host Configuration Protocols).

It is a residential package which we designed to only have private IP addresses.

We are giving Public IP addresses to our other packages not intended for residential use.

Lastly, the service is made possible by installing a Smart Bro antenna (also known as Customer Premise Equipment or CPE) at home with a direct 'line-of-sight' to the nearest Smart cellsite offering the strongest possible radio frequency transmission that gives speeds several times faster than any dial up internet connection."

I also went to their main office this morning and got same response from the customer service. And the antenna they are referring has a cable connected to a router and then to my laptop, so the box they installed is really a router.

So I guess I have to find another ISP?

---

### Post by lensark on 2008-11-05
```
sudo nano /etc/network/interfaces
```

then add the following lines to the  file:

```
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```


when I do sudo nano /etc/network/interfaces i get this two lines:

auto lo
iface lo inet loopback


what does this mean? i read from other posts and they seem to have

auto eth0
iface eth0 inet dhcp

initially instead..

what does this mean?..

---

### Post by davidshere on 2008-11-05
> **lensark said:**
> 
It is a residential package which we designed to only have private IP addresses.

Strange, but not necessarily a bad idea.  If you were an average residential consumer that wasn't looking to run a webserver, you wouldn't care if you had a public IP or not.

> **lensark said:**
> So I guess I have to find another ISP?
You could do that, or upgrade to their "other packages not intended for residential use."  With their residential service, what you want to do is impossible.

---

### Post by lensark on 2008-11-06
Update:

So I got the responses from the three ISP's here in my place. They wont allow me to set up a web server unless I upgrade my residential account. =(

The cheapest is like 3x the charge of my current connection. And I can't afford it yet I am still a student. ~_~ 

I will try out setting up in uni next week when school starts ;)

Thank you very much carib and david =)

nef.

---

### Post by cpetercarter on 2008-11-06
I don't think you need to change ISP or change from a residential to a business package. Have a look at [http://www.no-ip.com/]("http://www.no-ip.com/"). It enables you to map a static IP address onto a dynamic one, so that you can always access "myname.no-ip.com" from anywhere, even though your ISP assigns you a different IP address each time you log on. There are several other providers of similar services.

---

### Post by lensark on 2008-11-06
here is my ifconfig:

n3f@n3f-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:30:eb:b6  
          inet addr:192.168.235.253  Bcast:192.168.255.255  Mask:255.255.224.0
          inet6 addr: fe80::21e:33ff:fe30:ebb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72656871 (69.2 MB)  TX bytes:6606462 (6.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121900 (119.0 KB)  TX bytes:121900 (119.0 KB)



if i ping neftali.homelinux.net:
PING neftali.homelinux.net (192.168.235.253) 56(84) bytes of data.

my ip from whatismyip.com: 125.60.235.215


My ISP said they are only giving private IP address, so my IP address should be 192.168.235.253 and not 125.60.235.215..

Can somebody please help me understand the difference of those two IP's....



nef,

---

### Post by lensark on 2008-11-06
> **cpetercarter said:**
> I don't think you need to change ISP or change from a residential to a business package. Have a look at [http://www.no-ip.com/]("http://www.no-ip.com/"). It enables you to map a static IP address onto a dynamic one, so that you can always access "myname.no-ip.com" from anywhere, even though your ISP assigns you a different IP address each time you log on. There are several other providers of similar services.


thnx for this info, i thought it's same with dyndns.. i will look up for this.. just need some understanding about IP's as I posted above...-_-

---

