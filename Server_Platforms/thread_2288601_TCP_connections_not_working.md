---
title: "TCP connections not working"
date: 2015-07-28
forum: Server Platforms
---

### Post by lorenzo-milesi on 2015-07-28
Hi.
I've a VM which behaves strangely on the network.


[LIST=1]
[*]ping to gateway *works*
[*]ping to 8.8.8.8 *works*
[*]traceroute to 8.8.8.8 *works*
[*]dig [www.google.com](www.google.com) *works*
[*]host [www.google.com](www.google.com) *works*
[*]telnet 1.2.3.4 25 *works*
[*]w3m [http://www.google.com](http://www.google.com) **DOESN'T WORK**, remains stuck on "opening socket"
[/LIST]

It looks to me there's some kind of problem from commands to access DNS or something like that.
What could be? What can I check? 
thanks

---

### Post by houstonbofh on 2015-07-28
You are still testing 2 things at once.  Ping [www.google.com](www.google.com) to get the IP address for google.  Then w3m to that IP address.  Also try to telnet to that address on port 80.  It could be someone just blocking web traffic.

---

### Post by lorenzo-milesi on 2015-07-29
[LIST]
[*]ping [www.google.it](www.google.it) does **not **work
[*]telnet 173.194.116.17 80 works (as it does for port 25)
[*]w3m [http://173.194.116.17](http://173.194.116.17) also works
[/LIST]

---

### Post by houstonbofh on 2015-08-14
So you do not have name resolution.  Check your DNS settings and connectivity.

---

