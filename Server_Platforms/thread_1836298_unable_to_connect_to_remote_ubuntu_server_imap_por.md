---
title: "unable to connect to remote ubuntu server imap port"
date: 2011-08-30
forum: Server Platforms
---

### Post by ishk on 2011-08-30
i have a virtual server space with a public ip. here i am running imap daemon. but i coudn't
connect to that port remotely.when i telnet it ,it says this
telnet: Unable to connect to remote host: No route to host

plz help me to solve this. I secure the imap using stunnel4
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN  

plz help me

regards

---

