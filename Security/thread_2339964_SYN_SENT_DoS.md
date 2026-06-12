---
title: "SYN_SENT DoS?"
date: 2016-10-14
forum: Security
---

### Post by Elxyer on 2016-10-14
Hello everyone,

I've been having some bad network activity on my Ubuntu server.
I've tried firewall IP blocking, but my router is still showing flooding on my server.
Does anyone know what else to try to get to the bottom of this?

It's all coming from the same IP address 191.96.249.75
[ATTACH=CONFIG]271605[/ATTACH]

Thanks!

---

### Post by kevdog on 2016-10-14
Your firewall is going to protect the packet getting through, but its not going to stop the constant barrage of attacks.  I'd contact your IP service provider.

---

### Post by Elxyer on 2016-10-14
I see, so that's why I'm still seeing his IP...

Is that something ISPs can usually do? I have Comcast...

---

### Post by kevdog on 2016-10-15
I'd just see if you can get a new IP address assigned to you -- probably the easiest way.

---

### Post by Elxyer on 2016-10-15
Yah, they said they can't do anything about it and I should see if i can block it from my router.
I have a DD-WRT router and I tried setting up IP blocking, but I wasn't seeing a difference.
I may have been setting it up incorrectly though...

---

