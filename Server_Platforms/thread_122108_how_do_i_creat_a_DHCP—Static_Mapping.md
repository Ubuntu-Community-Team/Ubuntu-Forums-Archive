---
title: "how do i creat a DHCP—Static Mapping?"
date: 2006-01-26
forum: Server Platforms
---

### Post by bfonseca on 2006-01-26
Hi,
I am trying to figure out a way to set a static dhcp ip address? I like to use ftp and remote desktop and other stuff with my computer but I dont like how I have to always do an ifconfig in the terminal to figure out what my ip address is.  Is there a way to make the dhcp a static Ip address? If so how?
Thanks 
Brian

---

### Post by drogoh on 2006-01-26
If you have control of the DHCP server, yes.

Assuming you have control of the DHCP server and it is on a Linux or Unix computer, you would need this in dhcpd.conf
```

host computer {
  hardware ethernet 00:00:00:00:00:00;
  fixed-address 192.168.0.2;
}

```

Note:  If your IP is obtained via DHCP from your ISP, you will not have any control over it being fixed or dynamic at all.

---

### Post by Iowan on 2006-01-26
I'd agree that a DHCP address for a server is... inconvenient.  Check the /etc/network/interfaces file.  Mine has a section:
iface eth0 inet static
  address 192.168.1.4
  netmask 255.255.255.0
  network  192.168.1.0
  broadcast...  there's more, but you get the idea.

You'll want to pick an address outside the DHCP range.

---

### Post by Tichondrius on 2006-01-26
To summarize what the posters above said, some DHCP servers can indeed assign a fixed IP based on physical address. Many home routers that serve as dhcp servers can do that but you need to go into the router configuration interface to set that up (it's different for each router). 

Your other option is just to stick with static IP and not use DHCP at all on that machine, but then you also have to manually enter the gateway, DNS, mask, etc, so that's why its better to use static-DHCP as I explained above. 

My D-link 624 and Linksys WRT54G routers both support static DHCP. The D-Link is the easiest to set up.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=Iowan]I'd agree that a DHCP address for a server is... inconvenient.[/quote]Nonsense, just have it hand out a static lease.  What's  inconvenient is to not centrally manage addresses.

---

### Post by Tichondrius on 2006-01-27
[QUOTE=LordHunter317]Nonsense, just have it hand out a static lease.  What's  inconvenient is to not centrally manage addresses.[/QUOTE]

agreed, DHCP is a lot more convenient than using static configuration files, even for a server. Just use static-DHCP to make sure the address assigned by DHCP is always the same.

---

### Post by Iowan on 2006-01-27
[QUOTE=LordHunter317]Nonsense, ....[/QUOTE]I am, admittedly, new to the game... but I fail to see where it is nonsense to think > I have to always do an ifconfig in the terminal to figure out what my ip address is. would be considered inconvenient.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=Iowan]but I fail to see where it is nonsense to think  would be considered inconvenient.[/QUOTE]That's not the issue, the issue is with locally-managed static IPs, I lose central management.

If I have 10 boxes, to find out their IPs I either have to:[list][*]Keep a central list[*]Login to every box and determine them[/list]If I'm already keeping a central list, I might as well have the list keeper (DHCP) hand out hte IP addresses for me, which brings a huge number of advantages.

It's a management thing.  DHCP, even with solely static addresses, makes management of your address space eaiser.

---

### Post by bfonseca on 2006-01-27
So it is possible to create a static-dhcp address?  I am using Mediacom for my broadband and they will not let me have a static ip...although the lady had mentioned something about assigning a lease and then came back and said she was wrong. but in a few of the discussions there was mention of assigning a lease(i dont know how to do this or even what it is). I do not have a router and the internet provider assigns dhcp, so am i stuck with dhcp? or can I change it? Is there some kind of script I can use? Can some one tell me a step by step instruction on how to set up the static-dhcp ip? Thank you in advance and about the step by step...only if is not to much trouble for you to take the time to make a set of instructions.
thanks
Brian

---

### Post by LordHunter317 on 2006-01-27
You're stuck with whatever your ISP hands you out.  We're talking about internal management of IP addresses.

---

### Post by Tichondrius on 2006-01-27
Yeah, ISPs usually don't give static addresses, BUT note that your address can change only when you disconnect (switch your machine off).  The way the DHCP protocol works is first the client (your PC in this case) broadcasts a request which the DHCP server answers by assigning the client an address, in addition to giving it other configuration info like the netmask, DNS server, etc. This is called a "lease" because the given address is only valid for a few days, after which it has to be renewed. If it's not renewed then the DHCP server may give this address to another client.

So if your PC is always ON (never turned off), it will automatically renew the DHCP lease indefinetly. So in fact your address will never change in this case.  But if your PC is turned off, the DHCP "lease" may expire and not be renewed, so next time your switch on and connect to the internet, you will get a new address.

Many people don't want to keep their machines on all the time, so what you can do is get a home broadband router which acts as a DHCP client that always renews the lease (because the router is always on) so the address never changes. your home PCs are then connected to your router which assigns them private IP addresses (ausing DHCP protocol again between the your router and your PCs). If you want to use one of these PCs as a server visible on the internet then you have to forward the relevant ports from your router to that PC.

This setup (using a home router) guarantees that you will have fixed address even if your ISP only assigns dynamic address using DHCP. It also has other advantages as far as security because your router will act as a NAT firewall, which is the most important basic line of defense.

---

### Post by bfonseca on 2006-01-28
Tichondrius thanks for the info...wow that was a great discription. I think I will do that then. What would you recommend for a broadband router?
Brian

---

### Post by imagine on 2006-01-28
[QUOTE=Tichondrius]So if your PC is always ON (never turned off), it will automatically renew the DHCP lease indefinetly. So in fact your address will never change in this case.  But if your PC is turned off, the DHCP "lease" may expire and not be renewed, so next time your switch on and connect to the internet, you will get a new address.[/QUOTE]This really depends on the ISP.
Eg my ISP (and most others in my area) drop the connection after 24 hours if I don't logoff myself. So I cannot have the same IP address for more than one day.

And to be precise DHCP isn't used for assigning IP addresses in my case anyway, but more PPPoE and Radius : )

---

### Post by Iowan on 2006-01-29
[QUOTE=bfonseca]Tichondrius thanks for the info...wow that was a great discription. I think I will do that then. What would you recommend for a broadband router?
Brian[/QUOTE]Depending on how much you want the router to do, whether you want it off-the-shelf or would like to build one... there are several one-floppy routers you could try.  I like [FREESCO](http://forums.freesco.org/support/).

---

### Post by Tichondrius on 2006-01-29
[QUOTE=Iowan]Depending on how much you want the router to do, whether you want it off-the-shelf or would like to build one... there are several one-floppy routers you could try.  I like [FREESCO](http://forums.freesco.org/support/).[/QUOTE]

No, I'm talking about a small router appliance, not a PC acting as a router (although that is possible, it is an overkill for home users). 

I can recommend the D-Link DI-624 which is a wireless router, as well as a 4-port switch. This means that you can connect 4 PCs to the router using regular ethernet cables, and also you can connect to it wirelessly from a PC equipped with a Wifi card (e.g. a laptop). The router is connected to your cable or DSL modem, and then your PCs connect to the router.

This router has the best performance amongst 54g wireless routers, and has a very good interface so it's very easy to set up all the options including DHCP settings etc.

I've been using this router for a few years, and the address assigned to me by my ISP (comcast) has not changed for as long as I can remember. I'm also running a web server on one of my home PC's and it's accessible from the internet.

---

