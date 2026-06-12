---
title: "dansguardian and squid"
date: 2009-12-24
forum: Server Platforms
---

### Post by buhlenhoff on 2009-12-24
I have ubuntu 9.10 running and I also have a successful squid install working as well as Dansguardian.  I am having a bit of difficulty configuring them to work how I would like them too.  If I want the proxy server to authenticate I can set browsers to 3128 and they'll be immediately asked to authenticate using the basic proxy authentication.  If I point browsers to 8080 then Dansguardian works great and the proxy server is clearly getting the traffic because it logs everything, but then there is NO authentication.  I have tried lots of different configurations, but can't figure what I am doing wrong.  From what I read I should not have to use the "sandwich" configuration with two squid instances since I only want to use basic authentication / identification.  Any advice would be appreciated.  Thanks.

---

### Post by kewlrichie on 2009-12-27
I believe when dans needs to access squid it does it as local host 127.0.0.1 so it prolly does do any auth. You can see this if you check the squid log /var/log/squid/access.log while someone is using dans it comes through squid as local host. If you want to see which computer is accessing what you would need to check the dans logs which is in /var/log/dansgaurdian/access.log.

To do auth in dans would have to check the dans config and look for "authplugin" and you can use proxy basic or whatever its called to use the squid auth. I think that should work

---

