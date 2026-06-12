---
title: "Private Network for VoIP and File Sharing?"
date: 2011-05-16
forum: The Cafe
---

### Post by Philsoki on 2011-05-16
Hey guys, a friend and I want to set up a private network that doesn't require an internet connection. We basically just want it for VoIP/Video Chat, instant messaging and file sharing. 

We live about 200 meters apart. What kind of hardware would I need for this, and what  (Preferably open source) software would you recommend? How much would it cost for a set up like this? Anyone on here that's got something like this that could give me some pointers?

I should mention that we want it to be a wireless network.

---

### Post by tmette on 2011-05-16
> **Philsoki said:**
> Hey guys, a friend and I want to set up a private network that doesn't require an internet connection. We basically just want it for VoIP/Video Chat, instant messaging and file sharing. 

We live about 200 meters apart. What kind of hardware would I need for this, and what  (Preferably open source) software would you recommend? How much would it cost for a set up like this? Anyone on here that's got something like this that could give me some pointers?

I should mention that we want it to be a wireless network.

Umm..I'm not sure of any way you can do this without the Internet, unless of course you had a 200 meter ethernet cable and router/switch.

---

### Post by Philsoki on 2011-05-16
> **tmette said:**
> Umm..I'm not sure of any way you can do this without the Internet, unless of course you had a 200 meter ethernet cable and router/switch.
But the Internet is a network. I just want to make my own one, and much, much smaller.:)

---

### Post by juancarlospaco on 2011-05-16
2 Cisco/Linksys routers 802.11N with external antenna connector, 
2 Parabolic antenna on your roof.

---

### Post by Smilax on 2011-05-16
laser pen and light sensor

---

### Post by aeiah on 2011-05-16
there's not much point doing p2p if there's only two nodes. you might as well do server-client. for filesharing, set up FTP servers or something.

you should be able to set something up for voip too since there opensource voip servers exist. i dont know enough about them to suggest one though.

your only cost is going to be in powerful wifi radios. you dont necessarily need two routers (one router with antenna in one house, one powerful wifi card/antenna in the other), although you may find it more stable.

---

### Post by arvevans on 2011-05-16
The reply recommending a pair of hubs with directional antennas is good.

I did something similar with a pair of WiFi dongles (one on each end of the link) with tin-foil and cardboard reflectors to focus the signal.  Then use ad-hoc mode with the WiFi configuration to make one end the host and the other end the client.  You will have to define this supplementary network in the IP configuration of whichever end you make the host, turn on DHCP, and let the client lock onto that network.  Alternatively you could use fixed IP addresses and add fixed routing for that supplementary network on both computers.  WiFi encryption will keep others from joining your network and/or monitoring the data flowing over it.

WiFi can be used for quite long distances (several miles) if the path is clear and if you have enough gain in the antenna systems.  Problem with adding antenna gain is that in the US there are ERP (Effective Radiated Power) limitations on the generic WiFi license and it is easy to make your device too powerful with a risk of FCC involvement.  WiFi is licensed in the US as a "Secondary User" of it's frequency spectrum, which means that you have to live with any interfering signal (change channels if you have this problem) and that you have to change channels if you are causing interference to the primary licensee of that frequency spectrum.

---

### Post by eriktheblu on 2011-05-16
Mumble/Murmur is not too difficult for VOIP.

For file sharing, I'd just go with a shared directory.

---

### Post by timZZ on 2011-05-16
It can be done but why would you want to?  The cost of running such a setup would be more than the cheapest internet package.

Seems a silly request.

You would have to host your own voip, instant messaging services but this isn't something that big companies do not do for internal practices. (Excluding the 200 metres as generally this is ethernet)

As I said ... You will have fun supporting it and it would probably just cheaper to get the cheapest internet connection.

You would also require good knowledge in radio signals as you will have to boast it from a router.

The routers will need to be paired to be on the same sub-net and then you will be both on an internal network.

---

### Post by Philsoki on 2011-05-16
> **timZZ said:**
> It can be done but why would you want to?  The cost of running such a setup would be more than the cheapest internet package.
What's a rough estimate on how much it would cost to keep it running?

And thanks everybody for all the suggestions and advice.:)

---

### Post by arvevans on 2011-05-18
Lots of questions about why one would want to set up a private WiFi link.  One answer is so that two people can share one Internet access.  This decreases cost to zero for one at the expense of some bandwidth loss for the other.  Some ISPs will say you cannot do this but there is almost no way they can tell that it is not just a second computer or WiFi connected laptop at one location.

Real-time video sharing is another reason to have a private WiFi link between closely spaced locations.

A private security (video motion detection) system is another reason to have such a link.

---

