---
title: "susceptible to ping flood."
date: 2009-11-20
forum: Security
---

### Post by MCBTunes on 2009-11-20
I am doing a class project where I am recruiting a bunch of machines on a network to ping flood a target (also on the network) to take the target down using the ping command in the Terminal. Right now the target is my laptop, running Ubuntu 8.10. How many computers do you figure I would need assuming I set the ping interval low, to cause my laptop to become non-functional? Is there any setting I can alter (temporarily) to make it easier for the attack to succeed?

Keep in mind I don't want to do any permanent damage to my laptop :). There is no permanent damage from being pinged to death is there? 

I have 20-30 computers available but if I could pull it off with 10-15 or so machines that would be better.

---

### Post by MCBTunes on 2009-11-20
I suppose this question may have been better in the development forum. If someone in power agrees feel free to move it :).

---

### Post by Yoann Juet on 2009-11-20
> **MCBTunes said:**
> How many computers do you figure I would need assuming I set the ping interval low, to cause my laptop to become non-functional? Is there any setting I can alter (temporarily) to make it easier for the attack to succeed?

With recent tcp/ip stacks : no chance with ping, nor hping ! Rather try a broadcast or multicast storm to overload the switch on which are connected those computers.

---

