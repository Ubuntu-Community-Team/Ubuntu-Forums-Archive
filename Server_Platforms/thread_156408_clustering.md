---
title: "clustering"
date: 2006-04-07
forum: Server Platforms
---

### Post by newbie_jhay on 2006-04-07
hi guys, 

i just want to ask, can 2 desktop pc's running on ubuntu be clustered? and one more question, how many pc's can an ubuntu server handle when it is just running from a desktop pc with these basic specs:

pentium4 1.6 Gig
256 mb sdr
80 Gigs hdd

well, here's the case... i've been planning to setup an ubuntu server on a small office with about 30 computers. the server would be configured with both samba and apache. but the problem is that the only pc's available (for both ws and server) have the specs i've stated above.... 

because of this, i wanna know if clustering 2 of these pc's to act as server would be possible so it could handle the load. i also want to know how much load can a pc with the said specs handle. if the office would allow it, i'll be able to run a test next week but sadly, my test might only be limited to about 6 pc's - 5 ws and 1 server....

i really hope u guys could give me an idea regarding these things coz it will be my first time to do this stuff.... 

thanks a lot in advance!!!

---

### Post by amohanty on 2006-04-07
> pentium4 1.6 Gig
256 mb sdr
80 Gigs hdd

If you plan to use this as a server, I woudl suggest some more hdd space, but otherwise these will do just fine.

Also what do you mean by **cluster** and **handle the load**?
Do you plan to use something like an HA cluster with cluster management software?
What do you want to use these servers for, that you need to load balance the boxes - if its only as a file server and intranet server, why are you thinking about clustering?

AM

---

### Post by Scotland on 2006-04-09
[QUOTE=amohanty]If you plan to use this as a server, I woudl suggest some more hdd space, but otherwise these will do just fine.

Also what do you mean by **cluster** and **handle the load**?
Do you plan to use something like an HA cluster with cluster management software?
What do you want to use these servers for, that you need to load balance the boxes - if its only as a file server and intranet server, why are you thinking about clustering?

AM[/QUOTE]

He's most likely talking about failover clustering. e.g. one box idle waiting on the other failing.

For this solution though, shared storage would be required.

I am also looking at using our 'to be replaced' dell poweredge 6400's (fully redundant, clustered using windows 2000 advanced server) to set up a failover linux cluster as a mail server.

Anyone have any pointers for me ?

Dougie.

---

### Post by amohanty on 2006-04-10
I have used [HeartBeat]("http://linux-ha.org/HeartbeatProgram") in the past, and it has worked quite well for me in small configs. Not having used it in an enterprise env, I couldnt say how it would perform, if you are looking for real cluster as opposed to a failover solution. 

Also if its just a two system failover config that you want to setup, it would be easier to set up a low cost 'sniffer' that regularly pings the specified machines involved and eseentially port forwards to the primary box. In the event that the primary master dies, it simply reroutes all traffic to the secondary. You can also make it handle the syncing of the two boxes.

HTH
AM

---

### Post by Scotland on 2006-04-10
[QUOTE=amohanty]I have used [HeartBeat]("http://linux-ha.org/HeartbeatProgram") in the past, and it has worked quite well for me in small configs. Not having used it in an enterprise env, I couldnt say how it would perform, if you are looking for real cluster as opposed to a failover solution. 

Also if its just a two system failover config that you want to setup, it would be easier to set up a low cost 'sniffer' that regularly pings the specified machines involved and eseentially port forwards to the primary box. In the event that the primary master dies, it simply reroutes all traffic to the secondary. You can also make it handle the syncing of the two boxes.

HTH
AM[/QUOTE]

Thanks for your reply, I can't really devote time to this until my new servers arrive and in production but, the 'low cost' solution just pinging is not a satisfactory solution.

Just because you can ping the other machine does not mean that a specific app is still functioning. 

All serious clusters must monitor all resources, detect what's failed etc,

Heartbeat looks promising. As I said, I can't really devote time at the moment.

Regards,

Dougie.

---

### Post by amohanty on 2006-04-11
> Just because you can ping the other machine does not mean that a specific app is still functioning.

All serious clusters must monitor all resources, detect what's failed etc,


I agree, thats why I said "just a two system failover config" :) In case you want a more robust and truly HA solution I would suggest going with a commercial vendor, a list is available here:
[http://linux-ha.org/CommercialSoftware](http://linux-ha.org/CommercialSoftware)

I have used Tivoli a bit and the RH Cluster Suite a bit more than that, and they definitely provide a good bang for your buck. 

HTH
AM

---

