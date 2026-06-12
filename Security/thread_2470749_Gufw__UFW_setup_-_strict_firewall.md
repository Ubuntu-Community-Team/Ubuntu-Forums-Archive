---
title: "Gufw / UFW setup - strict firewall"
date: 2022-01-09
forum: Security
---

### Post by julian.b on 2022-01-09
Hi all,

I would like to set up a strict firewall for an Ubuntu-based machine that is just used for web browsing. I would appreciate if some of the forum gurus could review the setup below. I created the rules in GUFW and provided below the output from "sudo ufw status verbose". I also reorganized the output for easy reference and added a few questions. FYI, I have a dynamic IPv6 address.

```

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
Web browsing rules. Do I need all 4 rules below if I only have the IPv6 address?
80/tcp                     ALLOW OUT   Anywhere     
80/tcp (v6)                ALLOW OUT   Anywhere (v6) 
443/tcp                    ALLOW OUT   Anywhere     
443/tcp (v6)               ALLOW OUT   Anywhere (v6)

DNS rules. Do I need both rules below if I only have the IPv6 address?
53                         ALLOW OUT   Anywhere     
53 (v6)                    ALLOW OUT   Anywhere (v6)

DHCP rules. Should I delete or modify any of the 2 rules below (for instance by adding the v6 or v4 equivalents)?
67:68/udp                  ALLOW OUT   Anywhere
546:547/udp (v6)           ALLOW OUT   Anywhere (v6)

Ntpd rules. Do I need this for time synchronization in Ubuntu? Is there a reason why I should/shouldn't keep this?
123/udp                    ALLOW OUT   Anywhere                   
123/udp (v6)               ALLOW OUT   Anywhere (v6) 

Are there any other ports I should open that are crucial to the operation of Ubuntu?

```

---

