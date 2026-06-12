---
title: "HA with Keepalived"
date: 2015-05-28
forum: Server Platforms
---

### Post by biki2 on 2015-05-28
Hello guys,
Hope you are doing great!!
Right now I'm using keepalived daemon in order to ensure a Load Balancing function between my two servers.
First  of all, I tried using the famous "Round-Robin Scheduling" algorithm and  it worked well, but unfortunately I don't believe that algo could  resolve my problem, in fact, I have 2 servers and one VIP, and let's say  for example I want one specific client (with a unique IP address) to  always connect to one specific server, and in general the clients'  requests will be distributed on these two servers using the "RR"  algorithm, do you know how I could manage to do this?
Thank you in advance.

---

### Post by etescartz on 2015-05-28
Install Heartbeat or High Availability daemon on both servers. It sets up secondary shared IP address which acts a second network interface. 

So you chose which server is a master, and which is the secondary or backup server. . That way each has it's own unique IP address. The Heartbeat deamon generates a secondary network adapter with a unique IP address to the master server and keeps in sync with the backup server.

If the master server goes offline or is unreachable because of power/connectivity/whatever failure.. then the heartbeat daemon tells the backup server to take over the shared IP address and service is resumed.

If the master comes back online he takes over the shared IP address like nothing happened.

That way you can setup services to point to the shared IP address and your VIP the real IP address of the particular server you want him/her to access.

Details like IP addresses and sync/timeout durations are all customizable.

Good luck!

---

