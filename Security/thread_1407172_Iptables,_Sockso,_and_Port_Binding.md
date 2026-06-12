---
title: "Iptables, Sockso, and Port Binding"
date: 2010-02-14
forum: Security
---

### Post by sablefoxx on 2010-02-14
So I want to run a Sockso server (streams .mp3s) so I can listen to my music on my netbook/any computer with internet.  However my school will only allow traffic to go out on port 80/21 so I cannot connect to my server via something like myurl.dyndns.org:8081 

Now it is my understanding that only root services can bind to ports below 1023, so now I could run Sockso as root on port 80 but that strikes me as a rather insecure solution.  I instead created an iptables rule which redirects tcp traffic on port 80 to 8081 which works fine, but the downside is that iptables doesn't save anything on reboot.  I've been Google'in to no avail, so I thought I'd ask, if anyone know how to do the following;

- A way to Sockso on port 80, without being root
- A way to run "iptables-restore myconfig" as root on boot
- A better solution?

This is the iptables command I've been using;
*iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port 8081*

Thx for the help/suggestions :D   -- Ubuntu 9.10

---

### Post by bodhi.zazen on 2010-02-15
Thread closed. We do not support circumventing private networks (school / office ).

You need to bring your issues to your (school) IT Department.

---

