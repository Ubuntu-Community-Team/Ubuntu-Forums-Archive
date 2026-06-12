---
title: "DNS issues. I can no longer SSH and Netplan DNS has no effect?"
date: 2019-03-10
forum: Server Platforms
---

### Post by dev18 on 2019-03-10
Greetings,
     I have a Ubuntu 18.04 Server that I was building a website on. The website kept dropping and I found the culprit was an unresponsive hop in the route for the server. (traceroute/tracert) It was an ISP DNS server.... But when I setup the server just a day ago, I specified nameservers in the .yaml file for netplan. I tried/tested it and it was applied because I did notice the static IP was assigned. But apparently the DNS did not.

    Without thinking, I edited /etc/resolv.conf, added my nameservers and commented out the ISP associated entries. I restarted the network-manager service and got an error that the hostname couldn't be resolved. So I edited and reverted /etc/resolv.conf back to the defaults and rebooted. But now, I can no longer ssh to the server even after rebooting the server in it's old /etc/resolv.conf configuration.

     Does anyone know how I can revert this mistake, ssh again, and properly apply my own dns settings? Kind of desperate here.

     Thanks,

---

### Post by dev18 on 2019-03-10
Update: Got ssh working. Somehow my custom rules for ufw got wiped but it was enabled.

---

### Post by wildmanne39 on 2019-03-10
*Thread moved to **Server Platforms a more appropriate sub-forum**.*

---

