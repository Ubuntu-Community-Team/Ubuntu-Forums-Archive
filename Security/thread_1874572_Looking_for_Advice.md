---
title: "Looking for Advice"
date: 2011-11-03
forum: Security
---

### Post by Buckie_Bhoy on 2011-11-03
I'm after some thoughts, not sure if their is there something dubious running some where on my system?
 
I noticed the following from the logs in my router where 192.168.0.2 is the internal ip of my Ubuntu box, and 81.141.216.129 was my external IP at the time.

```

Wed, 2011-11-02 21:05:01 - TCP Packet -
Source:192.168.0.2,52476 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:05:02 - TCP Packet -
Source:192.168.0.2,52477 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:05:13 - TCP Packet -
Source:192.168.0.2,52476 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:05:14 - TCP Packet -
Source:192.168.0.2,52477 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:05:37 - TCP Packet -
Source:192.168.0.2,52476 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:05:38 - TCP Packet -
Source:192.168.0.2,52477 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:06:26 - TCP Packet -
Source:192.168.0.2,52476 Destination:81.141.216.129,80 -
[HTTP rule match]
Wed, 2011-11-02 21:06:26 - TCP Packet -
Source:192.168.0.2,52477 Destination:81.141.216.129,80 -
[HTTP rule match]

```

The desktop was locked, but with Firefox still running.  The HTTP rule in my router is to block all incoming traffic to port 80.

---

