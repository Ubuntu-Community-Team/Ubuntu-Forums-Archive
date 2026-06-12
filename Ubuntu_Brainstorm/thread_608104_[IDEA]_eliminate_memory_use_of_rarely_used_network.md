---
title: "[IDEA] eliminate memory use of rarely used network services."
date: 2007-11-09
forum: Ubuntu Brainstorm
---

### Post by CrazyGuy123 on 2007-11-09
Consider the case of a linux installation acting as a router.  It has a web interface for configuration, running under apache.  The web interface probably only gets 1 or 2 hits per day on average.

To be able to serve these requests apache must be always running, consuming considerable amounts of memory, even when doing no actual work.

Why can't a TCP listening socket be opened in a special mode whereby when a packet is received, the correct application is started to handle the request?

The same could apply for any other rarely used network service, so any solution should be generic.

A similar sort of thing could be imlemented in many ways, for example using an always running daemon to hold sockets open and "proxy" data from the application to the socket.

Has this been done already?  Is it a practical idea?  Does the linux community feel it's required?

---

### Post by chrisccoulson on 2007-11-10
I'm sure this is already handled by the inetd or xinetd daemons, which can be set to spawn processes on receipt of packets on specific ports.

---

### Post by CrazyGuy123 on 2007-11-10
Why doesn't ubuntu use this by defualt for nfs sharing, samba sharing, CUPS printer sharing and a whole host of other rarely used desktop services.

---

### Post by coolen on 2007-11-12
It depends on the usage, I guess. In some situations, these services would be commonly used. Launching a process with inetd takes a lot of CPU cycles, and so if it's used often enough, is wasteful.
I've long felt that the Services window was kind of bare. I'd love to see a more robust option for configuring services, with an inetd option.

---

### Post by chrisccoulson on 2007-11-12
redhat-config-services used in Fedora seems to be a more feature complete tool for configuring services and runlevels.

---

### Post by CrazyGuy123 on 2007-11-12
to eliminate the wastefullness of continually quitting and re-opening the service, the service could be designed to only quit if it's been idle (ie. no existing or new connections) for at least 5 mins.

If that system was used, then inetd (or a similar daemon) could be used for ALL network services.  On frequently accessed services they would always run.  For example it could be used to spawn an X server when any GUI app is run (triggered by the TCP connection to the X port on the loopback interface) - which would be always for the desktop environment, but rarely for a server.

---

### Post by chrisccoulson on 2007-11-12
I don't think this is a good idea. If you've got the physical RAM available, it'd be a bit of a waste of that RAM by not keeping the services running, just for the sake of freeing up that additional resource. What else is the RAM going to be used for? Loading from disk on demand would add lag to the service and is a poor use of available resources (akin to not caching stuff in memory just for the sake of giving the impression that the system uses less RAM). The only benefit I see of this is slightly improving boot up time.

If the system is so low on physical RAM that you need to keep the services from loading until needed, then the machine is probably going to choke when they are spawned by inetd anyway. In this case, the user probably wouldn't use the services, and just disable them anyway

I can't think of a real world example where this would benefit anyone.

---

### Post by coolen on 2007-11-12
Well, inetd has been in widespread use for over a decade now, so I'm guessing someone out there had found a use for it.

Just because a system is low on resources doesn't mean it can't run perfectly well as a server. Many old machines have been reborn as servers. They have no problem sharing files over the network, acting as a web server, a mail server, or any other of at least a dozen good uses. However, due to their limited resources, they can't as all at once.

A good example is SSH. Most of these machines are headless, so you use SSH to do your administrative work. You don't use it very often, since it's Linux, and Linux can take care of itself for the most part because it rocks, so why have it running all the time waiting for some action?

Besides, if I understand it correctly, inetd is more wasteful on CPU cycles than RAM. CPU cycles are fairly expendable, since time is, if not infinite, at least available in abundance (and you'll recall that the measure of CPU performance is given in cycles per second).

Another concern is power usage. Having the system run flat out doing nothing for long periods of time is wasteful, and not very nice to your wallet. You want your wallet to be happy, don't you? Lookit 'im!

Also, as you so handily pointed out, in Linux, RAM that's not being used by a program is not wasted RAM. RAM being used by a program that is doing not a gorram thing, on the other hand, is.

---

### Post by coolen on 2007-11-12
> **CrazyGuy123 said:**
> to eliminate the wastefullness of continually quitting and re-opening the service, the service could be designed to only quit if it's been idle (ie. no existing or new connections) for at least 5 mins.

If that system was used, then inetd (or a similar daemon) could be used for ALL network services.  On frequently accessed services they would always run.  For example it could be used to spawn an X server when any GUI app is run (triggered by the TCP connection to the X port on the loopback interface) - which would be always for the desktop environment, but rarely for a server.

This is something that would need to be implemented by the developers of those projects, and they'd need to verify that inetd is present on the system and running, or else they'd be unable to restart.

---

### Post by chrisccoulson on 2007-11-13
> **coolen said:**
> Just because a system is low on resources doesn't mean it can't run perfectly well as a server. Many old machines have been reborn as servers. They have no problem sharing files over the network, acting as a web server, a mail server, or any other of at least a dozen good uses. However, due to their limited resources, they can't as all at once.

A server that is so resource limited isn't going to be a good server. And yes, whilst some people revive old boxes to provide network services, it isn't a typical server setup. Corporate networks with hundreds of clients use servers capable of running all of these services all the time and hardware would be wasted by not keeping these services loaded all the time.

BTW, I have a box at home running ssh and samba with only 32MB of RAM, and it runs fine without having to unload these services. So, I don't know what sort of 'low-end' machine you're talking about.

> A good example is SSH. Most of these machines are headless, so you use SSH to do your administrative work. You don't use it very often, since it's Linux, and Linux can take care of itself for the most part because it rocks, so why have it running all the time waiting for some action?


When I log in to SSH, I like it to happen instantly. My server with 32MB of RAM allows me to do this by keeping SSH running all the time, so why would I want to unload it for the sake of freeing up RAM that isn't going to do anything else

> Besides, if I understand it correctly, inetd is more wasteful on CPU cycles than RAM. CPU cycles are fairly expendable, since time is, if not infinite, at least available in abundance (and you'll recall that the measure of CPU performance is given in cycles per second).


Time is not infinite or in abundance. Time = money. If you tell a large corporation that their network services will take longer to respond because you want to free up RAM to do nothing, then they won't be pleased.

> Another concern is power usage. Having the system run flat out doing nothing for long periods of time is wasteful, and not very nice to your wallet. You want your wallet to be happy, don't you? Lookit 'im!


Again, I come to the example of my server with 32MB of RAM again. Even though it runs the network services 100% of the time, it runs nowhere near flat out (Pentium 133 BTW).
```
cat /proc/loadavg
0.27 0.19 0.16 1/74 24044
```

> RAM being used by a program that is doing not a gorram thing, on the other hand, is.

Not necessarily. If the RAM isn't going to be used for anything else, then it's wasted when you unload the unused service.

---

### Post by coolen on 2007-11-13
Which is why it should be optional.
My points about low end machines are a valid justification for inetd in general. You can have many services running from a single machine. It may be convenient to do so, but inconvenient to have them all running all the time. If you only run two services, then sure, you don't need to worry, but as I said, *you* don't need to worry.

In this case, we were talking about a more general purpose machine. My desktop, for example, runs a few services, since I don't have a low-end machine at my disposal right now, and every so often I add one more. I'd prefer to leave that RAM free for when I'm doing other things, such as opening the GUI application we were discussing to configure my services.

Time = Money does not always apply. Right now, I'm sitting on my laptop, waiting for my sister's clothes to finish washing, and watching (with ever increasing horror) the progress of a Windows install. My time is currently worthless.
For big corporations, it would not make sense to use inetd, which is why its use is optional. We're talking about an easier way to set a service up to run off inetd. I assume these big corporations have people working for them who are smart enough to know this isn't the right choice for them.

I'm talking about the more general case, not the case of big corporations, and not that of you. If someone wants to set up a few services running from their machione, and if they find their computer lags as a result, even when those services are not being used, it would be nice if there were an easy way for them to save on their system resources.
Let them use the daemon mode by default, and let the user choose otherwise should they need to.

---

### Post by chrisccoulson on 2007-11-13
I'm still not sure how this would benefit most people. For example, on my main desktop running Gutsy, I have Samba and SSH running, netiher of which come installed by default. Combined, they consume a little over 1MB of RAM and no CPU when they aren't doing anything, so they're pretty light. I can't see most users having many more network services running in a desktop environment (maybe NFS). If a system struggles with these services running, then it's going to struglle without them running. There are many more daemons running on the machine (not related to network services) consuming much more resource than the 1MB of network services. 

All of the daemons seem to be able to manage their memory footprint pretty well, so they consume virtually no resource when they're doing nothing.

In a server environment, you want the services always on.

inetd is primarily used for spawning services that are not network aware. The only one I can think of off the top of my head is SWAT.

Edit: Don't take my criticism of the idea personally. I'm not trying to have a go (just in-case it seems like that). I'm just trying to question the benefits of implementing something like this.

---

### Post by CrazyGuy123 on 2007-11-15
consider another use:-

The running of services that may NEVER be used.  Say for example it would be good to have a vnc server on all ubuntu desktop machines, but most ubuntu uses will never ever use it.  rather than have it waste ram all the time the system is running, and slowing down the boot time every time the system starts, it would be way better to only start it when it's needed for a friend to connect, which is only done once a year.

Say the vnc server takes 5 sec to start and uses 5 Meg of RAM.  in this case, which is better, 5 secs extra on boot time on every boot and 5Meg less ram all the time, or a 5 second delay on connection just once a year.

An even more optimized solution would be to have inetd analyse the frequency of use of different services and pre-load the commonly used ones.  That would allow the system to self-optimize, with no need to reduce performance to gain more functionality in the OS.  (so a new service could then be added, and it would have absolutely zero effect on system overhead unless it was frequently used)

---

### Post by CrazyGuy123 on 2007-11-15
One example of that case is a web server on an embedded router.  I bet a good deal of router web interfaces have NEVER been accessed in the years the user has had the router.  If manufacturers could use inetd or similar, they could reduce the amount of ram in the system and sell the router cheaper.

---

### Post by chrisccoulson on 2007-11-15
> **CrazyGuy123 said:**
> consider another use:-

The running of services that may NEVER be used.  Say for example it would be good to have a vnc server on all ubuntu desktop machines, but most ubuntu uses will never ever use it.  rather than have it waste ram all the time the system is running, and slowing down the boot time every time the system starts, it would be way better to only start it when it's needed for a friend to connect, which is only done once a year.

Services that are rarely used should *not* be enabled by default - period. Running services that are not needed is fairly irresponsible, and these services shouldn't be enabled on a default install (especially VNC).

> One example of that case is a web server on an embedded router. I bet a good deal of router web interfaces have NEVER been accessed in the years the user has had the router. If manufacturers could use inetd or similar, they could reduce the amount of ram in the system and sell the router cheaper.

In a typical embedded router which stores everything in some solid state device, where will it store the web interface when it's not running? It's still going to be stored somewhere in some solid-state memory device, which costs money - so where is the benefit? Okay, it might free up a few bytes of data memory, but the gain is negated by needing an extra service running - inetd.

---

### Post by CrazyGuy123 on 2007-11-15
The security issue of having always-running services like VNC should be dealt with seperately - a lot of people do it even now.

In the case of a router everything is stored compressed in FLASH, and when running it is ALSO stored in RAM.  not having to run the service all the time could enable leaving it only in flash until required.  Other examples in the case of a router is the UPnPd service, SNMP agent, telnet daemon, ssh, dynamic DNS updater, DHCP server, DNS server, L2TP server, PPTP server.

If a router used inetd for all those services then any of the services could be used without the reconfiguration needed to stop one service and start another when required, presuming there isn't sufficient RAM to run all the services simultaniously and still get good performance.

---

### Post by coolen on 2007-11-15
The point is, inetd *is* useful, and it would be nice if it were easier to configure.

---

### Post by slavik on 2007-11-15
If I am running apache, it better default to sit in RAM

If I need something that is a web server and uses RAM very little, I will either find another web server or write my own.

---

