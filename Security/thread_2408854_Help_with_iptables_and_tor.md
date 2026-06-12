---
title: "Help with iptables and tor"
date: 2018-12-24
forum: Security
---

### Post by petrodirovv on 2018-12-24
Good morning 
I think iptables rules the same for openwrt like Ubuntu that&#8217;s why I am asking a question here 

I have a router with openwrt firmware
Have installed tor package and Uncomment socks in tor file
Now if I am setting 127.0.0.1:9100 in my browser, all connections going through tor, but if I am removing socks in browser, all connections go directly by clearnet
What do I need to write in iptables in openwrt to block all clearnet traffic and allow only traffic by tor only if in browser set 127.0.0.1:9100 socks
If not, all traffic will be blocked and any connections will be dropped, no internet
In tor it names IsolateProxy like I think
My iptables rules is clear now Also I want to redirect all dns by tor 

Thank you so much

---

