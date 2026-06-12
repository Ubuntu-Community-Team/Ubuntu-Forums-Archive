---
title: "Security out of the box."
date: 2009-03-14
forum: Server Platforms
---

### Post by EmanresuusernamE on 2009-03-14
I was wondering, how secure is an Ubuntu server straight out of the box?  I know it's not like Windows which opens most everything up right from the get go.

1. What all ports are opened by default on a vanilla installation?  

2. I know iptables is installed by default, but how good is it out of the box with good user names and passwords?  

3. Should I buckle it down more with another firewall, or perhaps just alter the settings with something like Shorewall?

4. Does it open a port when a program starts to listen on that port automatically?

5. Does anyone know how hard it is to do a brute force attack on a new install?

In a nutshell what are there any major Got'chas I should know about?  The company I'm working for is thinking of pushing Ubuntu boxes, and I'd like to know what all we should really do to harden the defenses of our servers and inform our customers about.

---

### Post by windependence on 2009-03-15
If security is priority, you should look at OpenBSD. **[COLOR=#e00000]Only two remote holes in the default install, in more than 10 years![/COLOR]**

[http://www.openbsd.org/](http://www.openbsd.org/)

-Tim

---

### Post by Cheesemill on 2009-03-15
Not sure about the rest but for No 1 - None
All ports are closed on a default install.

Cheesemill

---

### Post by sisco311 on 2009-03-15
[thread=510812]Ubuntu Security[/thread]

---

### Post by hyper_ch on 2009-03-15
> **EmanresuusernamE said:**
> 1. What all ports are opened by default on a vanilla installation?
They are on ubuntu also - but no daemons are listening...

> **EmanresuusernamE said:**
> 2. I know iptables is installed by default, but how good is it out of the box with good user names and passwords?
As above, by default iptables has no rules setup in ubuntu. So nothing gets filtered and that's good as there are no daemons running. User and passwords have nothing to do with iptables.

> **EmanresuusernamE said:**
> 3. Should I buckle it down more with another firewall, or perhaps just alter the settings with something like Shorewall?
What are you afraid of?

> **EmanresuusernamE said:**
> 4. Does it open a port when a program starts to listen on that port automatically?
No ports are closed, so nothing needs to be opened.

> **EmanresuusernamE said:**
> 5. Does anyone know how hard it is to do a brute force attack on a new install?
Depends on the install. If you use a vanilla 8.04 there's still a serious bug in it that reduces the randomness massivley. I think if you get the 8.04.1 cd it's fixed there already.

> **EmanresuusernamE said:**
> In a nutshell what are there any major Got'chas I should know about?
Security is a progress...

---

### Post by EmanresuusernamE on 2009-03-15
> **hyper_ch said:**
> They are on ubuntu also - but no daemons are listening...


As above, by default iptables has no rules setup in ubuntu. So nothing gets filtered and that's good as there are no daemons running. User and passwords have nothing to do with iptables.

I'd still like to close down the ports that aren't in use.  The next big security hole may just exploit something like that.

> **hyper_ch said:**
> What are you afraid of?
What'cha you got? In order to really push Ubuntu servers to customers, you have to know a good deal at least of what all is possible with them out of the box.  To really scrub any Ubuntu sales, all one idiot customer has to do is look online and find one little detail we didn't see to make us look stupid.  These people are going to be coming from Windows servers and the more we can explain to them, the better Ubuntu servers look to them.

> **hyper_ch said:**
> No ports are closed, so nothing needs to be opened.See above.

> **hyper_ch said:**
> Depends on the install. If you use a vanilla 8.04 there's still a serious bug in it that reduces the randomness massivley. I think if you get the 8.04.1 cd it's fixed there already.
Upgraded to 8.10.

> **hyper_ch said:**
> Security is a progress...So is paranoia.  Especially coming from Windows machines.

---

### Post by koenn on 2009-03-15
> **EmanresuusernamE said:**
> I'd still like to close down the ports that aren't in use.  The next big security hole may just exploit something like that.
The mere fact that no program is using "a port", means that a port is closed. Therefore: no deamons => no open ports.
You can install a firewall if you want, and have it "block ports", but all it's going to do is block traffic to a non-existing destination.
You need to read up on tcp/ip networking.

> **EmanresuusernamE said:**
> 
What'cha you got? In order to really push Ubuntu servers to customers, you have to know a good deal at least of what all is possible with them out of the box.  To really scrub any Ubuntu sales, all one idiot customer has to do is look online and find one little detail we didn't see to make us look stupid.  These people are going to be coming from Windows servers and the more we can explain to them, the better Ubuntu servers look to them.

See above.
If you're going to sell/push servers, you better have some basic understanding of servers and networking, or you're going to look stupid in the eyes of customers who know more than you. Not a good way to promote Ubuntu, imo.

---

