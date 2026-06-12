---
title: "Am I getting Hacked? Can I stop it? Connection every 2 seconds!"
date: 2009-07-23
forum: Security
---

### Post by Mac10 on 2009-07-23
Hello,

I'm a new user to Ubuntu, lovin it so far. All of a sudden (last 3-4 days) I've been getting a HUGE amount of attempted? connections reporting in Firestarter. I've been whois-ing as many of the IPs as I can, but they all are from different areas (tonight anyway). Last night it was all from .cn domains, sending me some SHOUTcast port 8000 thing. Can anyone tell me from the firestarter logs what might be going on? Are they trying to crack me or what? I will log in, connect the cat5, and Firestarter immediately goes nuts! Is there a way to set up an automatic echo of any traffic not on port 80 (e.g. send that sh** back lol)? Any help would be great.
Here's a SMALL sample (screen shot). This kind of traffic goes on for days, usually the same 1-4 ports. Sorry about the pic size.

Thanks,

JamesMac10

---

### Post by m4tic on 2009-07-23
i doubt it someone specifically targeted you. anyway i dont see any problem there so dont worry

---

### Post by Grenage on 2009-07-23
It's not uncommon for this to happen, automated systems constantly scan designated ranges.  It will go away, come back, go away etc. etc.

---

### Post by Mac10 on 2009-07-23
Thanks for the repies guys. I was using a wireless router until a couple of days ago, you think maybe this was going on the entire time but it never got to firestarter because of the router? Now I'm just on a switched cat5.

---

### Post by Grenage on 2009-07-23
If you're forwarding ports, it doesn't matter what the medium is, Physical or Wireless.

---

### Post by Kazade on 2009-07-23
> **Mac10 said:**
> Thanks for the repies guys. I was using a wireless router until a couple of days ago, you think maybe this was going on the entire time but it never got to firestarter because of the router? Now I'm just on a switched cat5.

A router is essentially a firewall, unless you are forwarding ports any external requests won't make it through to your PC. Before, the router was taking and blocking these requests. Now that you don't have a router your PC is unshielded from the outside world which is why Firestarter is blocking them instead.

---

### Post by Mac10 on 2009-07-23
Aahh.. Exactly what I meant Kazade. Thanks for clearing that up.

---

