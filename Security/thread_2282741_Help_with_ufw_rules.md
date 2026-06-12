---
title: "Help with ufw rules"
date: 2015-06-16
forum: Security
---

### Post by vw16v on 2015-06-16
Hi, I'm trying to get my security setup on my new 10.0.16.x subnet and having "issues". I used to be really good at adding specific rules to ufw to allow specific machines (IP Ranges) and ports to connect.

However, I'm having problems adding the rules and need help. This is how my old subnet on 10.16.0.x was setup and the rules worked great and were tight.
```
Status: active

To                         Action      From
--                         ------      ----
10.16.0.48/28 135/tcp      ALLOW       10.16.0.48/28
10.16.0.48/28 139/tcp      ALLOW       10.16.0.48/28
10.16.0.48/28 445/tcp      ALLOW       10.16.0.48/28
10.16.0.48/28 137/udp      ALLOW       10.16.0.48/28
10.16.0.48/28 138/udp      ALLOW       10.16.0.48/28
10.16.0.48/28 22/tcp     ALLOW       10.16.0.48/28
10.16.0.48/28 3300/tcp     ALLOW       10.16.0.48/28
22                     ALLOW       10.0.16.0/28             < BAD RULES
22/tcp                   ALLOW       10.0.16.0/28        < BAD RULES
22/udp                   ALLOW       10.0.16.0/28        < BAD RULES
Anywhere                   ALLOW       10.16.0.0/28 22/tcp    < BAD RULES


```

I would like to remove these rules I added via cli>
22                     ALLOW       10.0.16.0/28             < BAD RULES
22/tcp                   ALLOW       10.0.16.0/28        < BAD RULES
22/udp                   ALLOW       10.0.16.0/28        < BAD RULES
Anywhere                   ALLOW       10.16.0.0/28 2112/tcp    < BAD RULES

And I would like to add the rules correctly to how I had them setup when I was using a 10.16.0.x subnet. Thanks for any help!

EDIT, I found out how to easily delete my bogus rules using the sudo ufw status numbered command. This allowed me to delete the BAD Entries. I appreciate any insight into how I added these specific rules before. I have to step away from the computer to ease my mind.

Hey guys, I think I got it now. I typo'd the subnet (DOH!)
It's slightly different than my old rules I created on 10.16.0.49+ subnet but this rules works>
22                       ALLOW       10.16.0.0/28

Need to try and keep my linux skills fresh.
Nevermind linux folks! I got my system back on lockdown. Peace, Love & Linux.

---

