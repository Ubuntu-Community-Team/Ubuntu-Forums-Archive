---
title: "Make my virtual network visible as a domain?"
date: 2009-12-18
forum: Server Platforms
---

### Post by itzpapalotl on 2009-12-18
Okay folks. Here's the skinny. I don't know how to ask the question exactly, so I am going to try to describe the results I need and hopefully someone out there can help get there!

I have a big ol' host server running Server 9.04 and VMware server2. It only acts as a host machine. (also as NS1 which isn't working I guess) The host machine's actual network card in to the greater world and configured with a static IP address provided by the ISP.

Now, living on the host machine are 7 virtual machines, all running on bridged network 192.168.187.x They each do different things, but each also needs to be able to be connected to in multiple ways, meaning I can not just use port forwarding. 

So.. I thought the way to do this was to install bind9 on the host machine and then make a local zone and some PTR files for the various virtual machines, which I am pretty sure I did right.

#########[/etc/bind/named.conf.local]

zone "thisdomain.net" {
type master;
file "/etc/bind/zones/thisdomain.net.db";
};

zone "187.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.187.168.192.in-addr.arpa";
};


########[/etc/bind/zones/thisdomain.net.db]

thisdomain.net. IN SOA ns1.thisdomain.net. admin.thisdomain.net. (
// Do not modify the following lines!
2009121801
28800
3600
604800
38400
)

// NS and MX records here
thisdomain.net. IN NS ns1.thisdomain.net.
thisdomain.net. IN MX 10 mail.thisdomain.net.
// And the local machines (god I hope this works)
satyr   IN      A       192.168.187.10
hermes  IN      A       192.168.187.20
janus   IN      A       192.168.187.30
hades   IN      A       192.168.187.40

#######[/etc/bind/zones/rev.187.168.192.in-addr.arpa]

@ IN    SOA ns1.thisdomain.net. admin.thisdomain.net. (
2009121802;
28800;
604800;
604800;
86400;
)

IN      NS ns1.thisdomain.net
1 IN    PTR thisdomain.net

#######

So okay.. It ain't working... Am I on the right track? How do I translate my local virtual network across the line to the greater internet?

---

### Post by Cheesemill on 2009-12-18
> **itzpapalotl said:**
> The host machine's actual network card in to the greater world and configured with a static IP address provided by the ISP.

Now, living on the host machine are 7 virtual machines, all running on bridged network 192.168.187.x

This doesn't make sense, in bridged mode the host and guest IP's will be in the same network, yet you say your host IP is assigned by your ISP in which case it wont be a private network address (192.x.x.x). What is the IP of your host?

Also if you only have one external IP you will have to use NAT and port forwarding of some kind, what exactly are you trying to achieve?

---

### Post by BkkBonanza on 2009-12-19
From what you say you only have one IP on the internet side. Under normal conditions that prevents you from having multiple servers on the same port - after all there is only one port 80 on any given IP.

Running bind here does nothing for you that you couldn't do by just using DNS services of your registrar or any other DNS provider. It doesn't inherently give you more public IPs - those you can only get from your ISP. Once you have some then you can configure them to route to different guest virtual machines on your system.

It is possible that you could use a reverse proxy on your host machine that will use domain names in a virtual host config that would then route to various guest VMs based on host name. I haven't done that but it should be possible. If I was going to do it I would use a light weight server that is known to be a good virtual host proxy - like Nginx. You can config virtual host names that it can proxy to different IPs internally. 

You wouldn't use bridged mode for the guest VMs though. You would want them to share a network with the host but not with the ISP. In VMware I don't know what they call that but in VirtualBox it's called host-only mode. The host machine and guest VMs all exist on a virtual LAN inside the one machine. On the host you would configure the public interface to the ISP and a bridge route so the host acts as a router for the virtual LAN.
Internet requests hit the public IP where Nginx is listening - nginx matches the domain name to it's table of virtual hosts and proxies it to a virtual IP on a guest. That would do it.

Of course, as far as DNS goes all your domains hosted would be pointed to your one single IP.

---

### Post by BkkBonanza on 2009-12-19
I just thought to add a bit more detail. In host-only mode VirtualBox will create routing automatically as below - probably VMWare has a similar option.

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.56.0    *               255.255.255.0   U     0      0        0 vboxnet0
default         router          0.0.0.0         UG    0      0        0 eth0

```

Notice here that 192.168.0.* is my real LAN but for you this would be the route to your ISP. And 192.168.56.* is the virtual LAN for my internal guest VMs.

Then in Nginx you would add a server section for each server on your virtual LAN as follows,
```

server {
    server_name: myfatdomain.com;
    location / { proxy_pass http://192.168.56.1; }
}
```
repeat as needed with suitable names and internal IPs. This can also do load balancing for the same names but look at docs to see extra section needed.

Nginx is nice because it's very light in memory/cpu usage and scales very well for heavy load. In the case of VirtualBox it does all the virtual DHCP for the virtual LAN so no extra configs needed there.

---

### Post by itzpapalotl on 2009-12-19
Okay so I server one public IP address eh? Huh. Weird. I thought for sure you could translate a LAN in to a full on domain with each machine having an FQDN, and those fqdns pointing past the single connection... I guess I am way off base here.

I'll try host only mode see if that gets me anywhere..
Thanks all!

Cheesemill, what I am trying to achieve is essentially twice as many hosts as public routable IP addresses. To clarify the network setup (if it halps any) the host machine is connected physically via a LAN card to (call it) 555.55.233.100. A Public IP address. Static. It runs a virtual network to which it is connected also at 192.168.187.1 as the gateway I think, certainly as the NAT. I have exactly no problems with the LAN side of things. It all works just peachy as long as I am sitting inside the gateway. What I want to do is kinda tell the world that if you want to deal with cosmicumbrella.net you should first come on over 555.55.233.100 and then if you want the hermes server hop through to 192.168.1.20 etc. I thought that was what DNS was all about, but I may be just plain wrong.

---

### Post by BkkBonanza on 2009-12-19
Yes, your understanding of DNS is a bit incomplete.
Here's how it works...

Someone puts an URL into their browser.
The browser checks (it's cache and) the local hosts file and finds the FQDN isn't present.
So it sends a DNS request to it's configured DNS server.
Often this will be a local router that checks a cache or passes it on.
Ultimately (after a few more steps involving root servers and such) it gets to whatever DNS server you specify via your domain registrar.
Your DNS server (wherever that may be) returns an IP address.
The browser attempts to open a connection to that IP address.
When it sends out the SYN packet to do that, various routers on the internet will get it to your ISP, which relays it to your server at the IP given.

Now at this point you get the connection request. You can accept it or not. But you can't change the IP at this point. There's just no way to do that because your private IP addresses are not visible on the public internet. They can't be because tons of other networks around the world also use private IPs that would conflict. Private IPs are unique ONLY within your network, so the only possible IP any client can use for you is the one(s) allocated by your ISP for your service. Your DNS server, whether on your own or some other provider's server must return only public IPs.

So what you do have control over is how you deal with the connetion after it gets to your server. This is where the reverse proxy comes in. Because the HTTP protocol indicates that a FQDN is passed along in the http request you know what domain ultimately the browser wants even though many may be shared by the same IP. This is usually called "virtual hosting".

Your proxy looks at the FQDN and decides where to pass the request within your area of control, on your virtual or real network, using private addresses. The final receiver accepts the connection and returns data as expected. And likewise the return data has to use a public IP to have any hope of getting back to the user's browser.

Note that if some client sent out a packet containing a private IP address (these are  certain standardized ranges) the packet would not be passed on by their gateway router, or if routed due to misconfiguration it would surely be dropped by the upstream router (ISP). A "host not reachable" error could be returned, or it may be dropped. It certainly wouldn't ever make it out on to the public internet where it has to pass to reach your server. Hence, you can not use anything but public IPs for public DNS. 

I hope that clarifies some things. You can do what you need using a reverse proxy but not using DNS servers. Which is just as well because running a reverse proxy (like Nginx) is way less work than running DNS anyway.

---

### Post by itzpapalotl on 2009-12-19
OKAY!!!
BkkBonaza, Thank you so much. I think I finally get the process. Basically in the end if I DID set this all up the way I had planned. Any computer attempting to connect to the site would in fact be querying its own LAN at best and nothing at worst. Got it.

I maybe will try to use this reverse proxy system you explained. Or maybe I'll just suck it up and combine my servers to fit in the 5 statics i do have..

Thanks so much. I gotta admit DNS and bind9 are kinda baffling, but a little less so now. Thank you.

---

