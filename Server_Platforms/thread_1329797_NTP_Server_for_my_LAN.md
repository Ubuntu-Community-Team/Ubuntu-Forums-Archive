---
title: "NTP Server for my LAN"
date: 2009-11-17
forum: Server Platforms
---

### Post by ratcheer on 2009-11-17
I did a little server project, today. It may be almost trivial, but it is successful and I am proud of it. I have set up and configured an NTP (Time) server on my little Ubuntu host and am updating the clocks of all the other hosts in my house from it.

One detail was finding a good source for my time update. I did this by checking many Open Access NTP servers listed in ntp.org. I found one that consistently gives me sub-27 ms response time and placed it first in my server list. My other servers are the four us.pool.ntp.org pools.

The other detail I had to figure out was how to serve the time from my Ubuntu host to the rest of the nodes in my LAN. I ended up with the following line in my ntp.conf file:

restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap

The other nodes get < 1ms response time to my local time server.

Again, this may be simple stuff, but it is cool to me!

Tim

---

### Post by spikyjt on 2009-11-19
Not so trivial as you think. Its been on my todo list for ages, after a couple of failed attempts. Well done for doing the research. Its clearly the good source that is key. I feel like logging in to my servers from my phone now to sort it out!:D

---

