---
title: "I've confused myself about network/interfaces!!!"
date: 2011-01-10
forum: Server Platforms
---

### Post by pstrbrc on 2011-01-10
OK, I'm resetting up my server after having packed it up a year ago in a move. It was working then, so either I knew what I was doing, or a blind pig found an acorn. 
But then was then and now is now. I went ahead and installed 10.04, with an Xfc gui. Clearly had internet access.  My IP has given me a fixed ip, and I have set up my router to work. (I'm writing this on my laptop through the same router.) I have set my router (Belkin) with a virtual server, inbound set to port 80, with a private (lan) address set to that port. But now I'm stumped. I need to set my network/interfaces values, and here I am:
auto eth0
iface eth0 inet static
address (this is the lan address I attached to port 80?)
netmask 255.255.255.0 (Is this a generic default?)
network (since it's a Belkin, this would be 192.168.2.0, right?)
broadcast 192.168.2.255 (Is this a generic default?)
gateway (This would be the router's lan address, right? 192.168.2.1?)

When I set it this way, I can ping the server from my laptop, but when I do a 
> sudo apt-get update
from terminal on the server, I get "unable to connect to..." messages for all repositories. What'd I do wrong?

---

### Post by stlsaint on 2011-01-10
A few simply adjustments to see where your at:

1. Make sure that all your config settings underneath the 
eth0 inet static line is indented as so:

```

iface eth0 inet static
    address (this is the lan address I attached to port 80?)
    netmask 255.255.255.0 (Is this a generic default?)
    network 192.168.2.0, 
    broadcast 192.168.2.255 (Is this a generic default?)
    gateway 192.168.2.1

```

2. Did you restart the network on server?
```

/etc/init.d/networking restart

``` (or you could just use service commands here instead of /etc/init.d of course)

3. I know it may sound silly but try a ping from the server to google: #maybe the server your using for update is having issue
```
ping -c 4 www.google.com
```

4.Set the address in your /etc/interfaces to another static ip within your network. NOT the address you gave to the virtual server for port 80. #Testing purposes.

5. Show the contents of your /etc/resolv.conf
```
 cat /etc/resolvl.conf
```

---

### Post by pstrbrc on 2011-01-10
Golly. I knew it had tyo be something stupid. 
](*,)](*,) (note to self) "remember to indent!"
thanks for the help!

---

### Post by Ed_Ziffel on 2011-01-10
netmask 255.255.255.0 (Is this a generic default?)
A netmask hides the number of bits in the position of the address that it is given in.  Ip addresses are designated in blocks blah blah long story short:  192.168.xxx.yyy is reserved for private networks.  Your belikin default is 192.168.2.1 for the router itself.  Therefore to be on the same network your devices should be configured to 192.168.2.abc with the exception of a couple of reserved numbers i.e. 001 (your routers address) and 255, which I beleive is the listening address. 255.255.255.0 effectively hides all but the last 255 bits in the ip so that the bits in the last postion are seen as ips on your network more or less.  

As a practicle matter you can change your default on your router to what ever you want as long as you make the changes to the rest of the network.

---

