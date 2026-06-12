---
title: "Why Tor Traffic If I'm Not Doing Anything?"
date: 2007-11-05
forum: Server Platforms
---

### Post by Ubuntist on 2007-11-05
I sometimes often with Tor and Privoxy.  Having a monthly bandwidth limit, I do not configure my machine to be a Tor proxy.

Whenever the Tor proxy is switched on there is a certain amount of traffic between my machine and the internet.  This happens even if I'm not using Tor (i.e., my browser is temporarily not pointing to Tor)  and I'm not doing anything on the internet (no downloads, no page loads, no page refreshes).  The traffic continues until I exit Tor.

What causes this traffic?  Is it something I should worry about?

---

### Post by inphektion on 2007-11-05
I would assume tor is talking to the servers it'll be using to anonymize your connection.  Checking if they are up, response times, maybe chosing the best ones to use.  I wouldn't worry but if you still are then run wireshark on the line and see what it is doing exactly.

---

### Post by civic_si on 2007-11-05
you can also just run netstat and see what open tcp connections you have.

---

