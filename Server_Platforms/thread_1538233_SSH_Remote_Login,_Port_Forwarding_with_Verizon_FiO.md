---
title: "SSH Remote Login, Port Forwarding with Verizon FiOS"
date: 2010-07-24
forum: Server Platforms
---

### Post by C-- on 2010-07-24
Hey, I'm trying to get SSH remote login working on my web server. I can SSH over the LAN, but not over the Internet (in that case, trying to log in just hangs until timeout). I set up port forwarding on my FiOS router according to the official tutorial, and I know SSH can find my public IP, but for some reason it's not redirecting me to the private IP of my server (Ubuntu 10.4 Server edition). I can clearly see in my router settings that am forwarding all incoming traffic to my public IP on any more to my private IP on port 22, but it still won't let me in.

---

### Post by YesWeCan on 2010-07-24
Have you got a firewall set up on your server?
Otherwise, it's probably your router config.

---

