---
title: "Able to ping one guest, but not its clone!?"
date: 2010-05-18
forum: Virtualisation
---

### Post by svaens on 2010-05-18
Hi all, 

I have this strange problem. 

I had 1 guest windows XP installation. 
I made a clone of its two hard-drives, and setup a new machine.

Next, I changed both from NAT networks to bridge networks (i'm using VirtualBox 3.1.8 r61349 by the way)

The problem is that I can ping the original machine, but I can't ping the clone. Both machines (original and clone) can ping out, and the clone can also ping the original. 

Any idea why this might be the case ? I have checked that the MAC addresses are different ... I changed the 'computer name' of hte clone from 'My Computer' to be different than the original .... 

Thanks for any insight.

---

### Post by dcstar on 2010-05-18
> **svaens said:**
> Hi all, 

I have this strange problem. 

I had 1 guest windows XP installation. 
I made a clone of its two hard-drives, and setup a new machine.

Next, I changed both from NAT networks to bridge networks (i'm using VirtualBox 3.1.8 r61349 by the way)

The problem is that I can ping the original machine, but I can't ping the clone. Both machines (original and clone) can ping out, and the clone can also ping the original. 

Any idea why this might be the case ? I have checked that the MAC addresses are different ... I changed the 'computer name' of hte clone from 'My Computer' to be different than the original .... 

Thanks for any insight.

```
arp -a
```

---

### Post by svaens on 2010-05-18
Hi and thanks for the reply;

Unfortunately I am not knowledgable enough to really take advantage of your assistance so far.

In order to try to find out, I ran this command on both the linux host, and the two windows guests .....  but it didn't tell me much.

host
```
sean@svUbuntuX2:~$ arp -a
? (192.168.0.4) at 08:00:27:5e:51:af [ether] on wlan0
home.gateway (192.168.0.1) at 00:04:ed:ad:14:15 [ether] on wlan0
sean@svUbuntuX2:~$ 

```

guest 1 (able to ping this machine)

No ARP entries found

guest 2 (not able to ping this machine)

No ARP entries found

---

### Post by svaens on 2010-05-19
Update:

ahh .... you didnt mean 'check the bloody windows firewall' by any chance, did you ? 

because that is what fixed it. Turn it off, .... now I can ping it. 

thanks!

---

### Post by dcstar on 2010-05-25
> **svaens said:**
> Update:

ahh .... you didnt mean 'check the bloody windows firewall' by any chance, did you ? 

because that is what fixed it. Turn it off, .... now I can ping it. 

thanks!

Then please mark the thread as solved.

---

