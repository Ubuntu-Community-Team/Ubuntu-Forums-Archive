---
title: "Raid 0 or not"
date: 2008-06-07
forum: The Cafe
---

### Post by Laxton14 on 2008-06-07
I recently ordered new laptop from gateway, I initially ordered the p172x fx with the raid 0 configuration but it will take me a few weeks to get that computer,  so I switched my order to the non raid configured one (both are the exact same hardware specs and everything, just in one raid is configured and in the other its not)  i was wondering... 

1) how beneficial is the raid set up

2) how hard would it be to set up the raid 0 configuration myself 

and 3) do you recommend... A-waiting for the other come in stock       
                           B-getting the non raid comp and setting up myself
                           C-getting non raid and just using no raid config

                                                      Thanks, Nathan
heres the site 
[http://www.gateway.com/systems/series/529598006.php](http://www.gateway.com/systems/series/529598006.php)

oh yeah.. and another thing.. both are same price.

---

### Post by saulgoode on 2008-06-07
If you will be running only Linux, get the non-RAID and use software-based RAID. If dual-booting and you want to have RAID, hardware-based is, to my knowledge, your only option.

---

### Post by LaRoza on 2008-06-07
> **Laxton14 said:**
> 

1) how beneficial is the raid set up

2) how hard would it be to set up the raid 0 configuration myself 

and 3) do you recommend... A-waiting for the other come in stock       
                           B-getting the non raid comp and setting up myself
                           C-getting non raid and just using no raid config


0. Not very, it is risky
1. Not hard, probably, but you'd have to read the documentation
3. Getting non raid and no using raid 0.

RAID 0 is very risk, it doubles the risk of data loss.

---

### Post by toupeiro on 2008-06-07
> **LaRoza said:**
> 0. Not very, it is risky
1. Not hard, probably, but you'd have to read the documentation
3. Getting non raid and no using raid 0.

RAID 0 is very risk, it doubles the risk of data loss.

+1

Raid 0 is for speed, speed, speed.  The more disks in your raid 0, the better your speed is. You are striping across a set of disks which means multiple drive heads can be used to serve your data instead of one.  There is no fault tolerance or redundancy in raid 0.  If you want fault tolerance with the benefits of raid 0, I would do raid 0+1, but its more costly from a hard drive perspective.  If you have a hardware controller to take care of your raid array, never opt for software RAID.  let your controllers handle that overhead, thats what they are there for.  I will only use software raid if I want to do raid configurations more sophisticated than what my hardware controller can allow, e.g. raid 5.  If its a server, I'll spend the money on a controller that can handle raid 5.

Maybe its just me, but raid in a laptop seems .. oh I dont know.. overkill?  If it were me though, and I absolutely depended on my laptop for every day computing, I would do a raid 1 (mirroring).  If you have a laptop that supports RAID, I doubt its a slow-poke, so you probably aren't screaming for performance increases.  Your data is most likely much more important.

The only time I ever see raid 0 used anymore is for very large SAN/NAS devices where they take multiple raid 5 or 6 luns and throw a raid 0 over all of them.  sometimes referred to as raid 50 or raid 60.

---

