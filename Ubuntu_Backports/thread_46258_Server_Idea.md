---
title: "Server Idea"
date: 2005-07-03
forum: Ubuntu Backports
---

### Post by Kyral on 2005-07-03
I'm just gonna paste in what I said on IRC, 'cause that's the best I can phrase it (keep in mind that as I write this Mirrormax is down)

> <Kyral> They should use a rotating server kinda thingy for Backports, like you go to one addy and it randomly sends you to one of the other servers

If anyone knows the formal name for that, really cool, but I think it would help Backports with things like servers going down and whatnot

---

### Post by ShaneAu on 2005-07-03
[QUOTE=Kyral]I'm just gonna paste in what I said on IRC, 'cause that's the best I can phrase it (keep in mind that as I write this Mirrormax is down)



If anyone knows the formal name for that, really cool, but I think it would help Backports with things like servers going down and whatnot[/QUOTE]
 MirrorMAX is half down. ubuntu-backports.mirrormax.net is across two servers (use to be three but the third wasn't needed). One of the servers are down, it's just magically went down... very anoying. I've sent a ticket to the DC it's in regarding the matter. The main server for MirrorMAX is up. There's no point in me changing the DNS record to only the one server because the server that's down will be back up soon, so might aswell wait.

Sorry. :(.

I simply use Round Robin DNS, so if a server in my own cluster happens to go down, it will still give the IP to the client trying to connect, you'd just have a 50% chance of connecting to the server that's up.

---

### Post by Darrena on 2005-07-03
[QUOTE=Kyral]I'm just gonna paste in what I said on IRC, 'cause that's the best I can phrase it (keep in mind that as I write this Mirrormax is down)



If anyone knows the formal name for that, really cool, but I think it would help Backports with things like servers going down and whatnot[/QUOTE]

It is load balancing, the easiest way to do this would be to use DNS and create multiple A records for the same name (This is called round-robin DNS) and point it to a couple of different servers.  With multiple A records users will recieve different servers.  Of course this would not evenly balance the connections and if one failed people would still have problems.  We do this at work for a couple of apps and simply manually change the NAT if one goes down.

A higher-end (and costly) solution would be many of the load-balancing solutions out there but even the open-source ones will require a server to handle it and with the potential number of connections it would not be a cheap one...  Maybe one of the current mirrors might have a server to be used for this?

At this time unless someone is willing to donate a server and the costs for hosting it I can't see this being an option.  Additionally I am not sure if it is a big deal if a mirror goes down, try again in a few hours or switch to a different mirror...

Your idea is not a bad one, just not practical and I am sure that jdong and others looked into some of the load-balancing options and found too many issues and settled on the current arrangement as a compromise.

---

### Post by Darrena on 2005-07-03
[QUOTE=ShaneAu]MirrorMAX is half down. ubuntu-backports.mirrormax.net is across two servers (use to be three but the third wasn't needed). One of the servers are down, it's just magically went down... very anoying. I've sent a ticket to the DC it's in regarding the matter. The main server for MirrorMAX is up. There's no point in me changing the DNS record to only the one server because the server that's down will be back up soon, so might aswell wait.

Sorry. :(.

I simply use Round Robin DNS, so if a server in my own cluster happens to go down, it will still give the IP to the client trying to connect, you'd just have a 50% chance of connecting to the server that's up.[/QUOTE]

Hey man, nothing to be sorry for!  Things happen and I think the OP knows that and was just offering a suggestion.   Your help is greatly appreciated by everyone and some downtime in no way diminshes that contribution.

---

### Post by ShaneAu on 2005-07-04
Ok the second MirrorMAX server is back online. :). Apparently it was hardware issues, the RAM was replaced.

---

