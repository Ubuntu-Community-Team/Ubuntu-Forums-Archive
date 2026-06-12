---
title: "MaaS - Nodes can't connect to server after bootstrap"
date: 2012-10-01
forum: Server Platforms
---

### Post by Fajkowsky on 2012-10-01
I installed maas and I was able to add nodes and they became in ready state.

I executed:

juju bootstrap
And then one of my nodes is waking up and I receive this message on server (after juju status):

[http://i.stack.imgur.com/ESWd6.jpg](http://i.stack.imgur.com/ESWd6.jpg)

And this message is shown on node after it wakes up:

[http://i.stack.imgur.com/QyfHj.jpg](http://i.stack.imgur.com/QyfHj.jpg)

I am doing this several times and each time I receive the same result.

I think something is wrong with my network. It look like this:

internet <-> router <-> switch <-> nodes
                |
                |<----->server

Router is used as a DHCP Server. It's ip is 192.168.0.1 - it's my default gateway. When I was installing maas server I installed dnsmasq and I have used as a range 192.168.0.5-192.158.0.200 and for gateway I used 192.168.0.1 and for domain I used nothing. I was able to add nodes without problems.

What maybe the problem not letting nodes to connect to maas server?

---

