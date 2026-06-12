---
title: "udp activity on port 5353 and 32678 and port 631 Listening"
date: 2008-03-04
forum: Security Discussions
---

### Post by openheart on 2008-03-04
Hey all.. big newbie here just getting used to Linux. I come from a windows paranoid past and had a few question I was hoping for some help on!

When I perform a netstat I get the following results

Protocol     IP Source       Port/Sevice          State
tcp            127.0.0.1          631                  LISTEN
udp              0.0.0.0          32768
udp              0.0.0.0          5353

now since I am not aware of anything other than my open browser (which to me would suggest port 80 why would these ports be open and one be in a state of listening...

Also when I perform a port scan on myself I sometimes see very high port numbers opening and closing. sometimes they change but almost always disappear immediately. Looking at these things can anyone suggest any way that I can investigate these things further?

How should I proceed? Thank in advance and...

UBUNTU ROCKS! (Hicup)

---

### Post by The Cog on 2008-03-04
**sudo netstat -plantu**
will reveal that 631 is the cups printer spooler deamon. In your case, it is only listening on the loopback address so it's not reachable across the network by other computers. In mine, I'be enabled remote printing so it's listening on 0.0.0.0 instead.

The two UDP ports are avahi-daemon which is some kind of service advertisement and location service I think. This daemon can be disabled from System->Administration->Services.

---

### Post by openheart on 2008-03-04
Thank you so much for explaining this to me. I can follow you explanation and you have allayed my fears. How about this one..

every time I do a port scan on myself I come up with open ports but these ports are all very high numbered and change everytime I do the port scan. In each case the state of the port is listed as open and the service is always listed as unknown here are some examples

Port State Service
39320 open unknown
57021 open unknown
50137 open unknown
45570 open unknown
47121 open unknown


any ideas? sometimes when I do the scan there are none.. Should I be worried about THIS?

---

### Post by The Cog on 2008-03-05
**sudo netstat -plantu**
will tell you the process name that's listening.

---

