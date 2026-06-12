---
title: "How do I connect my Ubuntu server with a static IP?"
date: 2012-08-01
forum: Server Platforms
---

### Post by Maheriano on 2012-08-01
I just installed Ubuntu Server on a little home server I have and it's working great except I took it to the client's house and he has a static IP on his home network. I set that up on his wireless switch and also his laptop so everything in his house connects fine except all those machines are Windows. When it came time to connect the Ubuntu server on the static IP I couldn't figure it out.

I changed the file /etc/network/interfaces to change it from a DHCP connection to a static connection using his credentials, here's how it looked:

iface eth0 inet static
address 184.70.214.XXX
netmask 255.255.255.XXX
network 184.70.214.0
broadcast 184.70.214.0
gateway 184.70.214.XXX
dns-nameserver 64.59.135.XXX 64.59.128.XXX

I set the address as the static IP I was given from my ISP. I set the netmask as the Subnet Mask I was given and I set the gateway as the Gateway I was given.

I'm really not sure what to set the rest to, I just guessed based on what came up on Google, is it right? Is there anything else I need to change? I also ran a few commands afterwards:
```
sudo ifdown eth0
sudo ifup eth0
sudo service networking restart
```

What else do I need to do? When I look at the connected devices in the administrative panel for the wireless switch it's not listed like it was back when everything was on DHCP. And when I forward the static IP through port 80 to the internal IP of the server (192.168.0.101) I get "Page Not Found" because it's not connected to the static IP service.

Any ideas? Thanks. The ISP is Shaw if that matters and port 80 is definitely open.

---

### Post by spynappels on 2012-08-02
Hi,

Could you clarify the setup a little for me?

Does he have a router with a static public IP and all his nodes in the local network set with static LAN (private) IPs, or are all the nodes assigned different static public IPs?

---

### Post by darkod on 2012-08-02
Couple of things:

1. The broadcast value is wrong. The 'network' ends with .0 and 'broadcast' ends with .255 but the best is not to bother with them at all. The network service knows how to work even if they are not specified. The important values to specify in /etc/network/interfaces are:
address
netmask
gateway
dns-nameservers

That's it.

2. Before trying to use the public IP on the server you need to clarify the setup, does it have a router in between or not. Yes, the ISP gave you the values but those might be the values assigned for the subscriber's router. Once the router does it's NAT, you use the server with a static private IP, not public.

In other words, if that public IP is assigned to the router that your client has in his house, you can't expect to configure the same IP on a second device right?

If there is a router, the LAN portion would probably work as a network in the 192.168.x.x range.

---

### Post by LHammonds on 2012-08-02
> **Maheriano said:**
> 
dns-nameserver 64.59.135.XXX 64.59.128.XXX

This is also incorrect.  It is plural.

dns-nameserver[COLOR=Red]s[/COLOR] 64.59.135.XXX 64.59.128.XXX

---

### Post by Maheriano on 2012-08-02
> **spynappels said:**
> Hi,

Could you clarify the setup a little for me?

Does he have a router with a static public IP and all his nodes in the local network set with static LAN (private) IPs, or are all the nodes assigned different static public IPs?
He has a modem with a static IP and also a wireless switch behind that which I also set up for the static IP. Then I went into his Windows laptop and set that up to request the static IP so when he gets online with his laptop it works great.

> **darkod said:**
> Couple of things:

1. The broadcast value is wrong. The 'network' ends with .0 and 'broadcast' ends with .255 but the best is not to bother with them at all. The network service knows how to work even if they are not specified. The important values to specify in /etc/network/interfaces are:
address
netmask
gateway
dns-nameservers

That's it.

2. Before trying to use the public IP on the server you need to clarify the setup, does it have a router in between or not. Yes, the ISP gave you the values but those might be the values assigned for the subscriber's router. Once the router does it's NAT, you use the server with a static private IP, not public.

In other words, if that public IP is assigned to the router that your client has in his house, you can't expect to configure the same IP on a second device right?

If there is a router, the LAN portion would probably work as a network in the 192.168.x.x range.
So I wouldn't set up the server for a static public IP but instead with a static private IP? How would that help? You mean like DHCP reservation?

I talked to the guy at Shaw (his ISP) because the modem kept getting the old random IP instead of the static and he said it's because something behind it was requesting the old IP. He told me to set up the computers for the static IP which is what I did, rebooted and then the modem got the static IP like it should. So that's why I think I need to tell the server to request the static IP. Is this wrong?

> **LHammonds said:**
> This is also incorrect.  It is plural.

dns-nameserver[COLOR=Red]s[/COLOR] 64.59.135.XXX 64.59.128.XXX

Sorry, I wrote that wrong, I did have it as plural.

---

### Post by darkod on 2012-08-02
When you say "tell it to request that public IP" you mean to configure the public IP as gateway?

The basic rule is the same for both public and private networks: one IP one device. Period. You can not have the same IP on two devices on the same network. How would the data know where to go?

So, it seems you only have a modem from the ISP which does no routing and no NAT. What is connected after the modem? The wi-fi router you mentioned?

Also, you said wi-fi switch but I guess you meant router because a switch is only a switch and has no routing capabilities between networks. And I have never heard of a wi-fi switch.

If it's a wi-fi router we are talking about, it should have one WAN network port and probably four LAN ports. You would set the public static IP on the WAN port and connect it to the modem.
In the router then you would configure the LAN options, what network it works for (like 192.168.x.x), whether it runs DHCP server, etc.

Lets say your router has the LAN private IP of 192.168.1.1 and it runs DHCP server issuing addresses from 192.168.1.100 to 192.168.1.150.

You can use any address outside the dhcp range as static on the server. For example, set the server with something like:
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4 (Google dns, you can use your ISP dns if you prefer)

After that the server should have working internet. Also any other computers in the network, especially if they are configured for automatic dhcp they will be receiving IPs from the router dhcp server.

For any services you want accessible from the outside, you will need on the router to forward the correct ports to the server private IP 192.168.1.10
For web, you forward port 80, for SSL port 443, etc.

The public IP goes to only one device, remember. To which device, depends on the (home) network setup.

---

### Post by Maheriano on 2012-08-02
First I want to say thanks for helping me out, this is very important to get fixed very soon.

> **darkod said:**
> When you say "tell it to request that public IP" you mean to configure the public IP as gateway?
I'm sorry I don't understand this, I went into the internet setup on the D-Link wireless switch (router I guess) and configured it to request that static IP instead of using DHCP. It seemed to work.

> **darkod said:**
> The basic rule is the same for both public and private networks: one IP one device. Period. You can not have the same IP on two devices on the same network. How would the data know where to go?
So are you saying since I configured his laptop to get that static public IP then that's why the server isn't working? So I need to change the laptop back to request a dynamic IP from the network and let the server use the static? But I thought the static IP only went as far as the modem and then the router controlled all the internal IP from there. Can a single computer behind the router actually get the static IP I was given by Shaw?

> **darkod said:**
> So, it seems you only have a modem from the ISP which does no routing and no NAT. What is connected after the modem? The wi-fi router you mentioned?
Correct, just a modem from them. Yesterday I just bought one of the new D-Link wireless routers and put that behind it and connected all his devices to that via wireless. Plus the server which is wired. It's a little home Acer server box I got for $1000.

> **darkod said:**
> Also, you said wi-fi switch but I guess you meant router because a switch is only a switch and has no routing capabilities between networks. And I have never heard of a wi-fi switch.

If it's a wi-fi router we are talking about, it should have one WAN network port and probably four LAN ports. You would set the public static IP on the WAN port and connect it to the modem.
In the router then you would configure the LAN options, what network it works for (like 192.168.x.x), whether it runs DHCP server, etc.
Sorry, it is a router I guess, some D-Link 8XX I got from Futureshop for $!00. It does have a single WAN port and 4 LAN ports. WAN is connected to the modem and the server is wired to the LAN. I went into the administrative panel (192.168.0.1) and configured it to use a static IP with the proper gateway and subnet mask I was given by my ISP. Once I rebooted everything I checked the (public) IP I got from his laptop and it was the correct static one I'm supposed to have (listed in first post). Is that right?

> **darkod said:**
> Lets say your router has the LAN private IP of 192.168.1.1 and it runs DHCP server issuing addresses from 192.168.1.100 to 192.168.1.150.

You can use any address outside the dhcp range as static on the server. For example, set the server with something like:
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4 (Google dns, you can use your ISP dns if you prefer)

After that the server should have working internet. Also any other computers in the network, especially if they are configured for automatic dhcp they will be receiving IPs from the router dhcp server.
So this part is only to get a specific internal IP from the router? There's nothing here to do with requesting the static IP? So it's basically like DHCP reservation to make sure it always gets the same internal IP? Or is there another purpose?

> **darkod said:**
> For any services you want accessible from the outside, you will need on the router to forward the correct ports to the server private IP 192.168.1.10
For web, you forward port 80, for SSL port 443, etc.
Ya, I have port forwarding set up on my home network with DHCP, I can do this once I get connected properly.

> **darkod said:**
> The public IP goes to only one device, remember. To which device, depends on the (home) network setup.

I'll tell you something else I did and now I'm wondering why this didn't work. I had this server set up at my house here on DHCP and I forwarded port 80 and was able to access it using my public IP, it worked great. Then I took it to its new home at a house with a static IP and am setting this up. I configured the wireless router to work with the static IP, rebooted everything and got the proper IP. I didn't do any changes on the server and when I looked in the D-Link administrative panel I could see it connected as 192.168.0.101 but the server name didn't show up, no big deal I guess. I connected to the web server in the browser using the internal private IP and it worked great. I forwarded port 22 and port 80 and couldn't get a response through neither of them via the public static IP so I was thinking it was because of something I needed to configure on the server. Should I not be configuring anything? Should I change it back? Do I need to do this? I know I'm port forwarding correctly, I got the same ISP and same router at my house, I use it all the time and am very familiar with port forwarding (not that it's hard).

---

### Post by darkod on 2012-08-02
Yes, going into the router web GUI and setting it up with the public static IP on the WAN port was correct. I guess all his wi-fi devices have working internet.

One more yes, go into the laptop network settings and put it back to automatic (dhcp). It will receive automatic IP from the router.

When you connected the server first time and still had the dhcp setting, it got the 192.168.0.101 address and it seems the router issues the IPs from .100 onwards. You should be OK assigning a lower IP to the server, like 192.168.0.10.

There are different ways to do this, you can also reserve a particular IP in the router for a particular machine, but I prefer to do it on the server in /etc/network/interfaces. So, open that file and make sure it has something like:

```
auto eth0
iface eth0 inet static
   address 192.168.0.10
   netmask 255.255.255.0
   gateway 192.168.0.1
   dns-nameservers 8.8.8.8 8.8.4.4 (or the IPs you have in your first post)
```

That should give the server working internet. Adjust the port forwarding in the router GUI to forward the ports you need to 192.168.0.10 (the static IP of the server). That should do it for you.

---

### Post by Maheriano on 2012-08-02
I set up the IP with the settings you posted and it still didn't work. Then I realized I could ping external domains which meant I had internet and when I did ifconfig it was showing the IP I had told it to request. So everything looked right but when I tried to forward any of the ports to it, it just timed out, I couldn't figure out why. I couldn't even SSH into my laptop, none of the port forwarding worked.

Then I had a stroke of genius, I tried putting in the public IP on my phone to see if the port forwarding was working and indeed it was. The only problem I was having this whole time is that the ISP blocked access to the public IP from inside the network (I guess). For some reason if you're on the network, there's no way to ping the public static IP, it just times out. Is this common?

Anyway, it's working great now, thanks guys!

---

### Post by spynappels on 2012-08-03
> **Maheriano said:**
> The only problem I was having this whole time is that the ISP blocked access to the public IP from inside the network (I guess). For some reason if you're on the network, there's no way to ping the public static IP, it just times out. Is this common?


This is actually an issue with your router rather than your ISP. Most routers do not have this "loopback" facility where you could use the external IP from inside the LAN, the only routers where I've seen it work reliably is some Linksys and routers using dd-wrt firmware.

Glad it's working for you anyway.

---

### Post by darkod on 2012-08-03
Yeah, if you need to open your own website from the internal LAN, I think what you need to do is add in hosts file something like:

192.168.0.10 [www.mydomain.com](www.mydomain.com)

That will tell the computer(s) that mydomain.com is actually on the local webserver with IP 192.168.0.10.

---

### Post by Maheriano on 2012-08-03
> **spynappels said:**
> This is actually an issue with your router rather than your ISP. Most routers do not have this "loopback" facility where you could use the external IP from inside the LAN, the only routers where I've seen it work reliably is some Linksys and routers using dd-wrt firmware.

Glad it's working for you anyway.

My D-Link 628 allows it. Can I change it on his 81X model?

---

### Post by spynappels on 2012-08-05
I don't think so, if it is possible, it would normally be enabled by default.

---

