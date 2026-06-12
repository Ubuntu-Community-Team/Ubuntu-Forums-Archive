---
title: "firewalled network access?"
date: 2007-04-13
forum: Server Platforms
---

### Post by 95aspire on 2007-04-13
ok got my server set up but the firewall, when its enabled i cant access my storage drive, but when its disabled i can access fine, 

what i need to know is what to do to enable access for this thro the firewall, ive allowed access for my ip addresses but still dont work. 

help asap is appriciated. thanks in advance.

---

### Post by kidders on 2007-04-13
Hi there,

You'll need to provide a little more information to help identify your problem. For instance, is your storage device a network share? If so, how are you sharing it? Where is it in relation to you (or your LAN)?

Also, what kind of firewall are you using, and what rules have you defined so far?

---

### Post by 95aspire on 2007-04-13
yes the drive is in my ubuntu box, its an 80gb drive. also have a 10gb for my website, but im using the firestarter gui to config the default firewall. the only rules ive made that i have figured out so far, is 1. forwarding azureus (which works) for connections, and 2. set up my lan ips from my comp and my sisters comp to the allowed incoming connection,

i admin both machines as its just in a home network. the machine im on now is my xp machine, and i have the firewall disabled right now on the linux box, and i can access the files fine, but the moment i enable the firewall and try to access the drive im denied access and get no notice in firestarter events tab.


EDIT
sorry for the post but i couldnt figure what to put for the search terms, i tried a few diffrent ones before posting tho but nothing worked

---

### Post by kidders on 2007-04-13
Hey again,

Since you mention WinXP, I'm assuming you're sharing your files with Samba. In that case (if memory serves), you need to be sure to allow internal (but _absolutely not external_) access to ports 139 and 145. Exactly what to open up depends on the specifics of your network.

In general terms, there is little to be gained by not allowing *all* local traffic on a home network. My tendency would be just to open up access to everything, in an environment where malicious local activity is not a concern.

---

### Post by 95aspire on 2007-04-13
well then how to i open full network traffic for ip addresses from my network? but ill try those ports in the mean time

---

### Post by 95aspire on 2007-04-13
ok those ports worked, thats what i was needing, just couldnt think of what the samba service was called, i had a brain fart lol, thanks but i would still appriciate how to open full local ip address access for the server. 

thanks

---

### Post by kidders on 2007-04-13
I've never use Firestarter, but there *must* be a way of defining access control based on network interface or netmask. Traffic both originating on _and_ destined for internal machines (based on whatever criteria you prefer) is pretty safe to allow, in low-security environments.

---

### Post by 95aspire on 2007-04-13
ya i realize this lol

guess i should add this is my first ubuntu box, ive had it running for about 6 months tho. so still tinkering with it

---

### Post by kidders on 2007-04-13
You haven't provided enough detail to be any more specific, I'm afraid. As I mentioned before, the sort of traffic you (possibly) want to unblock is local, both in terms of its origin and destination. Opening the door to traffic that only fulfils one of these criteria might have unintended results.

With most firewalls, you have to identify the traffic you want to manipulate in terms a router can understand, eg...[LIST]
[*]What network interface is it arriving on or departing through?
[*]What are the source and destination addresses/networks?
[*]What packet transmission protocol is being used?[/LIST]So, assuming you know your own network's netmask, and what is plugged into your computer's network interfaces, you have some criteria to create new rules with. Unfortunately, there is no way to "guess" this information.

One big issue for consideration is whether that basic info I suggested really is enough to identify internal traffic. Again, this depends on your own network configuration. For example, if your computer only has one network interface, it may not be. Unfortunately, without a good picture of your network topology, there is no way to know.

It might be worth reading up on network packet management, routing & firewalling, etc. to give yourself a clearer idea of what's involved.

---

