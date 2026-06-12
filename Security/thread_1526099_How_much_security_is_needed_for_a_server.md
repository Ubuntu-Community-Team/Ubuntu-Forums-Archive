---
title: "How much security is needed for a server?"
date: 2010-07-07
forum: Security
---

### Post by redfox1160 on 2010-07-07
I have an Ubuntu 10.04 server running in my basement. I don't really know a lot about servers, and I was wondering if I need to install any security on it. Thanks.

---

### Post by cariboo on 2010-07-07
What do you use the server for?

---

### Post by amauk on 2010-07-07
if you have any services open to the world (SSH, FTP, etc.) that can be used to alter your files or server setup
Then it's a good idea to restrict who can connect

you will have login credentials on all such services
but this does not stop people trying (and possibly succeeding) in guessing or brute-forcing passwords

If you do have such services open to the world
then configuring your firewall to only allow certain IPs through is the best way to go

If you do not wish to be so strict (say you want to maintain access to your server via SSH from arbitrary locations), then something like denyhosts or fail2ban is good

These are daemons that run on your server, monitoring the /var/log/auth.log log-file, and if they detect a possible break-in attempt, will ban the IP

---

### Post by redfox1160 on 2010-07-07
> **cariboo907 said:**
> What do you use the server for?

I was going to use it as an HTTP server, but Verizon blocks ports 80 and 8080; so I'm using it as a home media server.

> if you have any services open to the world (SSH, FTP, etc.) that can be used to alter your files or server setup
Then it's a good idea to restrict who can connect

you will have login credentials on all such services
but this does not stop people trying (and possibly succeeding) in guessing or brute-forcing passwords

If you do have such services open to the world
then configuring your firewall to only allow certain IPs through is the best way to go

If you do not wish to be so strict (say you want to maintain access to your server via SSH from arbitrary locations), then something like denyhosts or fail2ban is good

These are daemons that run on your server, monitoring the /var/log/auth.log log-file, and if they detect a possible break-in attempt, will ban the IP 

I'll look into denyhosts or fail2ban, even though I probably don't need them.

---

