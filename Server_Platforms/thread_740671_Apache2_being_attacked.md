---
title: "Apache2 being attacked"
date: 2008-03-31
forum: Server Platforms
---

### Post by asellus on 2008-03-31
Get ready for a pretty lengthy post...

In the beginning, the server was running 6.06LTS on a naked connection.  It hosted apache2, CS:S, and TF2.

All was fine and dandy until I noticed that the apache2 server would stop responding periodically.  I noticed that the maxclients setting was being hit 1-2 minutes after apache loading.  I did a little digging, and with a helpful tool called tcptrack, I noticed that I was being HAMMERED.  Example:

```
Client                Server                State        Idle A Speed
 124.43.40.92:6683     x:80       RESET        0s     0 B/s
 124.43.40.92:6752     x:80       RESET        0s     0 B/s
 124.43.40.92:6753     x:80       RESET        0s     0 B/s
 124.43.40.92:6743     x:80       RESET        0s     0 B/s
 124.43.40.92:6737     x:80       RESET        0s     0 B/s
 124.43.40.92:6740     x:80       RESET        0s     0 B/s
 124.43.40.92:6741     x:80       RESET        0s     0 B/s
 124.43.40.92:6742     x:80       RESET        0s     0 B/s
 124.43.40.92:6729     x:80       RESET        1s     0 B/s
 124.43.40.92:6727     x:80       RESET        1s     0 B/s
 124.43.40.92:6722     x:80       RESET        1s     0 B/s
 124.43.40.92:6749     x:80       RESET        1s     0 B/s
 124.43.40.92:6723     x:80       RESET        1s     0 B/s
 124.43.40.92:6721     x:80       RESET        1s     0 B/s
 124.43.40.92:6730     x:80       RESET        1s     0 B/s
 124.43.40.92:6726     x:80       RESET        1s     0 B/s
```

Take care to notice the seemingly sequential client-side port attacking port 80.  In this example however, apache is stopped, hence the RESET state.

Having noticed all these connections (which at the time were ESTABLISHED) I set to it to figure out how to stop them.  Very simple!

iptables -A INPUT -p tcp -s 124.43.0.0/16 --dport 80 -j REJECT

That worked great!  I made a small list of 'problem countries' and blacklisted them.  My webserver is mainly for people around Minnesota, anyways.  No biggie, all is well.

Fast forward a month or two.  I upgrade to 7.10.  A week passes, and I noticed that there's an average of 250-1000 k/s going through my server (again, noticed with tcptrack).  The breakdown of the connections appeared to be on port 80 again.  All the connections were ESTABLISHED at this point, not SYN_SENT (which is how they appeared when iptables was working).

I thought oh crap, my iptables entries were destroyed.  I checked.. they weren't.  Reapplied them to be safe, checked tcptrack, and noticed the connections were still being accepted and sucking up a ton of bandwidth.

That's it, I thought.  Stopped apache, killed the straggling processes, removed --dport 80, -p tcp, and switched -j REJECT to -j DROP on all my iptables scripts, and re-applied them.  Moment of truth.... I fired up apache.

No go.  They were listed as "RESET" but STILL SUCKING UP BANDWIDTH!!  Now, is this an Ubuntu 7.10 thing, or have I missed something stupid like iptables --activate ?

Help!


Cliff notes:

- server hosting apache2 on 7.10
- attacked by many IP's on sequential client ports, all directed to 80
- despite iptables DROP on these hosts, they suck up lots of bandwidth when apache is running

---

### Post by asellus on 2008-03-31
And now the attacks have completely ceased, with the trickle now and then staying at SYN-SENT as they used to.  What the hell...

I've started up apache2 again and haven't had an issue i the last 10 min.

---

### Post by asellus on 2008-04-01
Christ this is confusing.  Another question, same topic.

More and more I'm seeing these random IP's sucking up a TON of bandwidth from placed like Israel, Vietnam, etc...

Today I caught one going about a meg a second from host port 80 (client port like 4813 or something obscure).  I figured that if this was a valid transfer there would be a corresponding entry in my access logs -- there was nothing related to the IP.

Furthermore, there isn't a single file hosted on the webserver that is large enough to merit this amount of bandwidth being used for the length of time it would be used, so whether or not access.log is written with the entry before OR after the request was fulfilled is irrelevent.

Now I at least know the data is outbound from my server, since the IP that was using about a meg a second is a subcriber for the company I work for -- I pulled up their modem and watched the data streaming in, rather than out.

Here's the question... what exactly is Apache accepting a request to that causes this inordinate amount of bandwidth to be used without a single entry in the access logs?  Or is there a more verbose setting I could use with the logs that would assist in figuring this out?

Thanks,
-Ian

---

### Post by mrsteveman1 on 2008-04-02
It was my impression that normally the access log only shows valid HTTP requests etc, and perhaps won't show IP traffic that doesn't rise up to layer 4 or above of the network stack, EG stuff the kernel doesn't pass on. Error log might show other stuff but i doubt it.

You can definitely set the access log and error log to be more verbose, which might show you a lot more.

Also, when these specific attacks happen, i HIGHLY recommend you capture all of the IP traffic involved by using ettercap or wireshark, either on the server itself or on another machine. This way you have detailed evidence of what was being sent and why, and what parts of the network stack were involved. Wireshark specifically will decode a lot of the traffic and show you want was going on.

It may also be worth it for you to look into an IPS system on your gateway, Astaro makes very good devices as does barracuda and a few others.

---

### Post by Deathrend on 2008-04-02
I personally use an ASA5505 for my home network, it does an outstanding job for figuring out what should, and what shouldn't be entering.  We use an ASA5520 at work, which works outstanding as well.

Barracuda makes outstanding products, however they're a bit pricy if you're looking for smaller network/home network protection.

The Juniper NetScreen series are also good for small network protection.

---

