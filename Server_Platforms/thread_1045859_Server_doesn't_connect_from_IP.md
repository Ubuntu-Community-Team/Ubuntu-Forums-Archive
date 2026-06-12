---
title: "Server doesn't connect from IP"
date: 2009-01-20
forum: Server Platforms
---

### Post by honkthrast on 2009-01-20
Hey there, I'm having an issue with connections straight to the IP to a computer I have here at my home.

Internet IP is redundant, but to differentiate between the one that the router gives me and the one my ISP gives me, I'm going to call it Internet IP, and the router IP DHCP IP.

When I connect via the DHCP IP(192.xxx.xxx.xxx), I can pull up everything except gallery2, but I think that's a problem with my gallery2 installation.  When I connect via the Internet IP (70.etc), I can't even get my Index.html to load.  I have port 80 forwarded on my netgear router to that PC, I checked and made sure that the static DHCP IP is the same, and it is.  My ISP opted to give me a new IP (I have a dynamic IP address), which I'm thinking is why this has all happened.

I am connecting to the new IP that they gave me.

The address, I typed in, looks like this:
[http://70.xxx.xxx.xxx/index.html](http://70.xxx.xxx.xxx/index.html)
^ there are actually numbers there, I just imagine posting an IP on the internet is not good practice.

I can still connect to webmin, and when I use the DHCP IP
[http://192.168.1.2/index.html](http://192.168.1.2/index.html), it works.

I tried searching, and the only other problem was a firewall issue, and I'm fairly certain I haven't installed any firewalls since yesterday when it was working.

```

user@servername:~$ sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

It's probably not relevant, but localhost never worked on the server.  I installed the base server, LAMP, webmin, gallery2, and blosxom.  I can't think of any other relevant information, but please ask if I can help with any more info.

Thanks for the help,
Henry

---

### Post by blackened on 2009-01-20
> **honkthrast said:**
> I'm going to call it Internet IP, and the router IP DHCP IP...

These are popularly referred to as external and internal addresses, respectively.

From the way you've explained the situation it sounds like the server was never accessible using the external IP.

This sounds like a NAT problem. Double-check that the port is properly forwarded.

---

### Post by honkthrast on 2009-01-21
Wow, it fixed itself.  I never had a chance to try your recommendations, but sitting here all night and all day it fixed itself.  Haha, I haven't the faintest idea what happened.  Thank you for your help.

---

### Post by honkthrast on 2009-01-21
Ah, the same problem has returned, I can still connect to my web pages via the internal IP 192.168.1.2, but the external IP does not work from my computer, nor others. 

Here's what I've verified:
My router is forwarding port 80 to the 192.168.1.2.
The internal IP of my computer is 192.168.1.2. 
PuTTY returns connection refused if I try to connect to it from the direct IP, but when I use 192.168.1.2, it works fine.
I've double checked my external IP and it has not changed since yesterday when things started becoming messed up.

Earlier today I was able to perform everything from the external IP, but it seems to have broken itself since.  I tried rebooting with no luck.

---

### Post by honkthrast on 2009-01-22
Would this question be better in the beginner's area?

---

### Post by Iowan on 2009-01-22
This forum seems quite appropriate for your problem.
I can understand why the local address would be accessible - and why the external address might not be accessible from inside the network.  When you say:> but the external IP does not work from my computer, nor others.  are the machines inside or outside the network?

---

### Post by honkthrast on 2009-01-23
The machine I'm using to connect is within the network, but I've had a few people try to connect from the outside, and that doesn't work either.  (Plus, I had no problems connecting from the inside with the external IP.)  If I don't figure it out soon, I'll probably just have to reinstall again.  I just hope this isn't a recurring problem for me.

---

### Post by Iowan on 2009-01-23
There's another similar thread around here  - different forum. Keep an eye on [this]("http://ubuntuforums.org/showthread.php?p=6604089") one.

---

### Post by blackened on 2009-01-23
You might think about setting up a redirection service for port 80 if your isp blocks it (which sounds like what is going on. I think a few of the free dynamic dns hosts offer this service, the main one being no-ip.com.

Have you tried running your webserver on a non-standard port? First verify that the new port works on the internal IP, then change your port forwards and try to connect connect from the outside using the an explicit port number.

---

### Post by perks on 2009-01-28
> **blackened said:**
> You might think about setting up a redirection service for port 80 if your isp blocks it (which sounds like what is going on. I think a few of the free dynamic dns hosts offer this service, the main one being no-ip.com.

Have you tried running your webserver on a non-standard port? First verify that the new port works on the internal IP, then change your port forwards and try to connect connect from the outside using the an explicit port number.

My ISP blocks port 80. I've tried running my server using port 78 and have it forwarded in my router's config. I also changed the port in ports.conf and restarted Apache. However, when I try to access my site from [http://perks.isa-geek.com:78](http://perks.isa-geek.com:78) or [http://192.168.1.100:78](http://192.168.1.100:78), I get a 404 error. However when I don't specify a port, I get the "It Works!" page. Any help is much appreciated.

---

### Post by cariboo on 2009-01-28
Just to make absolutely sure that your isp isn't blocking anything check [canyouseeme]("http://www.canyouseeme.org/").

Jim

---

