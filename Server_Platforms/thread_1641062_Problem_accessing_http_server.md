---
title: "Problem accessing http server"
date: 2010-12-08
forum: Server Platforms
---

### Post by markovuksanovic on 2010-12-08
Hi,

I have a problem accessing a server...

If i try to access a web page using [http://127.0.0.1:8080/mypage](http://127.0.0.1:8080/mypage) I can access it correctly. If I try to use, [http://192.168.50.128:8080/mypage](http://192.168.50.128:8080/mypage) I get connection refused.

I configured iptables like this:

iptables -F
iptables -X

iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP
iptables -P INPUT DROP

iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -i eth0 -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -i eth0 -p icmp -j ACCEPT

But this didn't help. I can ping the server but still cannot access the page. Any ideas what else I am missing?

Marko

---

