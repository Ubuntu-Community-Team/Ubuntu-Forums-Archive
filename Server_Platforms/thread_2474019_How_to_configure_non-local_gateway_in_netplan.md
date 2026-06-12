---
title: "How to configure non-local gateway in netplan"
date: 2022-04-20
forum: Server Platforms
---

### Post by Tacioandrade on 2022-04-20
Hello friends, I have a problem with netplan and I don't know how to deal with it! I have a dedicated server at OVH and I hired some extra IPs for my server, but instead of giving me an IP with a gateway in the same range, they gave me an IP where the gateway is in the range of my main IP.


For example, my server's main IP is 200.10.20.4 and its gateway is 200.10.20.254. When I requested 1 extra IP instead of a block with more IPs, they gave me an IP 179.29.30.8, but his gateway is not 179.29.30.254 but 200.10.20.254.


Manually to work I have to do the following: I configure the IP without the gateway and using the command "ip route add default via 200.10.20.254 dev eno1" for example.


The problem is that I have to do this execution manually after each reboot, otherwise it doesn't work, I tried to put it via crontab for it to run after restarting, but it didn't work!


If anyone knows a way to solve this, preferably using netplan, if not, through a gambiarra I would appreciate it.

---

### Post by Chuck Young on 2022-05-01
here is how to add persistent routes to netplan.

[https://linuxconfig.org/how-to-add-static-route-with-netplan-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-add-static-route-with-netplan-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by Tacioandrade on 2022-05-13
Thanks, you save me! ;-)

---

