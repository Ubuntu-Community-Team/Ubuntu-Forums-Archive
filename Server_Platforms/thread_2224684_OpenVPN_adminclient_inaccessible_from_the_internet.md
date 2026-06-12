---
title: "OpenVPN admin/client inaccessible from the internet"
date: 2014-05-17
forum: Server Platforms
---

### Post by zkvvoob on 2014-05-17
Hello,


Could you, please help me find a solution to this problem I'm having. I just installed OpenVPN 2 on a Ubuntu 12.04 server which has web and mail running for months smoothly. I managed to access the web admin interface from the local network (i.e. [https://192.168.0.105:943](https://192.168.0.105:943)), but if I try from an outside computer using the public static IP address - no luck. 


The server is behind a firewall, but I've forwarded port 943 to the local machine just as I've done for the other services (web, mail).


Thanks in advance for your help!

---

### Post by nerdtron on 2014-05-17
What is the webpage error when you try to access the website using the Public IP of the server?

---

### Post by zkvvoob on 2014-05-18
Just the usual "Google Chrome could not connect to...". But actually I managed to figure it out, I think. For some reason my Linksys router has a problem with some of the ports I try to forward, in this case 943. When I tried connecting through the one used for the actual VPN-ing, it worked.

---

