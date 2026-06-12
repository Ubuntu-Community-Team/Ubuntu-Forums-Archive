---
title: "IPTABLES problem"
date: 2007-07-29
forum: Server Platforms
---

### Post by FastZ on 2007-07-29
Hey guys, I know there is lots of talk on here about IPTABLES but I'm having problems with getting them to work on my server.  I have a web service running on port 8888 on my server and i have shared the address to that service with some friends of mine, but apparently, that port's been found by some people that I don't really care to grant access to.  I've tried to block their IP addresses using IPTABLES but even after I create an entry in my IPTABLES, the connection made with this random IP address is still there and they continue to connect to my server.  I've found the only thing that stops them is if I run Firestarter and lock the "firewall" completely, but then that keeps my friends from accessing the server and myself from accessing it as well when surfing to it from within my LAN.  Is there a fool-proof way to create good IPTABLES, maybe using a GUI and a little less of the CLI?  Also, how do you break a connection that's made to your server?  For example, say there is somebody surfing my server and it's somebody that I don't know, nor want to have surfing my server.  How do I break their connection that they made and make it where they can no longer ever surf my server?  Thanks for any help.  I appreciate it.

---

### Post by PilotJLR on 2007-07-29
How have you been banning people with iptables? I ask because this should be all you need:

```

sudo iptables -A INPUT -s <source ip address> -j DROP

```

---

### Post by murraymca on 2007-07-30
You could use SSH port forwarding, give your friends the public keys...and have them access your server over the tunnel.  Would that be an option?  tcpwrappers could be used on ssh to restrict access for more protection.  

Your friends could use something like:

ssh -f -N -L8888:localhost:8888 your_address_they_browse_to

Of course I'm not sure of the exact syntax or what the local port number would be (so I just plugged 8888 into both).  Sure you will figure it out...if you decide to do it let us know if you have any problems.

Cheers.

---

### Post by HermanAB on 2007-07-30
Hmm, no, not -A, use -I instead.

The -A option add a new rule at the bottom of the list.
The -I option stuffs a new rule in at the beginning of the list.

So if you wish to drop something on the floor cold turkey, then you got to stuff that rule in at the front, before it has a chance of being accepted by something else:
iptables -I INPUT -s 1.2.3.4 -j DROP

I struggled with this myself few years ago, so now I know...

'Hope that helps!

Herman

---

### Post by murraymca on 2007-07-30
I know what you mean...I hope you didn't see my post about IPTABLES processing order :P

---

### Post by FastZ on 2007-07-31
> **PilotJLR said:**
> How have you been banning people with iptables? I ask because this should be all you need:

```

sudo iptables -A INPUT -s <source ip address> -j DROP

```

That's how I was creating entries in my iptables.  Just amending them to the list.  I had even tried to block a source address from accessing certain ports and that didn't work either.

> **murraymca said:**
> You could use SSH port forwarding, give your friends the public keys...and have them access your server over the tunnel. Would that be an option? tcpwrappers could be used on ssh to restrict access for more protection.

Your friends could use something like:

ssh -f -N -L8888:localhost:8888 your_address_they_browse_to

Of course I'm not sure of the exact syntax or what the local port number would be (so I just plugged 8888 into both). Sure you will figure it out...if you decide to do it let us know if you have any problems.

Cheers.

That'd never work as a lot of my friends who visit my server aren't "computer inclined".  Basically, I think most of them would rather just stop using my server than have to learn how to type that into a command line.  

> **HermanAB said:**
> Hmm, no, not -A, use -I instead.

The -A option add a new rule at the bottom of the list.
The -I option stuffs a new rule in at the beginning of the list.

So if you wish to drop something on the floor cold turkey, then you got to stuff that rule in at the front, before it has a chance of being accepted by something else:
iptables -I INPUT -s 1.2.3.4 -j DROP

I struggled with this myself few years ago, so now I know...

'Hope that helps!

Herman

Never thought about that and it makes perfect sense.  I'll try it.

---

### Post by murraymca on 2007-07-31
iptables is probably the best way, but if you open up more services like irc or things like that for your friends hehe...you could go back to ssh port forwarding.  You could just put it down in a script and let them know to click on it before trying to access your service (if that would make it easier on them).

Hope you sort it out.

---

