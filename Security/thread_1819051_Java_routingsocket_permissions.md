---
title: "Java routing/socket permissions?"
date: 2011-08-05
forum: Security
---

### Post by hoink on 2011-08-05
I'm using libshout-java in my java application to stream mp3/ogg to an icecast/shoutcast server.

It connects, but only as long as the ice/shoutcast server is 1) on localhost (on my Ubuntu development machine) or 2) my local private 10...* network.

But when I point the libshout-java code to an internet address, I get a socket error -4 (a shout exception, not a java exception). This failure occurs when running the java code from Eclipse or from the command line.

I've confirmed that other ice/shoutcast streamers running on my Ubuntu development machine can successfully connect to ice/shoutcast internet IPs. But java can't.

Additional detail: the Ubuntu machine is "multi-homed", I guess: it connects to the internet via a wi-fi connection to my router (192...*), and then shares that connection with an ethernet-connected PC connected on a private network (10...*).

I'm trying to figure out if this is security or networking issue.  (The Ubuntu development machine is set as the DMZ on the router, ie, it's not likely a port-forwarding issue, especially given that other non-java streamers can connect.)

---

