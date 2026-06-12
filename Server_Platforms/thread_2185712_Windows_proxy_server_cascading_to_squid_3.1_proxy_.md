---
title: "Windows proxy server cascading to squid 3.1 proxy on ubuntu"
date: 2013-11-03
forum: Server Platforms
---

### Post by anh-tct on 2013-11-03
Hi everyone

I have installed a squid proxy server 3.1 on ubuntu 12.04, i run proxy as NCSA authentication with specified username and password

I use another proxy server  running on windows platform and cascading this to squid with that user name and password (windows proxy does not have a static IP address so cannot filter access to squid by IP)
 
Then my client computer use the windows proxy to access to the internet, sometimes the username and password authentication from squid  popup on client computer. 

Anyone can help me in this case? how to config the squid server to solve this trouble?

auth_param basic program /usr/lib/squid3/ncsa_auth /etc/squid3/squid-user
auth_param basic credentialsttl 24 hour
auth_param basic casesensitive off
auth_param basic children 20

THanks very much

---

