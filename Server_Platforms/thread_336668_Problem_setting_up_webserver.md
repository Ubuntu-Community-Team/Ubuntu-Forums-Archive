---
title: "Problem setting up webserver"
date: 2007-01-11
forum: Server Platforms
---

### Post by ishift on 2007-01-11
here's the problem:

i got a domain from yahoo. and i have set up a lamp server (edgy :) ). initially, i set up everything on the local network. i have wordpress and gallery2 running. now, for some odd reason, wordpress is not opening up. apparently, it sees the scripts and runs them. i can check the page source. however, nothing is showing up. i tried opera and ie7, and they both show the page without any css. what's going on?

gallery2 works fine.

my other problem is how to basically show my site to the world. i don't know what to configure my router (d-link di-624) to. i looked at many tutorials and explanations. based on what i've read, i should be online, but i'm not. what gives?

i need help. please!

---

### Post by chrisfay on 2007-01-12
Do you have a firewall installed on the server itslef?
Have you given your server a static IP and portforwarded port 80 in your Dlink to that ip?
Do you have a domain, or have you tried with your WAN IP to reach your site?

9 times out of 10 the issue is with port forwarding or port filtering by the ISP. If you're sure you have the routing correctly set, you can try changing Apache's listen port to some non-standard port like 8580 or 8080 to check for ISP port blocking. Then make sure you port forward that chosen port to the router's IP. Then try reaching the server again via xxx.xxx.xxx.xxx:8580. If you can connect on this port, but not on 80, you're probably blocked. 

Most, if not all ISP's consider servers against their TOS unless you're paying for business access or some special hosting package. Some filter their ports and some don't. Fortunately for me, my ISP does not, but be careful. They may shut down your services if they find you in violation.

---

### Post by ishift on 2007-01-12
no, i don't think i have a firewall on my server.
yes, i've given my server a static dhcp and port forwarding to port 78 on my dlink on that ip.
yes, i have a domain and the wan ip (along with the domain) works as long as i have the port attached as well (ie, example.com:78)

and, yea, thanks for the warning.

---

### Post by ishift on 2007-01-13
*healthy bump*

any ideas?

---

