---
title: "Randomized Domains in Chrome on Ubuntu"
date: 2020-06-12
forum: Security
---

### Post by philip14 on 2020-06-12
[COLOR=#000000]I found today what I thought was a misbehavior on Ubuntu when I connect to a new network interface. Turns out the culprit was Chrome.[/COLOR]

[COLOR=#000000]In an effort to saturate this topic with more sources, here is a solution to what appears to be a Chrome security issue but is actually a feature. Apparently it is already known, but was not already known to me.[/COLOR]

[COLOR=#000000]I had all services off and connected my NIC, capturing traffic for a VLAN compromise investigation, and instead of what I wanted to see, I kept seeing random domains that came back with a real IP address.[/COLOR]



Host: kxzzskctf


Location: [http://localhost](http://localhost)
Expires: Fri, 12 Jun 2020 19:26:09 GMT
Cache-Control: no-cache


[COLOR=#000000]It became even more annoying when that connection was clearly operational but was not appearing on netstat.[/COLOR]


[COLOR=#000000]COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME[/COLOR]
[COLOR=#000000]chrome 13467 user 41u IPv4 261742 0t0 TCP host:55652->198.105.244.23:http (CLOSE_WAIT)[/COLOR]
[COLOR=#000000]chrome 13467 user 43u IPv4 261743 0t0 TCP host:55654->198.105.244.23:http (CLOSE_WAIT)[/COLOR]

[URL="https://mikewest.org/2012/02/chrome-connects-to-three-random-domains-at-startup/"]
https://mikewest.org/2012/02/chrome-connects-to-three-random-domains-at-startup/[/URL]

[COLOR=#000000]Apparently it is on purpose. Hopefully this will help someone else[/COLOR]

---

### Post by EuclideanCoffee on 2020-06-13
Interesting. Is this an fyi or a security concern of yours?

---

