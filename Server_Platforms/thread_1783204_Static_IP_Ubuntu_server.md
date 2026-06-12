---
title: "Static IP Ubuntu server"
date: 2011-06-15
forum: Server Platforms
---

### Post by brent1975 on 2011-06-15
Hello, I am fairly new to the open source community so excuse the novice question.

I have a client that has just started a small business and would like to have his own web server to host a simple site.

The client has a Time Warner business Internet account with 5 static IP's and wants to dedicate one of those IP's for the server. The client will not have a router between the server and gateway so basically an open internet connection. I will enable 22, and 80 via ufw later. I will be doing all modifications via at the terminal. Here is just an example of what I have.

I know these are lan configs. but if this is what the ISP has given me what would the output file look like in the network/interfaces?
setting for static
IP 192.168.1.101
subnet 255.255.255.0
gateway 192.168.1.1

I also know that I would open the resolv.conf file and change the DNS to what the ISP has given me.

---

### Post by arrrghhh on 2011-06-15
Here's my /etc/network/interfaces file:

```
iface eth0 inet static
        address 192.168.0.99
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1
```

The IP of the box is .99, and the IP of my gateway (router) is .1.  What you have looks good, just fill in the blanks for your setup.

---

### Post by brent1975 on 2011-06-15
> **arrrghhh said:**
> Here's my /etc/network/interfaces file:

```
iface eth0 inet static
        address 192.168.0.99
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1
```The IP of the box is .99, and the IP of my gateway (router) is .1.  What you have looks good, just fill in the blanks for your setup.


So I would add broadcast and network  Just so I know.

If I had an IP of 69.32.2.16 broadcast would be  broadcast 69.32.0.255

and network 69.32.0.0 ?

---

### Post by arrrghhh on 2011-06-15
> **brent1975 said:**
> So I would add broadcast and network  Just so I know.

If I had an IP of 69.32.2.16 broadcast would be  broadcast 69.32.0.255

and network 69.32.0.0 ?

Erm... probably not.  I'd ask your provider...  I can't say definitively if that is correct or not, since my setup is on a LAN, and I'm the admin of all the network gear ;).

---

### Post by collisionystm on 2011-06-15
Broadcast address calculator

[http://www.remotemonitoringsystems.ca/broadcast.php](http://www.remotemonitoringsystems.ca/broadcast.php)

---

### Post by arrrghhh on 2011-06-15
> **collisionystm said:**
> Broadcast address calculator

[http://www.remotemonitoringsystems.ca/broadcast.php](http://www.remotemonitoringsystems.ca/broadcast.php)

Seems cool, but I couldn't get it to work for the life of me...

---

### Post by brent1975 on 2011-06-15
Okay, so I am now at the site and I am not so clear how to set this static box here is the config info that I received from time warner.
Ip 173.197.3.100
Subnet 255.255.255.248
Gateway 173.197.3.97

Any clues what the config file should look like? This is a direct connection to the modem.

---

### Post by arrrghhh on 2011-06-15
> **brent1975 said:**
> Okay, so I am now at the site and I am not so clear how to set this static box here is the config info that I received from time warner.
Ip 173.197.3.100
Subnet 255.255.255.248
Gateway 173.197.3.97

Any clues what the config file should look like? This is a direct connection to the modem.

I plugged in the numbers myself, and it worked this time.  Probably my work laptop acting up again...

Here's the exact config you'll need:

```
iface eth0 inet static
        address 173.197.3.100
        netmask 255.255.255.248
        broadcast 173.197.3.103
        network 173.197.3.96
        gateway 173.197.3.97
```Basically the netmask determines the size of the block of IPs you own, and that in turn determines the broadcast (highest) and network (lowest) address in the range.

Edit - this 'script' also assumes eth0 will be the interface you're using.

---

### Post by BkkBonanza on 2011-06-16
> **brent1975 said:**
> So I would add broadcast and network  Just so I know.

If I had an IP of 69.32.2.16 broadcast would be  broadcast 69.32.0.255

and network 69.32.0.0 ?

Your broadcast address is usually the highest address in the network. So for 69.32.0.0 it would be 69.32.255.255

(From wikipedia:
The broadcast address for an IPv4 host can be obtained by performing a bitwise logical OR operation between the bit complement of the subnet mask and the host's IP address.

Example: to broadcast a packet to an entire IPv4 subnet using the private IP address space 100.16.0.0/12, which has the subnet mask 255.240.0.0, the broadcast address is: 100.16.0.0 | 0.15.255.255 = 100.31.255.255.
)

I think if you leave out the broadcast setting in the interfaces file it will assume the default so it likely makes sense to add it manually only if you have something abnormal.

---

### Post by capscrew on 2011-06-16
> **brent1975 said:**
> Okay, so I am now at the site and I am not so clear how to set this static box here is the config info that I received from time warner.
Ip 173.197.3.100
Subnet 255.255.255.248
Gateway 173.197.3.97

Any clues what the config file should look like? This is a direct connection to the modem.

This subnet mask (255.255.255.248 ) sets a /29 network with 8 hosts (6 *usable* hosts plus a network ID and broadcast address).  To fit the host IP of 173.197.3.100 in with a gateway of 73.197.3.97 you would need to have the following

```

address   179.197.3.100   # Your host 
netmask   255.255.255.248
network   179.197.3.96    # NetID
broadcast 179.197.3.103   # This is the last number 8 host range
gateway   179.197.3.97

```

---

### Post by brent1975 on 2011-06-16
Thanks everyone for the assistance, makes much more sense now.

---

