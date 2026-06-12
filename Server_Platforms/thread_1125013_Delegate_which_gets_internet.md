---
title: "Delegate which gets internet?"
date: 2009-04-13
forum: Server Platforms
---

### Post by blindmist on 2009-04-13
I have 2 cards in my server. I have one that goes to my home LAN so i can have use of the gigabit cards and switch, and then I have a static dedicated line that goes to an ISP.

The problem is, sometimes I like to use my servers dedicated line to browse the internet via proxy on the address 192.168.1.29 because sometimes my house internet is slow because of family.

The problem I am having is that I had to replace the static dedicated card because lightning took the other one out. Before I replaced the card, I made the local LAN from static to DHCP so that the server could still access the internet through my homes internet. I like it to be able to download stuff with torrentflux. I have now changed it back to its static local ip.

Now I have the burnt card replaced and it wont stop going out my home's internet. I have even disabled that card in /etc/network/interfaces and left just the static dedicated line, but the server refuses to go out on the WWW on that ip now.

How do I delegate which card see's the outside world and which one stays locked up at home?

---

### Post by blindmist on 2009-04-14
I also just noticed that if I have both cards up, I can access the "apache" part of it because I can go to the website via [http://jslay.net](http://jslay.net) or [http://205.209.251.20](http://205.209.251.20) and I can even ssh to it as well on the outside ip. Now when I use the "external" ip 205.209...... for the proxy, it cannot load any pages. When I use the 192.... as the proxy, it goes out onto my homes internet. I check the ip and it gives me my homes ip, not the servers, which it used to.


hmmmm....

---

### Post by blindmist on 2009-04-14
I believe I figured it out, or it just started working that way

in my /etc/hosts file it looked like this

```

127.0.0.1       localhost.localdomain   localhost
205.209.251.20  sfhs.jslay.net
192.168.1.29    sfhs.jslay.net

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I noticed that the 192.168.1.29 had sfhs.jslay.net with it, I didn't think it should be that way so I took it out. Now it looks like so...

```

127.0.0.1       localhost.localdomain   localhost
205.209.251.20  sfhs.jslay.net
192.168.1.29

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```



Is this ok? Is this what fixed it? Does something need to be there?

---

### Post by BkkBonanza on 2009-04-14
Usually you can use the route command to establish what routing you need. 
Type, **route -n** to show your current routes. 
You can change the default gateway by removing the one current and adding a new one.
So for example if your current one shows like this,
default   192.168.0.10  
You may choose to use commands like, (read up on route command)
route add default gw 192.168.1.1
route del default gw 192.168.0.10

An easier way with less reading is to install Wicd (using Synaptics) because it is pretty good at handling multiple connections. You can set the interface you want in it's preferences and then tell it to connect using the wired connection. It will bring it up with suitable routes. It's made more for wireless but it does work with wired connections too.

Edit after reading new comment: I don't believe the /etc/hosts will have anything to do with what routing you use. But you shouldn't have two ips with same name so that is still good to fix.

---

### Post by blindmist on 2009-04-14
I believe I have setup the default gateway correctly now, but I am still having problems.

If I use the internal 192 ip for my proxy, I can access both jslay.net and 192.168.1.29 over port 80, but when I take the proxy away, and just go out on my home internet, I cannot access jslay.net, but I can still access 192...


The weird part is, before I went to bed last night, I could not access my server at all. I gave it a shot when I woke up this morning and my local address seems to be working fine, just nothing else.

In my hosts file, what should I name my 192 address?

Here are a few other files so maybe someone can see a flaw in them.

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#static dedicated line!!!!BURNT UP CARD! DO NOT USE!
#auto eth1
#iface eth1 inet static
#
#       address         205.209.251.20
#       netmask         255.255.255.0
#       network         205.209.251.0
#       broadcast       205.209.251.255
#       gateway         205.209.251.1

#static dedicated line
auto eth2
iface eth2 inet static

        address         205.209.251.20
        netmask         255.255.255.0
        #network        205.209.251.0
        #broadcast      205.209.251.255
        gateway         205.209.251.1

#static LAN line to house
auto eth3
iface eth3 inet static

        address         192.168.1.29
        netmask         255.255.255.0
        #network        192.168.1.0
        #broadcast      192.168.1.255
        gateway         192.168.1.1

```

/etc/hosts
```

127.0.0.1       localhost.localdomain   localhost
205.209.251.20  sfhs.jslay.net
192.168.1.29

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Also, I just now noticed that my /etc/resolv.conf has 1 name server, it being 192.168.1.1

I believe this is my problem, and how it got changed from what it was, I don't know.

I need to call my ISP to get the static DNS addresses for the static line.

EDIT:
Ok, I got the correct DNS ip's in there now and it appears to be working just fine. Only time will really tell.

---

