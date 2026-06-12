---
title: "remote access to server from internet"
date: 2008-07-10
forum: Server Platforms
---

### Post by derekroyce on 2008-07-10
I can use PuTTY to access my driver on my home network.

But I can't figure out how to get access via internet from work.

I have the ip address for the router, but I don't know how to figure out the address to use to access the server. 

I know the internal network address of the server but how do I get to that from the internet.

I've Googled this until my eyes have fallen out.

---

### Post by cdenley on 2008-07-10
Try googling "port forwarding". From the internet, you can only connect to the router. You have to tell the router to forward connections on port 22 to your LAN IP.

---

### Post by carcdrcdr on 2008-07-10
Simple.  You need to enable port forwarding from your router to your box in question.  This is usually done from your routers web console.  Check your routers manual or search the internet on how to enable port forwarding on your router.

Port forwarding will cause your router to send requests from a port you define to an internal port on a computer in your network.  **I highly recommend NOT using port 22 on your router.  Hackers know that ssh logins are done via port 22 and will scan vast amounts of IP address just to attack you :(**

The way around this is to set up port forwarding on an different port on your router.  For example:

Set up your router to forward port 8888 to your machines internal IP address on port 22.  This will make it harder for attackers to locate your machine.  When you putty to your machine from the outside world you will just have to select port 8888 when you enter your external IP address.  (Note: use any port in the 1000-8000 range and you should be fine)

More info on port forwarding: [http://en.wikipedia.org/wiki/Port_fowarding](http://en.wikipedia.org/wiki/Port_fowarding)

I also recommend: [http://www.dyndns.com/](http://www.dyndns.com/) or another source for DynamicDNS service so you do not have to remember your IP address.

---

### Post by Traumadog on 2008-07-10
> **derekroyce said:**
> I can use PuTTY to access my driver on my home network.

But I can't figure out how to get access via internet from work.

I have the ip address for the router, but I don't know how to figure out the address to use to access the server. 

I know the internal network address of the server but how do I get to that from the internet.

I've Googled this until my eyes have fallen out.

Hi derekroyce,

To access your server from the internet, you'll need the following:

1.  You'll need the IP address assigned to you by your home Internet Service Provider (ISP).  If you don't know that address, you can goto [http://whatismyipaddress.com/](http://whatismyipaddress.com/) from your home computer to get the address. That website will report back the IP address of the computer that contacted it.

2.  Enter the IP address assigned to you by your home ISP in the "Host Name - IP Address" box on the PuTTY configuration screen and try to connect.

Please note:  You'll need to make sure the firewalls in your router and/or server will accept a connection over port 22 (or whatever port you've picked for ssh communications) from outside your internal network.  You'll also need to make sure that port is not being blocked by your ISP as well.  Also, be aware that unless you have a static IP address provided to you by your ISP, your IP address will be subject to change from time to time.  You can overcome this problem, however, by signing up with a service such as DynDNS ([www.dyndns.com](www.dyndns.com)).

Hope this helps!  :)

Traumadog.

---

### Post by derekroyce on 2008-07-17
Thanks this helped a lot.

I will work on changing my port from 22 to something else for security.
Also, sign up with DynDNS.

---

### Post by hyper_ch on 2008-07-17
I wouldn't bother about changing port 22. It's mostly script kiddies that use bots to guess a password. Use a secure password and install denyhosts or fail2ban.

---

### Post by Traumadog on 2008-07-17
> **derekroyce said:**
> Thanks this helped a lot.

I will work on changing my port from 22 to something else for security.
Also, sign up with DynDNS.


I'm glad to have been of help.

Best wishes, :)

Traumadog.

---

