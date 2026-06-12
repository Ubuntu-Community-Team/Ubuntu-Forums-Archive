---
title: "Is This Standard?"
date: 2009-02-13
forum: The Cafe
---

### Post by kevin11951 on 2009-02-13
I have been researching networks, and this is what I consider to be standard, is that right?

---

### Post by gletob on 2009-02-13
I don't really know what you mean by standard but that should work.

Are you planning on using the dhcp server of the router

How much distance is between the two switches?

How will you be connecting the two switches?

---

### Post by kevin11951 on 2009-02-13
> **gletob said:**
> I don't really know what you mean by standard but that should work.

Are you planning on using the dhcp server of the router

How much distance is between the two switches?

How will you be connecting the two switches?

1.  yes, dhcp of untangle will be on, question:  does the untangle dhcp server, allow you to connect a switch to a switch, and it still gives ip addresses to those on the second switch?

2.  none, its a one room office.

3.  all the lines in the diagram are cat 5e cables

---

### Post by wmcbrine on 2009-02-13
> **kevin11951 said:**
> 1.  yes, dhcp of untangle will be on, question:  does the untangle dhcp server, allow you to connect a switch to a switch, and it still gives ip addresses to those on the second switch?Yes (and it's not dependent on the specific dhcp server). You'd be amazed how deeply you can stack switches. There's a rule for hubs... none for switches, that I know of. But with only two, I think you'd be safe even with hubs.

---

### Post by kevin11951 on 2009-02-14
> **wmcbrine said:**
> Yes (and it's not dependent on the specific dhcp server). You'd be amazed how deeply you can stack switches. There's a rule for hubs... none for switches, that I know of. But with only two, I think you'd be safe even with hubs.

oh, that good, i wasnt sure.  Just out of curiosity, what is the rule with hubs?

---

### Post by wmcbrine on 2009-02-14
I had to look it up... it's been so long since it was relevant:

> The need for hosts to be able to detect collisions limits the number of hubs and the total size of the network. For 10 Mbit/s networks, up to 5 segments (4 hubs) are allowed between any two end stations. For 100 Mbit/s networks, the limit is reduced to 3 segments (2 hubs) between any two end stations, and even that is only allowed if the hubs are of the low delay variety.

[http://www.nationmaster.com/encyclopedia/Ethernet-hub](http://www.nationmaster.com/encyclopedia/Ethernet-hub)

---

### Post by ugm6hr on 2009-02-14
I've been looking at networking platforms and found this: [http://ebox-platform.com/product/use-cases/#uc-multiple](http://ebox-platform.com/product/use-cases/#uc-multiple)

Available essentially preconfigured with Ubuntu in an install CD.

---

### Post by walkerk on 2009-02-14
What speed is the uplink between switches? Say its 100 MB/s, all of you employees will share that bandwidth whereas your servers will each get 100 MB/s in the LAN. The best solution would to have a Gigabit ISL (inter-switch link)... Just a tip.

---

### Post by gletob on 2009-02-14
> **walkerk said:**
> What speed is the uplink between switches? Say its 100 MB/s, all of you employees will share that bandwidth whereas your servers will each get 100 MB/s in the LAN. The best solution would to have a Gigabit ISL (inter-switch link)... Just a tip.
That's what I was thinking

---

### Post by BuffaloX on 2009-02-14
With all systems being in the same room, you should only use one switch for best performance and reliability.
Adding an extra switch increases complexity and an unnecessary bottleneck.
Otherwise it seems perfectly sound.

---

### Post by kevin11951 on 2009-02-14
Ok, I updated it for only one switch...

I also feel it is a little more aesthetically pleasing :).

---

### Post by wmcbrine on 2009-02-15
> **kevin11951 said:**
> Ok, I updated it for only one switch...That's fine, but you understand there was no *need* to do that, right? Your two-switch design was fine, too.

---

### Post by MikeTheC on 2009-02-15
No, actually that's not a standard way to network systems.

This is a much more standard network topology:

[img]http://www.thp.uni-koeln.de/~lassig/images/network01.jpg[/img]











[font=arial][size=1]</sarcasm>[/size][/font]

---

### Post by doas777 on 2009-02-15
who are your customers for the web server and the WAP? if you want to expose the webserver to the web, I would recommend placing it in a DMZ. same with the WAP, if it might be used by externals. email should definetly be in the DMZ, so that external servers can send messages to it, without allowing those servers access to your internal network.

I prefered the two switch version. we usually use a fiber switch for our servers/SAN in the datacenter and attach it to a fast-ethernet switch fabric (4 switches per floor, each floor in it's own VLAN, running through a shared backbone between floors.).

also do you have any need for remote access? 

just out of curisoity, who's network is this and how much money do they have?

---

### Post by BuffaloX on 2009-02-15
Both layouts will work just fine, but one switch is more efficient than two.
You should only use more switches if it simplifies your wiring.
Like maybe having one wire across the room instead of four in this case.

Couldn't you combine the mail and file/print server?
That would save a little bit of power and would be one less noise source.

What does the VM server do?

Having 4 servers for 4 users seems a bit extreme to me, but maybe I'm just old fashioned. :P

---

### Post by kevin11951 on 2009-02-15
> **doas777 said:**
> who are your customers for the web server and the WAP? if you want to expose the webserver to the web, I would recommend placing it in a DMZ. same with the WAP, if it might be used by externals. email should definetly be in the DMZ, so that external servers can send messages to it, without allowing those servers access to your internal network.

I prefered the two switch version. we usually use a fiber switch for our servers/SAN in the datacenter and attach it to a fast-ethernet switch fabric (4 switches per floor, each floor in it's own VLAN, running through a shared backbone between floors.).

also do you have any need for remote access? 

just out of curisoity, who's network is this and how much money do they have?

Its my fathers business, and not alot (money).  After posting that, i got rid of the email, and web server, because he already has godaddy for that :mad: i like working on servers.

> **BuffaloX said:**
> Both layouts will work just fine, but one switch is more efficient than two.
You should only use more switches if it simplifies your wiring.
Like maybe having one wire across the room instead of four in this case.

Couldn't you combine the mail and file/print server?
That would save a little bit of power and would be one less noise source.

What does the VM server do?

Having 4 servers for 4 users seems a bit extreme to me, but maybe I'm just old fashioned. :P

all the wiring is in the ceiling, so mess isnt an issue.  VM = vitrual machine server,  He needs visio, and autocad (2d) and that is the best solution i could come up with so far.  Also there are more than four employees, but i didnt want to crowd the diagram.

---

