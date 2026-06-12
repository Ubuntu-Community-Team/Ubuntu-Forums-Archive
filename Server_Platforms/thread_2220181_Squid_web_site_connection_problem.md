---
title: "Squid web site connection problem"
date: 2014-04-27
forum: Server Platforms
---

### Post by secoonder on 2014-04-27
Hello
we have a website on **192.168.3.61** at main location.
web site name is "www.abcd.com.tr"
There are two seperate locations.they are connected with Vpn to main location.
Main location and two seperate locations firewall are iptables + squid proxy.on the other hand ,we have 3 firewall.
Main location computers can connect [www.abcd.com.tr]("http://www.abcd.com.tr")
but two seperate computers can not [www.abcd.com.tr]("http://www.abcd.com.tr"). squid error is:
[B]"""ERROR
The requested URL couldnt not be retrieved.
Failed to connect to 192.168.3.196
the system returned:
(111) Connection refused[/B]"""

But the site ip is 192.168.3.61 ?? Not 196 ??

1)Two seperate computers access allow all at squid.
       acl london src 192.168.45.0/24
        http_access allow all
No problem.Moreover,the client access other sites.No problem
2) When "nslookup www.abcd.com.tr"command other two seperate networks,take answer is [www.abcd.com.tr]("http://www.abcd.com.tr")- 192.168.3.**61**.No problem
3) when traceroute [www.abcd.com.tr]("http://www.abcd.com.tr") command.take answer at the end of line 192.168.3.**61**.No problem
4)two seperate computers can connect other web sites on 192.168.3**.61**.No problem.(192.168.3.61 has a a lot of web sites)
5) at DNS Server zone, 192.168.3.61 match [www.abcd.com.tr]("http://www.abcd.com.tr") for two seperate network.No problem

Moreover,when other two firewall configured ip list to bypass squid,the client can access [www.abcd.com.tr]("http://www.abcd.com.tr") ?? :smile:

i think ; this problem is related by squid ?
What can i do
please help me.Regard.

---

