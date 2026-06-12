---
title: "Port 80 outbound slow"
date: 2012-01-06
forum: Server Platforms
---

### Post by C23 on 2012-01-06
Hi, I recently picked up a dedicated server and had Ubuntu 11.10 Server installed freshly. When connecting through port 80 on things like wget, the server stalls for some time on resolving, but eventually goes through. The server is used to host a Minecraft multiplayer server, and the game connects to its own website to tell if a player has purchased the game or not, the stalling through port 80 can be seen there also, taking 3-5 seconds to resolve.

I'm not sure what to call this, if there is anything I can do, or if I should contact the data center techs about it. Port 80 inbound is fine, I have a web server running and it's quick and snappy. I decided to post here about it because I'm completely unsure about this issue.

Thanks a ton for any replies.

---

### Post by volkswagner on 2012-01-07
What do you have in /etc/resolv.conf?

You can try different name servers here.

You can test the resolve time like:

```
time host google.com
```

This is the results I got.
```
real	0m1.240s
user	0m0.020s
sys	0m0.040s

```

---

### Post by C23 on 2012-01-07
This is /etc/resolv.conf
```
nameserver 192.168.1.100
nameserver 69.30.192.15
nameserver 69.30.192.14

```
time host google.com:
```
real    0m4.582s
user    0m0.008s
sys     0m0.012s
```

---

### Post by collisionystm on 2012-01-07
> **C23 said:**
> Hi, I recently picked up a dedicated server and had Ubuntu 11.10 Server installed freshly. When connecting through port 80 on things like wget, the server stalls for some time on resolving, but eventually goes through. The server is used to host a Minecraft multiplayer server, and the game connects to its own website to tell if a player has purchased the game or not, the stalling through port 80 can be seen there also, taking 3-5 seconds to resolve.

I'm not sure what to call this, if there is anything I can do, or if I should contact the data center techs about it. Port 80 inbound is fine, I have a web server running and it's quick and snappy. I decided to post here about it because I'm completely unsure about this issue.

Thanks a ton for any replies.

A few things to look at that would cause a delay.

#1. Check your route on the server. The default route should be the local IP of your router.
type, route , to check this.
#2. As mentioned, your resolv.conf should contain a valid DNS server. Generally it is your local router DNS in a home network. However you can also use 8.8.8.8 which is the google public DNS. A properly configured network route should not have any delays in a DNS response because DNS is a rather simple protocol.
#4. How about your firewall? Have you changed anything on there? If the firewall is enabled, be sure that you allowed input from your loop back. Forwarding and output should be set to INPUT allowed also. There is no reason to filter either of these unless you are running a high security network.
Check your firewall rules with
sudo iptables-save

it will post the output on the screen.


If you could give a brief description of your network layout, it would help A LOT.

EDIT:

Why have you included your external DNS in your server?
nameserver 69.30.192.15 nameserver 69.30.192.14

There is no point in doing this. If your router providing the dns access fails, you will not be able to reach these DNS servers anyways.

Also be sure the time on your server is correct. The best practice is to install ntp and enable it.

---

### Post by C23 on 2012-01-07
@collisionystm I'm renting this server, so I don't really know details on the network. There's no firewall, nothing in iptables. The system time is also correct. Looks like I should take it up with the host.

If nameserver 69.30.192.15 nameserver 69.30.192.14 is removed from resolv.conf the server can't connect to anything, so this looks like an error on their part.

Edit: yeah appears to be something in their network, if I set nameserver 8.8.8.8 I get results like:
```
real    0m0.093s
user    0m0.008s
sys     0m0.004s
```

---

### Post by collisionystm on 2012-01-07
> **C23 said:**
> @collisionystm I'm renting this server, so I don't really know details on the network. There's no firewall, nothing in iptables. The system time is also correct. Looks like I should take it up with the host.

If nameserver 69.30.192.15 nameserver 69.30.192.14 is removed from resolv.conf the server can't connect to anything, so this looks like an error on their part.

Edit: yeah appears to be something in their network, if I set nameserver 8.8.8.8 I get results like:
```
real    0m0.093s
user    0m0.008s
sys     0m0.004s
```

Fast response time because you are pointing to google.com with 8.8.8.8

Every provider will limit your outbound bandwidth because they do not have unlimited resources. You will need to special request a larger allocation and in turn, I am sure, have to pay a larger sum.

---

### Post by collisionystm on 2012-01-07
If your hosting a server, you may run into a spot where you need to provide your own name entries for games/programs.
I suggest you install bind9 and just put 8.8.8.8 in as a forwarder. Then point your resolv.conf to 127.0.0.1

---

### Post by C23 on 2012-01-07
> **collisionystm said:**
> Fast response time because you are pointing to google.com with 8.8.8.8

Every provider will limit your outbound bandwidth because they do not have unlimited resources. You will need to special request a larger allocation and in turn, I am sure, have to pay a larger sum.

Ah, well I pay for 10TB of monthly bandwidth and surely haven't used all that up. Setting the nameserver to 8.8.8.8 sped up resolving as a whole. Do providers track bandwidth usage through them? If so I'm guessing it's bad to change it.

---

### Post by collisionystm on 2012-01-07
> **C23 said:**
> Ah, well I pay for 10TB of monthly bandwidth and surely haven't used all that up. Setting the nameserver to 8.8.8.8 sped up resolving as a whole. Do providers track bandwidth usage through them? If so I'm guessing it's bad to change it.

No they will check bandwidth by the Mac address of your servers nic card

---

### Post by d3v1150m471c on 2012-01-07
I recommend using djbdns/dnscache.

---

### Post by SeijiSensei on 2012-01-09
If you're renting a virtual machine, rather than a physical one, you can experience delays if the host machine is overloaded.  Even with an excellent provider like [Linode]("http://www.linode.com/"), I'll still get delays when I use SSH to connect to the server since the host may need to swap some parts of the virtual images of the machines running on it.

Will your provider tell you how many VMs are being hosted on your server with you?  If not, get a new provider.  At $20/month, Linode isn't the cheapest, but it has a lot of satisfied users including me.

I don't see these delays as often when running services like SMTP where my receiving server is constantly handling mail.  It's more common when services have to start up.  

> The server is used to host a Minecraft multiplayer server, and the game connects to its own website to tell if a player has purchased the game or not, the stalling through port 80 can be seen there also, taking 3-5 seconds to resolve.

If this is only case of delay, it could just be slow response time from the account confirmation server.  Is that yours, too, or just a service you use that is provided by others?

---

