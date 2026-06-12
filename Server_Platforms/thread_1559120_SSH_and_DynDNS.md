---
title: "SSH and DynDNS"
date: 2010-08-23
forum: Server Platforms
---

### Post by breadoo on 2010-08-23
I have an Ubuntu server (10.04) tied to DynDNS (assume that server's address is "bobo.dyndns-ip.com").

Server information:
hostname: bobo.dyndns-ip.com
domainname: (none)

On a client computer, I can connect that server's Web server via [http://bobo.dyndns-ip.com](http://bobo.dyndns-ip.com). 
I can also ping bobo.dyndns-ip.com.
I can also SSH on the same LAN via "ssh me@bobo".

Problem:
However, I cannot ssh via "ssh [email]me@bobo.dyndns-ip.com[/email]". When I try to do that, I get "Permission denied" (yet ssh me@bobo works perfectly!)

Does anyone know why this is so, and how to fix this? Is more info on the problem needed?

---

### Post by brad_c6 on 2010-08-23
(I am no expert of DynDNS, so I assume it updates a DNS name "bobo.dyndns-ip.com, therefore registering a new ip address.)


If with default settings SSH uses public keys, which means that when you connect at a certain time

bobo.dyndns-ip.com ----Points to----> 152.21.145.98

Your computer notices this dns record (bobo.dyndns-ip.com") and puts it together for down the road that if this server has this IP use this key to connect. After time your server will change IP and BOOM the record is broken. So now your computer thinks something fishy is going on in the connection (ie. hacker attempting to "sniff" your password)

Quick Fix(but annoying) is to delete the no longer good entry in(or delete the file if you have no other ssh servers to connect to)

```
/home/<yourusernamehere>/.ssh/knownhosts
```

The better fix would be to setup OpenVPN with certificate authentication, as to not allow attackers to even get a prompt or anything.

(So you connect to your VPN and then ssh locally to the computer, therefore your ssh ip is always the same. Even though the outside is not)

---

### Post by Ryan Dwyer on 2010-08-23
You cannot use the external hostname (bobo.dyndns-ip.com) from inside the network. It will resolve to your external address which will stop at your router.

If you want to use that hostname internally then you must either configure it in /etc/hosts or set up a private DNS server to resolve the hostname to the private address.

---

### Post by cdenley on 2010-08-23
> **Ryan Dwyer said:**
> You cannot use the external hostname (bobo.dyndns-ip.com) from inside the network. It will resolve to your external address which will stop at your router.

If you want to use that hostname internally then you must either configure it in /etc/hosts or set up a private DNS server to resolve the hostname to the private address.

That often is a problem with some routers, although some will work. It seems to work fine for his web server, and he seems to connect to a server but fails to authenticate. Perhaps their router is running an SSH server, and instead of using the port forward rule, the router's SSH server handles the connection.
```

host bobo.dyndns-ip.com
host bobo
nc -v -z -w 4 bobo.dyndns-ip.com 22
nc -v -z -w 4 bobo 22
nc -w 4 -q 1 bobo.dyndns-ip.com 22 < /dev/null
nc -w 4 -q 1 bobo 22 < /dev/null

```

---

### Post by TJet1.8 on 2010-08-23
Uhmm...ok guys...alot of interesting solutions without a real root cause analysis. :lolflag:

So if you are accessing your server via dyndns, you have to understand that communications are going out your router, hits dyndns, and then tries to come back from the internet into your router.

If you don't have ports opened in your router to allow the ssh port to come in...then ACCESS DENIED!!

What you need to do is port forward a TCP port from the internet into your server "through" your router.

Example
-------

Lets say you want to ssh into your server from the internet via some obscure TCP port(let's say port 55443).

Setup your router to Port Forward TCP port 55443 from the internet to your servers IP on port 22 for ssh.

Then you will ssh into your server like this:
ssh -p 55443 [email]me@bobo.dyndsn-ip.com[/email]

The -p tells ssh to communicate over port 55443.
When it hits your router, the router will then forward the port to your servers IP on port 22.

Every router is different, so I can't give you "exact" instructions on how to do this with your router.

I have this exact same set and it work perfectly!!

Good Luck
:popcorn:

---

### Post by BkkBonanza on 2010-08-24
As Ryan said, some routers won't correctly route their WAN IP back to the LAN. The simplest solution is just mapping that domain in the hosts file to use the private IP instead.

---

### Post by cdenley on 2010-08-24
As I already said, if the client gives "Permission denied", then it must be connecting to a SSH server. Considering that he is connecting to some SSH server, and he can access the web server using the same domain, I don't think the problem is a port forwarding one (so much for a "root cause analysis"). I think either you configured /etc/ssh/sshd_config to only allow LAN IP's, or you aren't actually connecting to the server you think you are. I still suggest posting the output for the commands I posted previously, as well as your sshd_config on the server.
```

grep '^[^#]' /etc/ssh/sshd_config

```

---

