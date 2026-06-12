---
title: "Trying to set up a private LAMP webserver"
date: 2009-12-18
forum: Server Platforms
---

### Post by thebrotherofasis on 2009-12-18
Dear people,

I recently installed an Apache + Mysql + PHP webserver in my ubuntu 9.10 desktop. If I go

```
http://localhost/
```

or 

```
http://192.168.2.101
```

the server is accessed perfectly.

Now, what I would like to do is to be able to have other computers in my wlan access the server created in the desktop where I installed the webserver.

So far, I have had no success, and I identified it was due to the firewall (I'm using **ufw**), since when I disable it from the server, I can access the webserver right from other computers in my wlan.

So, what rule should I add to the firewall to permit access to the webserver?

Thank you!

---

### Post by c9-3Rr0r on 2009-12-18
Default apache uses port 80 on tcp protocol. So u should add that rule to yours ufw. 
```

sudo ufw allow 80/tcp

```

---

### Post by cdenley on 2009-12-18
To allow only your LAN, in case WAN connections somehow get routed to your server:
```

sudo ufw allow proto tcp from 192.168.2.0/24 to any port 80

```

---

### Post by thebrotherofasis on 2009-12-18
I did 

```
sudo ufw allow proto tcp from 192.168.2.0/24 to any port 80
```

and it worked partially, since it seems that computers connected via wire to the same wireless router that the server is connecting to, can't access the server.

Anything else I should do to make the server accessible even to those computers who are not under WLAN but LAN?

Additionally, I'd like to know how I can find out which ports are used by different servers, so that I can learn how to create these rules?

Finally, what does the "/24" mean in "192.168.2.0/24"?

Thanks again!

---

### Post by thebrotherofasis on 2009-12-18
I just realized I only needed to restart the server machine, and now all the wan and lan computers can access it to its ip address.

Also, I found after doing a little research, that in order to find out which ports are open I can do:

```
sudo netstat -lntup
```

or, a little more specific

```
sudo netstat -anp --tcp --udp | grep LISTEN
```

Now, the question that comes to my mind is how can I make other computers access the webserver, not through typing the ip address in the browser, but through typing a more human-readable address? 

Does this have to do with assigning domain server names or something?

How can I, for example, replace "192.168.2.101" in my server to something like "localhost.somename"?, and make it accessible to all computers in my wlan (lan)?

Thanks.

---

### Post by Cheesemill on 2009-12-18
The easy way is to edit the hosts file on all of the machines in your network, you can find it at /etc/hosts (I can't remember where it is in Windows but a quick Google will find it for you).

The hard way is to set up an internal DNS server.

---

### Post by memilanuk on 2009-12-19
> The hard way is to set up an internal DNS server.

Not so hard if you use dnsmasq...

---

### Post by cdenley on 2009-12-19
> **thebrotherofasis said:**
> i did 

```
sudo ufw allow proto tcp from 192.168.2.0/24 to any port 80
```

and it worked partially, since it seems that computers connected via wire to the same wireless router that the server is connecting to, can't access the server.

Anything else i should do to make the server accessible even to those computers who are not under wlan but lan?

Additionally, i'd like to know how i can find out which ports are used by different servers, so that i can learn how to create these rules?

Finally, what does the "/24" mean in "192.168.2.0/24"?

Thanks again!
The "/24" is the subnet mask. It is used to give a range of IP's.

192.168.2.0/24 = 192.168.2.1 - 192.168.2.254
192.168.0.0/16 = 192.168.1.1 - 192.168.254.254

---

### Post by BkkBonanza on 2009-12-19
Just a few brief notes.

The netstat command actually doesn't show you which ports are open but what programs are listening on what ports. They aren't always the same as the firewall could be block a port that some program is listening on.

More generally, the notation /24 refers to the first (most significant) 24 bits of the address being masked, leaving the last 8 bits open for use (256 addresses). You could have any value between 1 and 32 but the most common are /8 (class A), /16 (class B), /24 (class C). A whole address is 32 bits so /32 would mean that address range (network) only contains one possible address. /31 has 2, /30 has 4 etc.

Many/most routers can provide local DNS for you. For example, the popular Linksys WRT-54 (mine) runs dnsmasq which has a DNS function. Adding names to your router would be the simplest way to have them resolv for your LAN. As long as your LAN computers have the router ip in their resolv.conf they will ask the router, and if the router doesn't know it gets relayed out to your ISP or some other DNS you configure.

---

### Post by wojox on 2009-12-19
I've got a router and use it as for my firewall. No need for two. Here's a guide to get a domain name:
 [HOWTO: Setup an Apache Web Server For Free ($0)]("http://ubuntuforums.org/showthread.php?t=632841")

---

### Post by thebrotherofasis on 2009-12-19
> **BkkBonaza said:**
> Just a few brief notes.

The netstat command actually doesn't show you which ports are open but what programs are listening on what ports. They aren't always the same as the firewall could be block a port that some program is listening on.

More generally, the notation /24 refers to the first (most significant) 24 bits of the address being masked, leaving the last 8 bits open for use (256 addresses). You could have any value between 1 and 32 but the most common are /8 (class A), /16 (class B), /24 (class C). A whole address is 32 bits so /32 would mean that address range (network) only contains one possible address. /31 has 2, /30 has 4 etc.

Many/most routers can provide local DNS for you. For example, the popular Linksys WRT-54 (mine) runs dnsmasq which has a DNS function. Adding names to your router would be the simplest way to have them resolv for your LAN. As long as your LAN computers have the router ip in their resolv.conf they will ask the router, and if the router doesn't know it gets relayed out to your ISP or some other DNS you configure.


Thank you for your comments.

1) If a firewall is blocking a port that a program is listening for, it means some ports are may not be listed by the netstat command? Then, is there any other command I can use to list all open ports, regardless of possible firewall deny rules?

2) For example: if I allow in the firewall the following IP range:

192.0.0.0/8

It means that it will permit connections from 192.1.1.1 to 192.254.254.254 ?

3) I found that this is a good link to expand on the knowledge of this topic: ```
http://en.wikipedia.org/wiki/Subnetwork
```

4) Thanks for the tip on adding the names to my router.

---

### Post by thebrotherofasis on 2009-12-19
> **wojox said:**
> I've got a router and use it as for my firewall. No need for two. Here's a guide to get a domain name:
 [HOWTO: Setup an Apache Web Server For Free ($0)]("http://ubuntuforums.org/showthread.php?t=632841")

Thank you very much for this tutorial... I was acutally googling for this topic, and it seems like a nice how to.

You mentioned > This guide is not for setting up LAMP servers (Linux, Apache, MySQL, PHP/Perl/Python) but I suppose it works for a LAMP server too?

---

### Post by BkkBonanza on 2009-12-19
> **thebrotherofasis said:**
> Thank you for your comments.

1) If a firewall is blocking a port that a program is listening for, it means some ports are may not be listed by the netstat command? Then, is there any other command I can use to list all open ports, regardless of possible firewall deny rules?


Actually netstat shows you what programs are listening regardless of firewall open/closed status. It will show you, for example, that sshd is listening on port 22 even if the firewall is blocking it, and so sshd cannot be reached. To test the actual status of ports as seen from outside the firewall you use a program like nmap, a port scanning tool (often used by those trying to find a way into your system). 
> 

2) For example: if I allow in the firewall the following IP range:

192.0.0.0/8

It means that it will permit connections from 192.1.1.1 to 192.254.254.254 ?


Yes. Well, from 192.0.0.0 to 192.255.255.255 but as 0 and 255 are usually used for special or broadcast purposes you usually exclude them. But also note that while 192.168.0.0/16 is designated as a private (local) address range, 192.0.0.0/8 would contain valid public addresses.

---

### Post by wojox on 2009-12-20
> **thebrotherofasis said:**
> Thank you very much for this tutorial... I was acutally googling for this topic, and it seems like a nice how to.

You mentioned  but I suppose it works for a LAMP server too?

Sure, I've got LAMP running on my Karmic server and everything worked ok. It's geared more for setting up port forwarding and dyndns. Just found that two days ago and configured everything like was posted. Now have a free domain name.

---

