---
title: "How to ssh from an external location"
date: 2012-04-04
forum: Security
---

### Post by Ms. Daisy on 2012-04-04
I have installed sshd on my home computer, and ssh is installed on my laptop. I disabled passwords & set up the keys. I have successfully ssh'd inside of the LAN, so I know everything is set up properly.
 
Now I want to ssh into the home computer from **outside** of my LAN. I can't find any step-by-step tutorials on this. There are billions of tutorials on how to ssh from inside a LAN, but not from outside the LAN. What I have pieced together from Googling leads me to the following questions:
 
1. I need to set up my home router to port forward. This is where I need detailed instructions that I cannot find. From what I gather I need to use my internal IP (192.168.0.x) of the server and the ssh port (which I changed from 22 to something obscure). Is that it? 
 
2. Whenever I turn my computer off, it gets reassigned a new local IP (192.168.0.x) - do I need to set permanent internal IP addresses for this to work? 
 
3. Do I need sshd installed on both machines? One tutorial made it sound like I do.
 
4. I have a dynamic external IP from my ISP. Can you make it work automatically even if I get a new IP address? Or do I have to configure it each time? Any tutorials on this?
 
Feel free to flame me for missing obvious tutorials as long as you give me some links.

---

### Post by CharlesA on 2012-04-04
1) You need to set up port forwarding on the router. What router do you have?

2) I have my machines set to grab the same IP from DHCP but my server is set with a static IP. I'd go with a DHCP reservation for the box you are going to be trying to ssh into or just set a static IP for it.

3) You only need sshd installed on the box you want to connect to. ssh is installed by default.

4) You can check out something like dyndns. That's what I use, but there are also ones like no-ip.com and others.

---

### Post by SeijiSensei on 2012-04-04
> **Ms. Daisy said:**
>  
1. I need to set up my home router to port forward. This is where I need detailed instructions that I cannot find. From what I gather I need to use my internal IP (192.168.0.x) of the server and the ssh port (which I changed from 22 to something obscure). Is that it?

[Portforward.com]("http://www.portforward.com/") has instructions for most routers.  Just ignore the advertisement for their software and look at the database of instructions.  You'll need to set up a forwarding rule, and you'll need to open the port you choose on the router's external interface.
 
> 2. Whenever I turn my computer off, it gets reassigned a new local IP (192.168.0.x) - do I need to set permanent internal IP addresses for this to work?

If you're using a laptop that you take outside your home, you probably want to go the route of setting up a specific IP assignment for your Ethernet MAC address on your router.  If the machine stays put nearly all the time and is connected over Ethernet, I recommend setting up a [static address]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") on the machine itself.  You do this by editing /etc/network/interfaces.

> 3. Do I need sshd installed on both machines? One tutorial made it sound like I do.
 
As Charles said, you only need sshd on the server.  The client uses the ssh program.

> 4. I have a dynamic external IP from my ISP. Can you make it work automatically even if I get a new IP address? Or do I have to configure it each time? Any tutorials on this?

Does your IP address really change all that often?  Most times if you have a router connected to the Internet that's on 24/7, your address will stay the same for days on end.  Currently I have a residential Verizon FiOS account; my router has had the same address since it was installed a couple months back. I had a similar experience with Comcast, when I had them as a provider some years ago.

Otherwise you'll have to resort to using a service like the ones Charles mentioned.

One other option, though one that costs money, is to rent a virtual machine from some place like [Linode]("http://www.linode.com/").  Then you can install OpenVPN at both ends, and have your home machine connect to the remote server whenever it boots up.  Since the virtual machine has a public static IP, you'll have no problems connecting to it and using the OpenVPN tunnel as a "back door" into your house.

---

### Post by Ms. Daisy on 2012-04-04
A VPN will come after I've figured out ssh first.  Gotta keep it simple for now.

Portforward.com is really idiot-proof, that's a good link.

Thank you, exactly what I needed.  And success- I just connected to my home computer via ssh from my local McDonalds!

---

### Post by dfreer on 2012-04-05
I use DynDNS to always know my current external IP address. The idea is that you install a client (ddclient I believe is in the repositories), which will periodically contact the DynDNS servers with your current external IP address. They provide a free service that will map that external IP address to a friendly name, like mypc.dyndns.org. You simply SSH to that friendly name, in your case specifying the random port that you use.

That handles the external aspect. From there, as mentioned above, you will want to set up port forwarding on your router to redirect incoming traffic on that port to your specific machine. You will want to use some form of static IP address with that machine, at least some way that your router always knows where to redirect the traffic.

Source: Years of running SSH from home. I use a paid for service with DynDNS with my own domain name.

---

### Post by CharlesA on 2012-04-05
> **dfreer said:**
> I use DynDNS to always know my current external IP address. The idea is that you install a client (ddclient I believe is in the repositories), which will periodically contact the DynDNS servers with your current external IP address. They provide a free service that will map that external IP address to a friendly name, like mypc.dyndns.org. You simply SSH to that friendly name, in your case specifying the random port that you use.

That handles the external aspect. From there, as mentioned above, you will want to set up port forwarding on your router to redirect incoming traffic on that port to your specific machine. You will want to use some form of static IP address with that machine, at least some way that your router always knows where to redirect the traffic.

Source: Years of running SSH from home. I use a paid for service with DynDNS with my own domain name.
My IP doesn't change that much, but it's easier to remember a hostname than an IP address, at least for me. Well, unless it's something like 192.168.1.2

I've been tempted to poke around the DNS control panel of my domain registrar and see if I can point a custom URL to my IP at home, but I haven't gotten around to it yet.

---

### Post by SeijiSensei on 2012-04-05
> **CharlesA said:**
> I've been tempted to poke around the DNS control panel of my domain registrar and see if I can point a custom URL to my IP at home, but I haven't gotten around to it yet.

You shouldn't need to do more than add an A record with a hostname and an IP address.

---

### Post by CharlesA on 2012-04-05
> **SeijiSensei said:**
> You shouldn't need to do more than add an A record with a hostname and an IP address.
That's what I was thinking. It was either that or a CNAME pointing to the dyndns hostname. I can't recall exactly.

---

