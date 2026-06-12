---
title: "why does my computer ping my router on its own?"
date: 2017-01-02
forum: Security
---

### Post by sgian on 2017-01-02
I run snort on a desktop that is also running a minecraft server we use on a LAN.  I noticed that around 10 PM last night when no one was on that pc, the pc pinged the router 23 times.  I'm the only one in the network that knows how to ping, or would even bother learning to ping.  Why would the pc ping the router on its own?

Specs:
Ubuntu 16.04 with current updates, running snort/snorby and a minecraft server.  Nothing else running.  Openbox installed but I had Unity loaded at the time. The router is a belkin with the most current update, which is from a year or two ago.

---

### Post by Doug S on 2017-01-02
Could it be the minecraft server itself doing the pings? Perhaps as a latency check?

---

### Post by sgian on 2017-01-02
I am not sure, but wouldn't the minecraft server be pinging throughout the day?  This was all between 10:03 and 10:10 PM my time last night.  The only other activity logged in the last 24 hours was sending data to Canonical, most likely to check for updates.  (I have already suppressed 5 likely false positive types of events so it is a lot quieter now).

---

