---
title: "Checking who's using"
date: 2009-04-16
forum: Security
---

### Post by happyhacker on 2009-04-16
I have just installed a wireless router used just to allow wireless access to the internet. This works fine. It connects directly into our switch. I have configured WPA PSK. Because staff are not very security aware (OK, OK!), I will assume someone will get the pass phrase and log in from the car park. The Ubuntu server is not in the loop here but anyone could of course see the network. The network is just a simple workgroup and I have no plans to change that.

Is there a way of restricting wireless access to the internet only?

How can I best monitor and control 3rd party access in this way?

---

### Post by Scubdup on 2009-04-16
I 'd like to see some possible solutions too. Naively hadn't realised how insecure WEP was so as soon as I get home I'm switching to WPA but I'd love to be able to monitor or check on the history of machines that have accessed the network already.

---

### Post by lensman3 on 2009-04-16
Set the wireless part of the router to have its own IP range.  Setup the wire side of the router to have its own IP range. Forward both ranges to a common default gateway (the Internet side of the router).  That way the router handles two IP ranges.  Don't set up a forward from one IP range to the other one.  

Now that I have said that, I don't think inexpensive routers are that smart.  They can't handle two IP ranges (and subnets).

---

