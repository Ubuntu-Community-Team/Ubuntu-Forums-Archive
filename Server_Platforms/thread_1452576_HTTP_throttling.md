---
title: "HTTP throttling"
date: 2010-04-12
forum: Server Platforms
---

### Post by minaev on 2010-04-12
Hello,

I'm thinking about some ways to limit access to my web-server. It runs Nginx and php in FCGI. The server contains a large amount of information. The data is freely available and no authentication is required but other companies might like to mirror it and use on their own servers.

The requests could be limited on different levels: IP, TCP, HTTP (by nginx) or by the php application. I found some solutions (like Nginx's limit_req_zone directive), but they do not solve the second part of the problem: there's no way to define a whitelist of clients who are allowed to use the data.

I thought about an intellectual firewall that would limit the requests on IP basis, but I'm yet to find such device. Another way was to hack some scripts that would parse the log file every minute and modify the iptables to ban suspicious IPs. It would take days and I doubt this system will survive, say, 1000 requests per second.

Any ideas? Perhaps, some HTTP proxy, like Squid, could do this?

---

### Post by minaev on 2010-04-12
Solution proposed at nginx mailing list was to use http_limit_req module together with http_geo module. First, we define a group of addresses in directive `geo' and then we set limits with `limit_req' for these groups:

```
geo $slow {
  default 1;
  10.0.0.0/8 0;
}

if ($slow) {
  set $limit_rate 100k;
}
```
Other limits, including requests per second, are set in the same way.

---

### Post by HermanAB on 2010-04-12
Howdy, 

Google for "iptables bandwidth limiting".

---

