---
title: "Correct config of /etc/hosts"
date: 2009-03-29
forum: Server Platforms
---

### Post by R.Bucky on 2009-03-29
I am sure that this topic has been beat to death. It still seems a bit unclear to me. Call it self-doubt...

I have had a variety of minor issues on my Ubuntu Server 8.04. For instance, I cannot view CMS installations on my server from within the network because they are coded to have my domain, [http://buckycomputing.net](http://buckycomputing.net), instead of allowing my internal ip or localhost. I have a true static ip from my ISP. However, sometimes I am unable to view my website using my domain name, but instead have to use my IP. Anyways, here is my /etc/hosts file. 

Can someone suggest improvements? Yes, I have substituted my real hostname for "hostname."

127.0.0.1	localhost
127.0.1.1	hostname buckycomputing.net

I would appreciate ANY suggestions.

~Mark

---

### Post by BkkBonanza on 2009-03-29
Normally the /etc/hosts file has higher priority than DNS lookups. So if a name is entered in the file then that address will be used instead of DNS. The format is,

ip name [name]...

Now, a couple observations about your file. You have an address for a machine called "hostname". I suspect that's an error as people don't normally name their machines/sites "hostname". But it probably doesn't matter. More critical is you have an entry for buckycomputing.net pointing to address 127.0.1.1 - is that a valid address? Not usually - if the site is on your own machine then it should be 127.0.0.1 same as localhost. If it's on another machine in your LAN then it should be the ip of that machine, eg. 192.168.0.2 - but 127.0.1.1 is likely incorrect.

When some program on your machine wants to connect to buckycomputing.net it will check this file and substitute 127.0.1.1 and probably have trouble connecting to the machine.

BTW some people use /etc/hosts as a way to re-direct sites they don't want to connect to. Like if you are sick of ads from some site then you enter it there pointing to your own machine and that stops the site form being connected to.

---

### Post by R.Bucky on 2009-03-29
The "hostname" is the name of my server box. The 127.0.1.1 address was default with my hostname when I installed. It would make sense to place my domain name with the localhost instead of where it currently resides. When I view my web site from another box on my network, I use my internal ip of 10.1.10.XXX. It seems to work out, except with certain CMS's like Concrete5 and wordpress. I have already routed 24.18.97.111 (buckycomputing.net) to my server box in the router config. So, another entry on my /etc/hosts such as below seems like it would be replicating what is already in the configuration.

10.1.10.XXX     buckycomputing.net

Can anyone posts their /etc/hosts or 'modified' versions?

---

### Post by capscrew on 2009-03-29
All of the 127.0.0.0 range is a virtual interface.  It is only addressed by the local host ie: the machine talking to itself.  The use of 127.0.1.1  seems to very misunderstood.   You can read the reason for its existence [**here**]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-net-dns").

If you wish to communicate to another host locally you need to use some other IP address range.  The /etc/hosts file only maps IP addresses to hostnames.

If you are only talking to yourself then any IP address in the 127.0.0.0/8 range will work.  Try pinging 127.0.1.254 and see what you get.

> The "hostname" is the name of my server box. The 127.0.1.1 address was default with my hostname when I installed. It would make sense to place my domain name with the localhost instead of where it currently resides

This is incorrect.  Since your hostname is for other hosts to use, you would be better served by mapping the hostname to the Ethernet interface (eth0 or some such).

The name the "localhoast" is what your associate with an 127.0.0.0/8 address.  Usually 127.0.0.1.

> When I view my web site from another box on my network, I use my internal ip of 10.1.10.XXX.

This means you are NATing the inside private address to the outside public address.

>  It seems to work out, except with certain CMS's like Concrete5 and wordpress. I have already routed 24.18.97.111 (buckycomputing.net) to my server box in the router config. So, another entry on my /etc/hosts such as below seems like it would be replicating what is already in the configuration.

There are 2 areas of DNS.  The public DNS is for the mapping of buckycomputing.net to the 24.18.97.111 IP address allong with any FQDN entries you have. The /etc/hosts file is to map local (LAN) addresses to hostnames only.  

You need to map the 10.1.10.xxx address to the hostname of the machine you want to talk to by name.   By this I mean this should be in the host you are at. Here is an example:
```

# /etc/hosts file
# loopback
127.0.0.1 localhost
127.0.1.1 localhost.buckycomputing.net
# Ethernet
10.1.10.xxx <hostname> <hostname>.buckycomputing.net

```

Note that we are mapping both the host name and the FQDN to the 10.1.10.xxx address.

Don't confuse DNS with routing.  DNS is only for name services, with local and public spheres.

---

### Post by windependence on 2009-03-30
The reason you can't view your CMS and other websites from inside your NATed network is because your router, like most SOHO routers does not do NAT reflection. 

What's really happening is that your router, when doing a DNS lookup on your domain name, resolves it to your outside static IP as it should. Your outside IP is not inside your network, so the router does not know where to send the request, and you get a timeout. You would think that the router would simply send the packet out to the internet and then it would come back in, but that is not the way routing works. 

So, to find your server from the inside, you put an entry into the /etc/hosts file on your client machine to tell it what IP to resolve the domain name to. Of course, you can always access the server using the IP of the server, which requires no DNS lookup.

Hope this makes it a bit clearer.

-Tim

---

### Post by R.Bucky on 2009-03-31
Finally, an answer to my query! I have been irritated by this one for some time. Thank you for the explanation Tim. This thread seems to clear things up quite a bit. Thanks all.

Mark

---

### Post by BkkBonanza on 2009-03-31
But your original post showed your name (buckycomputing.net) in your /etc/hosts file. So how could lack of reflection have caused your problem. You should have been getting your local ip all along and it's probably why no one thought of mentioning the router relection issue.

---

