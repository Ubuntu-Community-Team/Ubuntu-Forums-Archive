---
title: "Setting up reverse proxies."
date: 2016-05-12
forum: Server Platforms
---

### Post by marco_jacobs on 2016-05-12
Hello folks,

I'm currently setting up a gameserver for a little project of mine. Since I want to lower the chance of getting a ddos attack i'm taking some actions to hopefully prevent this as much as possible. I currently have 1 dedicated server running the gameserver, which are 2 applications. The server is running Ubuntu server 14.04.

Those 2 applications are a world server (the world of the game) & a login server (the server which handles the accounts). The world server runs on port 8085 & the login server on 3724.

I have setup an DNS for a domain I have, which is an A record that directs to my dedicated server IP. Now I want to hide my dedicated server IP for the possible chances of a DDOS attack and have read some things about reverse proxies.

I've found some information on Google regarding setting up Nginx for my reverse proxies, but I can only find information for http proxies. I'm planning on buying 2-5 cheap VPS servers to setup as my reverse proxies, by adding those IP's to my DNS record setup (domain) instead of using my dedicated server IP. Does anybody here can help me with some information regarding this topic?

I hope I provided enough information for somebody to help me, since I can't find anything related on Google..

---

### Post by TheFu on 2016-05-12
Welcome to the forums.

Surviving a DDoS is more about having much more bandwidth than the attackers than anything else.  Only then can steps be taken to redirect their traffic.  Reflecting their traffic back is illegal in most jurisdictions.  The bandwidth for 5 servers, even if at completely different providers, isn't that hard to flood.  Entire countries have been taken off line via DDoS, so it really isn't likely that anything you do yourself can handle any determined DDoS attack.  There are web-protection companies for this.  

I only have 20Gbps of bandwidth, so being taken off line has happened a few times.  Any attacker with 25 GigE connected systems can take me down.  Run the numbers using normal broadband uplink connections - 7000 normal broadband systems could take me down too ... there are botnets with 100+K systems like that. No chance my systems would survive - ok, my systems would probably be fine, but the network would be toast and inaccessible during the attack.  Definitely lock down the inputs to only those things which should get through to the back-end servers.  Lots of examples for this filtering for http/https, but anything with a header should be filter-able.  For example, I block win10 users from one of my websites, but other versions are fine. If you control the clients, I'd at least force that client to be used. If it isn't, then redirect them to a place to get the correct client or purchase it.

OTOH, using a reverse proxy to prevent direct access to important services **is** extremely smart. I do it using nginx.  Any protocol can be proxied, though I've only done HTTP/HTTPS.  I would strongly suggest you use a protocol based on HTTP/HTTPS - a nice REST API would be easier to secure.  The ports used don't really explain which protocol is being used ... so to get started, what protocol is your "login server?"

BTW, [https://www.nginx.com/resources/admin-guide/proxy-protocol/](https://www.nginx.com/resources/admin-guide/proxy-protocol/) should work for any TCP connection. See the "stream" example?  I've never done this, but nginx is very solid and I've been using it for both a reverse proxy and web server almost a decade.

---

