---
title: "Only my phone is blocked on vps"
date: 2017-12-08
forum: Server Platforms
---

### Post by neon88com on 2017-12-08
Hi i have strange situation.
I cannot access any of my website on VPS but only from cellular. 
If I'm connected to WiFi everything is ok.

system: Ubuntu 16.04 Server (64 bits)


**ufw:**


> sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22/tcp (OpenSSH)           ALLOW IN    Anywhere
80,443/tcp (Apache Full)   ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
2200                       ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
Anywhere                   ALLOW IN    94.254.128.174
22/tcp (OpenSSH (v6))      ALLOW IN    Anywhere (v6)
80,443/tcp (Apache Full (v6)) ALLOW IN    Anywhere (v6)
22 (v6)                    ALLOW IN    Anywhere (v6)
2200 (v6)                  ALLOW IN    Anywhere (v6)
80/tcp (v6)                ALLOW IN    Anywhere (v6)
443/tcp (v6)               ALLOW IN    Anywhere (v6)
80 (v6)                    ALLOW IN    Anywhere (v6)

**iptables:**
sudo iptables -L INPUT -v -n
Chain INPUT (policy DROP 151 packets, 8734 bytes)
 pkts bytes target     prot opt in     out     source               destination
91964 7673K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0         
91964 7673K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 1570 89925 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 1503 86453 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0          
 1503 86453 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 1503 86453 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0

---

### Post by volkswagner on 2017-12-10
Where is your VPS located? If it's behind your firewall/router you'll have to open/forward ports.

If it's at a hosting provider, perhaps they have a firewall allowing only your public IP from network you used during setup.

I'm guessing no other users can access from outside your home network as well.

---

