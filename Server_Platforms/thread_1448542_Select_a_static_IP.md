---
title: "Select a static IP"
date: 2010-04-06
forum: Server Platforms
---

### Post by cbecker78 on 2010-04-06
Newb warning:  This is probably a dumb question but I cannot find the answer to it.  How do I decide *what* IP address to enter in my config file when assigning a static IP.  

All of the instructions I can find say something like "of course you should modify the file according to your own settings."

Should I just use the gateway and IP that returns from "iwconfig" and "route -nee"?

reading through some forum posts, it looks like some users even use the same IP...  So how would an ssh client know the difference?

:confused:

---

### Post by lisati on 2010-04-06
My own preference is to let my router choose an IP address for the machines connected to it. When it comes to setting a static IP address, I make sure the machine is connected, and use the router's control panel to tell the router to use a static IP address for that machine - on my main router the option is labelled "Use the same address". 

Some IP addresses are public (what people can see and possibly access from the internet) and some are local (only seen on your local network). The local addresses are often in the ranges 192.168.x.x and 10.x.x.x

One of the reasons I prefer to let my router choose an IP address instead of setting it on the computer's end is that if I decide that, for example, 192.168.1.2, is a good local IP address on my network for my laptop, and then I use my laptop somewhere else, it might not work too well because the other person might have decided that 192.168.1.2 should be used for *their* computer.

Hope this helps.

---

### Post by cbecker78 on 2010-04-06
Thanks!  I'm not sure how to get my router to do that, but I will look into it.  You've definitely helped me understand (I think) why I could ssh into my server while at home, but not when I went to work.  I think the dchp had it assigned with a local IP.

I'll see how far I can get with this new info...

---

### Post by romeroc24 on 2010-04-06
> **cbecker78 said:**
> Newb warning:  This is probably a dumb question but I cannot find the answer to it.  How do I decide *what* IP address to enter in my config file when assigning a static IP.  

All of the instructions I can find say something like "of course you should modify the file according to your own settings."

Should I just use the gateway and IP that returns from "iwconfig" and "route -nee"?

reading through some forum posts, it looks like some users even use the same IP...  So how would an ssh client know the difference?

:confused:

The minimun data in your conf file must be like (# are comments):

```

$ sudo vim /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth1 inet dhcp
iface eth0 inet static
address 192.168.1.254
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

---

### Post by haddog on 2010-04-06
> **cbecker78 said:**
> Newb warning:  This is probably a dumb question but I cannot find the answer to it.  How do I decide *what* IP address to enter in my config file when assigning a static IP.  

All of the instructions I can find say something like "of course you should modify the file according to your own settings."

Should I just use the gateway and IP that returns from "iwconfig" and "route -nee"?

reading through some forum posts, it looks like some users even use the same IP...  So how would an ssh client know the difference?

:confused:

romeroc24 gave a great example. you need to edit the interfaces file located in /etc/network/interfaces .

Use your editor of choice. romeroc24 used vim, i like nano. 

Regarding ip's. I use one outside of the router dhcp assigned ip's. So my router uses 192.168.1.2 thru 102.168.1.50 for ip's it assigns. So when I assigned a static ip of 192.168.1.101  - anything in the 100's I know is a server, with .101 being the 1st server, .102 the 2nd, .103 the 3rd server and so on. I do this so I am consistent. Just my 2 cents.

---

### Post by cbecker78 on 2010-04-07
> **romeroc24 said:**
> The minimun data in your conf file must be like (# are comments):

```

$ sudo vim /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth1 inet dhcp
iface eth0 inet static
address 192.168.1.254
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

Hi, thanks.   That is pretty much how I have it set up.  (I'm assuming the order isn't important, since I have gateway after netmaks and network?)  My question was pertaining to what ways i "pick" what address to enter.  i.e., how did you choose '245' as the last three digits. Because I didn't want to be the same as someone else.

I have since learned thanks to info from lisati (And please correct me where I am wrong) that the static IP address set to my box in an internal IP, and only used within my network.  So I want to simply pick the 3 digits such that they would be higher than what gets randomly assigned by my router.

In order to connect from the outside world, I need a static public IP from my ISP, and to set up a port forwarding protocol on my router to take incoming requests on my public IP and route them to the assigned internal IP of my server.

Does that sound about right?

Edit: @ haddog; 
> Regarding ip's. I use one outside of the router dhcp assigned ip's. So my router uses 192.168.1.2 thru 102.168.1.50 for ip's it assigns. So when I assigned a static ip of 192.168.1.101 - anything in the 100's I know is a server, with .101 being the 1st server, .102 the 2nd, .103 the 3rd server and so on. I do this so I am consistent. Just my 2 cents.ah... I didn't see your post; this looks like it is confirming what I was thinking about internal IPs.  Thanks~

---

