---
title: "Best distro for 'network server'?"
date: 2011-10-26
forum: Server Platforms
---

### Post by porchrat on 2011-10-26
Hi all

Maybe this is the wrong forum and maybe "network server" is the wrong word. However I find a lot of folks in this forum to be very knowledgeable not just of Ubuntu but Linux in general so I'm hoping some of you will have some interesting and helpful suggestions.


Anyway here is the issue:
There are quite a few people using my little network. Most are laptops connecting to a little wireless router which in turns connects to my ADSL router which (obviously) provides my Internet connection.

Up until now I have relied on each individual to setup their own security on their various devices but I'm uncomfortable with this approach. I have decided that if possible I want to setup a box between the ADSL router and the wifi router to act as a general firewall. Maybe to store some unimportant files like media or backups on too if that is not too insecure. I happen to have a slightly older box sitting here gathering dust that I would like to get some use out of. It isn't the fastest machine in the world but it is an Athlon with what upon inspection looks like 2GB of DDR-400 RAM so it should be capable of running some relatively interesting stuff.

Is there any particular distro suited to this sort of job? I've done some searching but I really don't know what I'm looking for here. While I'm pretty familiar with Ubuntu and the terminal in general the only other distro I've ever used was an ancient version of Gentoo.

Otherwise is Ubuntu capable of performing this role and if so what sort of stuff would you recommend I install and what key things should I do when setting it up?

Also does anyone maybe have any guides or articles I could read to bring me up to speed with proper practice when attempting something like this.

Thanks again guys.

---

### Post by surfer on 2011-10-26
[ipcop]("http://www.ipcop.org/") is a nice operating system for a firewall, as far as i know. i do not know if you can store backups there.

other than that you can do a [minimal ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD") installation, configure iptables as firewall and add whatever else you like.

---

### Post by CharlesA on 2011-10-26
I'm a fan of pfSense for a firewall appliance.

---

### Post by porchrat on 2011-10-26
> **surfer said:**
> [ipcop]("http://www.ipcop.org/") is a nice operating system for a firewall, as far as i know. i do not know if you can store backups there.

other than that you can do a [minimal ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD") installation, configure iptables as firewall and add whatever else you like.

Storing backups would be nice but it isn't absolutely necessary. It is definitely way down on my priority list ATM.

I usually use ftw. I don't know why but iptables itself always scared the mutton curry out of me.

I will take a look at ipcop as well thank you for the suggestion.

---

### Post by Lars Noodén on 2011-10-26
[Ubuntu Server](http://www.ubuntu.com/business/server/overview) would be a good choice, though I would always recommend Debian Stable for servers also.  On either you have a lot of packages to add storage or other capabilities.  Firewalls are overrated, but both come with IPTables.

---

### Post by porchrat on 2011-10-26
> **CharlesA said:**
> I'm a fan of pfSense for a firewall appliance.

> **Lars Noodén said:**
> [Ubuntu Server](http://www.ubuntu.com/business/server/overview) would be a good choice, though I would always recommend Debian Stable for servers also.  On either you have a lot of packages to add storage or other capabilities.  Firewalls are overrated, but both come with IPTables.

pfSense looks good as well.

I have been reading up and now I'm not sure about needing a dedicated machine as a firewall. Is my wifi NAT router not good enough as a firewall? After all it is blocking all incoming packets. I did at one point setup a DMZ to allow one dude remote access through SSL but that is no longer the case.

It seems like a lot of power usage to keep this bugger up and running 24/7 just to inspect the outgoing stuff.

---

### Post by Lars Noodén on 2011-10-26
> **porchrat said:**
> pfSense looks good as well.

I have been reading up and now I'm not sure about needing a dedicated machine as a firewall. Is my wifi NAT router not good enough as a firewall? After all it is blocking all incoming packets. I did at one point setup a DMZ to allow one dude remote access through SSL but that is no longer the case.

It seems like a lot of power usage to keep this bugger up and running 24/7 just to inspect the outgoing stuff.

Firewalls are overrated.  Your wifi NAT router is probably good enough.  It might be a model on which you can run pfSense.  Or you can buy such a model and load pfSense and keep your current as a spare.

---

### Post by collisionystm on 2011-10-26
> **porchrat said:**
> Hi all

Maybe this is the wrong forum and maybe "network server" is the wrong word. However I find a lot of folks in this forum to be very knowledgeable not just of Ubuntu but Linux in general so I'm hoping some of you will have some interesting and helpful suggestions.


Anyway here is the issue:
There are quite a few people using my little network. Most are laptops connecting to a little wireless router which in turns connects to my ADSL router which (obviously) provides my Internet connection.

Up until now I have relied on each individual to setup their own security on their various devices but I'm uncomfortable with this approach. I have decided that if possible I want to setup a box between the ADSL router and the wifi router to act as a general firewall. Maybe to store some unimportant files like media or backups on too if that is not too insecure. I happen to have a slightly older box sitting here gathering dust that I would like to get some use out of. It isn't the fastest machine in the world but it is an Athlon with what upon inspection looks like 2GB of DDR-400 RAM so it should be capable of running some relatively interesting stuff.

Is there any particular distro suited to this sort of job? I've done some searching but I really don't know what I'm looking for here. While I'm pretty familiar with Ubuntu and the terminal in general the only other distro I've ever used was an ancient version of Gentoo.

Otherwise is Ubuntu capable of performing this role and if so what sort of stuff would you recommend I install and what key things should I do when setting it up?

Also does anyone maybe have any guides or articles I could read to bring me up to speed with proper practice when attempting something like this.

Thanks again guys.


Use Zentyal.

It only does everything.

Very EASY and INTUITIVE. 

[www.zentyal.com](www.zentyal.com)

It has more features than you probably need, but it will do everything you want very easily.

---

### Post by CharlesA on 2011-10-26
> **Lars Noodén said:**
> Firewalls are overrated.  Your wifi NAT router is probably good enough.  It might be a model on which you can run pfSense.  Or you can buy such a model and load pfSense and keep your current as a spare.

This.

> **collisionystm said:**
> Use Zentyal.

It only does everything.

Very EASY and INTUITIVE. 

[www.zentyal.com](www.zentyal.com)

It has more features than you probably need, but it will do everything you want very easily.

And That. ;)

---

### Post by porchrat on 2011-10-26
OK so you guys are saying that the NAT router is probably going to be good enough?

The ADSL router has a firewall as does the wireless router. On top of that all the important machines with my work stuff on them run Linux with default deny policies for all the incoming traffic.

Maybe I'm better off just cleaning this machine out (it is helluva dusty) and using it as a backup server... hmmm...

---

### Post by Lars Noodén on 2011-10-26
> **porchrat said:**
> Maybe I'm better off just cleaning this machine out (it is helluva dusty) and using it as a backup server... hmmm...

Does its network interface support Wake-on-LAN?  That would be one way to reduce the power consumption you mentioned.

---

### Post by porchrat on 2011-10-26
> **Lars Noodén said:**
> Does its network interface support Wake-on-LAN?  That would be one way to reduce the power consumption you mentioned.

Wow I had never heard of that sort of thing. I honestly don't know.

I don't think it would make that much of a difference though as folks use the Internet around here something like 22 hours out of 24.

---

### Post by samosamo on 2011-10-27
m0n0wall. It does what I need it to do. If I needed more, I'd go for it's bloated son pfSense. Or run two servers, m0n0wall and Zentyal.

---

### Post by wgn on 2011-10-27
SmoothWall

[http://www.smoothwall.org]("http://www.smoothwall.org")

Supposed to be pretty close to a turnkey dedicated firewall.

---

