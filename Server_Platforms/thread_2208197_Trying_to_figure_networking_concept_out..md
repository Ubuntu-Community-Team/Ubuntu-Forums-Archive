---
title: "Trying to figure networking concept out."
date: 2014-02-26
forum: Server Platforms
---

### Post by bigsigh on 2014-02-26
Is this possible?
Is it routable?



[COLOR=#FF0000]------------------------------[/COLOR]>-- eth1 -- internal subnet -- dhcp from gateway -- eth0 
isp -- eth0 --> gateway[COLOR=#FF0000]------------------------ red is empty space for formating-------[/COLOR] Ubuntu server
[COLOR=#FF0000]------------------------------[/COLOR]>-- eth3 -- 2nd internal subnet ---- static ---------- eth1


Can a single Ubuntu server with two interfaces operate on two different internal subnets?

---

### Post by papibe on 2014-02-27
Hi bigsigh.

> **bigsigh said:**
> [COLOR=#FF0000]------------------------------[/COLOR]>-- eth1 -- internal subnet -- dhcp from gateway -- eth0 
isp -- eth0 --> gateway[COLOR=#FF0000]------------------------ red is empty space for formating-------[/COLOR] Ubuntu server
[COLOR=#FF0000]------------------------------[/COLOR]>-- eth3 -- 2nd internal subnet ---- static ---------- eth1
I'm afraid I don't understand your table. Could you provide more details or may be a diagram?
> **bigsigh said:**
> Can a single Ubuntu server with two interfaces operate on two different internal subnets?
Yes.
However, there are network layouts in which this is helpful and powerful, and others in which this would be a big NO NO.

Regards.

---

### Post by bigsigh on 2014-02-27
> **papibe said:**
> Hi bigsigh.

Yes.
However, there are network layouts in which this is helpful and powerful, and others in which this would be a big NO NO.

Regards.

Wonderful, I assume the routes would be written in ip route but I know little about this, my google foo has been weak, would you have any resources that you could point me towards so I could figure this out? Thank you.

---

### Post by papibe on 2014-02-27
I'd start reading this:
[LIST]
[*][askubuntu: ubuntu server as a router/gateway]("http://askubuntu.com/questions/331975/how-can-we-make-our-ubuntu-server-router-as-gateway-mode-to-router-mode").
[*][askubuntu: how to set up a linux server as a router]("http://askubuntu.com/questions/376717/how-to-set-up-a-linux-server-as-a-router").
[*][Ubuntu wiki: Ubuntu as a router]("https://help.ubuntu.com/community/Router").
[/LIST]
Regarding network layout, you usually want to do something like:
```
                                                 ____eth1--> subnetwork1
                                               /
Internet -> modem/router -> (eth0) UbuntuServer
                                               \
                                                 ----eth2--> subnetwork2
```
Hope it helps. Let us know if that helped, and if you have more questions.
Regards.

---

### Post by bigsigh on 2014-02-27
> **papibe said:**
> 
Regarding network layout, you usually want to do something like:
```
                                                 ____eth1--> subnetwork1
                                               /
Internet -> modem/router -> (eth0) UbuntuServer
                                               \
                                                 ----eth2--> subnetwork2
```

Hi Papibe,
Thank you for your time.

What you propose is very easy.

What I propose is this;
```

                            / -eth1-- subnetwork1 -- eth0 - \
Internet -> modem/router ->                                   UbuntuServer
                            \ -eth3-- subnetwork2 -- eth1 - /
```

UbuntuServer is not a gateway, it is not a bridge, it is not a firewall, it is simply a client with 2 internal interfaces each with it's own ip on it's own subnet.

I could have two physical UbuntuServer, as clients, each with one interface, each on it's own subnet.

I propose one UbuntuServer as a client with 2 interfaces, each interface on its own subnet.

---

### Post by SeijiSensei on 2014-02-27
Are you thinking that using two ethernet adapters on the server will speed things up?  For that you should be using [bonding]("https://help.ubuntu.com/community/UbuntuBonding").  The arrangement you propose could actually be slower than using just one adapter because of routing issues.

Gigabit Ethernet is orders of magnitude faster than most upstream Internet connections, except perhaps in a few countries with really high-bandwidth networks.  I'd just stick with one interface on the router connecting to one on the server.  Performance won't be an issue.

---

### Post by papibe on 2014-02-27
I see it now, thanks.

I personally can't see what would be the value on that, but I may be not getting the whole picture.

I'd recommend not setting up the server to route the traffic between the subnetworks because the router would both be the gateway to the Internet, and route the traffic between your subnetworks.

I imagine your modem/router supports VLANs? Or you have a intelligent switch after the router?

The router is going to do DHCP, isn't it?

Regards.

---

### Post by tgalati4 on 2014-02-28
There might be a performance increase if you set up a hypervisor and set up 2 virtual machines, each with its own, dedicated network interface.  But you would have to do some testing to see if this holds true.  As SeijiSensei suggests, your internet-facing connection will be the bottleneck, and possible traffic collisions between the subnets on your router may actually hurt performance.  Remember, the router is a CPU as well, so if it is battling traffic collisions, it is not passing traffic.

---

### Post by bigsigh on 2014-02-28
Gentlemen, Thank you for your help.

This is not an application for bonding or sharing.

I also believe I understand where the problem is but I won't be able to verify this until I can get this server out of production.

I did fire up a Ubuntu 13.10 live disk on a laptop and connected the wifi to an access point on one subnet by dhcp and was able to set a static ip on another subnet on the ethernet which would respond to pings from the gateway, the route table as shown by ip route looked appropriate with the default being the gateway assigned to wifi and both interfaces showd their respective ip's on each subnet.

I haven't had a case like this before which is why I confused myself, I was sure this should work but lacked confidence because I hadn't messed with it and it's a production server.

---

### Post by bigsigh on 2014-02-28
I'm so disgusted with myself. I discovered this Ubuntu server had two different network managers running. Once I shut one of them down the interfaces and routing worked just as it's supposed to.

smh.

I wish someone had just said, 'sure that works' instead of everyone trying to figure out the why I'm doing what I'm doing, I would have looked into the why a couple of days ago and this would have been fixed.

Regardless, Thank you for your input, you folks were actually much more helpful than a couple of other forums.

---

### Post by koenn on 2014-02-28
> **bigsigh said:**
> I wish someone had just said, 'sure that works' instead of everyone trying to figure out the why I'm doing what I'm doing,.

your questions were impossible to answer without some indication of  what "it works" actually meant. 
Yes, 2 NIC's with separate subnets  in one machine is something that works.  But  you knew that amready, given your reply to  papibe's suggestion. 
you asked "Is this possible? Is it routable?"  - well; that all depends on what  it is  you're trying to do, but you did not explain any of that.

---

