---
title: "[Advice] What's the best set-up, given the kit I have?"
date: 2010-12-02
forum: Ubuntu Cloud and Juju
---

### Post by keyz182 on 2010-12-02
Hi all,

I'm in the process of planning, then setting up a cloud at the University I work at. I'm trying to figure out what the best set up is, and while I have some ideas, I'd like to get some feedback from people who know their stuff.

Here's the kit we'll have:

4x Node servers (Intel Xeon E5620 4 core 8 thread, 24GB RAM, 2x2TB Hard Drives, 2 Built in Gigabit ethernet, 1 4xGigabit ethernet card)

1x Controller Server (Intel Xeon 2 core, 6 GB Ram, 4 or 8 TB of disk space, 2 built in GB ethernet, 1 4xGigabit Ethernet)

The University has also given us a 24 port Gigabit switch connected to the outside world to use, along with our own subnet to use.

One of the problems is I'm not exactly sure how to best utilise the network we have. Should I connect 4 ports on each server to the switch, and bond them so it appears as a 4GB connection, or should I leave them separate?

Any thoughts?

---

### Post by kim0 on 2010-12-02
Hi keyz182,

UEC does not treat multiple ethernet devices in a specific manner, thus you can either use just one interface (easier, lower throughput) or if you want to utilize all links, then just as you mentioned you can bond them all

Interesting setup, if you'd like to share your setup and experiences with the rest of the community please do. Also, if you hit any documentation problems while working, please help make it better

---

### Post by keyz182 on 2010-12-02
Thanks.

I'm testing a smaller cloud at the moment, off the Uni network with an old pc and two of the nodes.

For the network set up I'm testing now, I've got 

```
(the outside world) --> eth0 (OldPCServer) eth1 ----> nodes
```

eth0 is on 192.168.20.11
eth1 is 10.10.1.1
and the nodes are 10.10.1.2 10.10.1.3

This is using Managed Networking

If I were to bond the connections and plug them all into the switch, that that'd mean I'd have to put the nodes on the same network as the controller, so:


```
(the outside world) ---> controller (192.168.20.11)
                    +--> nodes      (192.168.20.12,13 etc)
```

Would this setup still work with managed networking, and are there any potential issues I need to keep an eye out for?

---

### Post by kim0 on 2010-12-03
thanks for the clear questions :) I am not sure if it would work that way, however why not keep the core switch connected to all bonded cables of NCs, along with eth1 of CLC. And only eth0 of CLC plugs to the public network. At least that's how I'd do it

---

### Post by keyz182 on 2010-12-06
Thanks for the reply! 

So you're suggesting this set-up [(figure 1)]("http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0#figure2") as opposed to this [(figure 1)]("http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0#figure1")?

---

### Post by kim0 on 2010-12-08
That is correct

---

### Post by wcorey on 2011-01-08
An excellent document, that I used to initially set up UEC, is "[COLOR="Navy"]*Intel Cloud Builder Guide to Cloud Design and Deployment on Intel Platforms*[/COLOR]"

[http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fsoftware.intel.com%2Ffile%2F26674%2F&rct=j&q=intel%20cloud%20builder%20guide&ei=D_YoTb3OIsL98AaD-_CrAQ&usg=AFQjCNEFEkmOR-Gwt1fEB1Ij26801_cLxA&sig2=uINJUG_Eeq3dBkXwj4wS_g&cad=rja](http://www.google.com/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fsoftware.intel.com%2Ffile%2F26674%2F&rct=j&q=intel%20cloud%20builder%20guide&ei=D_YoTb3OIsL98AaD-_CrAQ&usg=AFQjCNEFEkmOR-Gwt1fEB1Ij26801_cLxA&sig2=uINJUG_Eeq3dBkXwj4wS_g&cad=rja)

It is available on the web and is quite thorough.

---

### Post by raymdt on 2011-01-09
Very nice stuff. Thanks for sharing :D

---

