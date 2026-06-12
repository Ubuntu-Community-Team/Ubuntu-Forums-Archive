---
title: "Can't connect to LAMP externally"
date: 2008-10-31
forum: Server Platforms
---

### Post by tamasys on 2008-10-31
Hi there.
I'm kinda new to Linux, but I have been trying to set up a LAMP server to run a small website off. I have installed Ubuntu Server 8.04 with a Xubuntu GUI, and it has Apache, MySQL, and PHP5 set up on it.

The problems I am having are that I tried to set up port forwarding for port 80 with my router/modem (Netgear DG834G), and now I cannot access the internet from the server, but I can ping other computers on the LAN, and I can't access the server from outside the LAN. I tried disabling the forwarding, but I still can no longer connect to the internet from the server.

The port forwarding is working, because if I type in my external IP in a computer on the LAN, it connects to the server, but canyouseeme.org gives me a "Connection timed out" error.
I can't work out why this is happening. Is there something I haven't configured on the server?

---

### Post by valentin.dumitran on 2008-10-31
What does *ifconfig* display? What about *traceroute google.com* or *traceroute 72.14.207.99*?

You probably didn't setup the corect gateway on your server.

---

### Post by tamasys on 2008-10-31
*ifconfig* outputs:
```

eth0      Link encap:Ethernet  HWaddr 00:d0:59:2d:9b:28  
          inet addr:192.168.0.100  Bcast:192.168.0.225  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe2d:9b28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72156 (70.4 KB)  TX bytes:192889 (188.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)

```
I can't use traceroute because I don't have it installed, and I obviously can't use the internet to get it...

I think that the gateway is correct, because I have had internet access on the server before.

---

### Post by valentin.dumitran on 2008-10-31
The broadcast address shoud be 192.168.0.2**5**5, but that shoudn't affect your internet connection.

If your ip address is assigned via DHCP, you should check your router settings; maybe you filtered the mac or something. If you set up your ip address manualy, try *cat /etc/network/interfaces*.
You should see something like:
```

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

```
Gateway should be the address of your router. If it's not, correct it, then type *sudo /etc/init.d/networking restart* to reload your configuration.
Try to ping your router from your linux box and see if it responds, or try to open the routers administration page from it.

Before you do all that, please check if the network cable is connected. :D I spent a couple of hours once for a problem like this. :D

---

### Post by hrod beraht on 2008-11-01
> **tamasys said:**
> ...I tried to set up port forwarding for port 80 with my router/modem (Netgear DG834G), and now I cannot access the internet...

Well since your problem started after trying to do the port forward, that seems like a logical place to start.
Here are the instructions from PortForward.com on how to [[COLOR="Blue"]forward port 80 with the Netgear DG834G router[/COLOR]]("http://portforward.com/english/routers/port_forwarding/Netgear/DG834G/HTTP.htm").

Bob

---

### Post by eighto2 on 2008-11-01
Who is your ISP? 
Some ISPs block the use of port 80 for serving, like verizon for example... You can still use 80 to browse but nothing can come in... try switching it to 8080 and test it externally to see...

Also

> **tamasys said:**
> 
I can't use traceroute because I don't have it installed, and I obviously can't use the internet to get it...

I think that the gateway is correct, because I have had internet access on the server before.

What does your /etc/resolv.conf file look like?

---

### Post by tamasys on 2008-11-01
> **eighto2 said:**
> Who is your ISP? 
Some ISPs block the use of port 80 for serving, like verizon for example...

I am fairly sure that port 80 is unblocked, I am using Netspace.

> **eighto2 said:**
> 
What does your /etc/resolv.conf file look like?

My resolv.conf says "nameserver 192.168.0.1"

> **hrod beraht said:**
> Here are the instructions from PortForward.com on how to [[COLOR="Blue"]forward port 80 with the Netgear DG834G router[/COLOR]]("http://portforward.com/english/routers/port_forwarding/Netgear/DG834G/HTTP.htm").

Bob

The instructions are for an older version of the firmware I think, because the router has the HTML service set up already, but everything else was the same as how I had done it.

> **valentin.dumitran said:**
> If you set up your ip address manualy, try *cat /etc/network/interfaces*.
You should see something like:
```

iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

```

I had all the 255s as 225 (oops) but i have changed them now, still no difference.

> **valentin.dumitran said:**
> 
Try to ping your router from your linux box and see if it responds, or try to open the routers administration page from it.
I can ping the router, other computers on the network, etc, but nothing outside the LAN.

**EDIT:** Hmm... [ShieldsUP!]("https://www.grc.com/x/portprobe=80") says that port 80's status is "Stealth". What does that mean?

---

### Post by eighto2 on 2008-11-03
It means, you either do not have the ports forwarded. 
Or your isp is blocking port 80 connections.

---

### Post by WhiteShepherd on 2008-11-03
With loss of net access but sites can still access your server?  Sounds like it may be a DNS issue.  

You can test this by doing a ping on yahoo.com

Type: ping 206.190.60.37   (you can exit with a crtl-c)

If this works that IP does not require DNS.

Now type: 
ping yahoo.com   

If the previous IP works but the name you just typed in now fails you most likely have DNS issues.  I notice your DNS is set to your gateway (192.168.0.1). I've seen problems before using a router as a DNS forwarder. I'd try changing your server DNS that to your REAL ISP's DNS server/s then renew your DHCP connection to your router.

Type:
sudo dhclient -r
sudo dhclient

Good luck.

---

### Post by tamasys on 2008-11-03
> **WhiteShepherd said:**
> I've seen problems before using a router as a DNS forwarder. I'd try changing your server DNS that to your REAL ISP's DNS server/s then renew your DHCP connection to your router.

Type:
sudo dhclient -r
sudo dhclient

Good luck.

Wow! Thanks! I fiddled around with a couple settings (and realised that a few 255s were written as 225s...), but nothing happened, and then I used sudo dhclient -r and it worked! Thanks heaps!

---

