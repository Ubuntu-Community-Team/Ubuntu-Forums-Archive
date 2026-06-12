---
title: "Squid Cache Dir Not found"
date: 2011-04-03
forum: Server Platforms
---

### Post by mkhurram92 on 2011-04-03
hi all there
i have install Squid3 on Ubuntu 10.10. After setting up all the configuration i create swap directories using

squid3 -z

After when i go to the cache directory of squid3(/var/spool/squid3/ there is nothing ???

While my log file are creating TCP_MISS

1301844271.733    445 192.168.100.3 TCP_MISS/403 946 GET [http://d3lvr7yuk4uaui.cloudfront.net/items/domains/u/ubuntuforums.org.js?](http://d3lvr7yuk4uaui.cloudfront.net/items/domains/u/ubuntuforums.org.js?) - DIRECT/216.137.61.181 application/xml
1301844271.742    651 192.168.100.3 TCP_MISS/200 453 POST [http://toolbarqueries.clients.google.com/tbproxy/af/query](http://toolbarqueries.clients.google.com/tbproxy/af/query) - DIRECT/74.125.230.175 text/xml
1301844281.095  55317 192.168.100.3 TCP_MISS/200 269 GET [http://0.229.channel.facebook.com/x/1627609413/1183398692/false/p_100002133514370=0](http://0.229.channel.facebook.com/x/1627609413/1183398692/false/p_100002133514370=0) - DIRECT/66.220.151.92 text/plain
1301844296.918      0 192.168.100.168 TCP_DENIED/403 3792 POST [http://setup.ivelog.com/setup.asp](http://setup.ivelog.com/setup.asp) - NONE/- text/html
1301844298.116      0 192.168.100.168 TCP_DENIED/403 3793 POST [http://setup.ivelog.com/setup.asp](http://setup.ivelog.com/setup.asp) - NONE/- text/html
1301844310.571    686 192.168.100.3 TCP_MISS/200 1654 POST [http://www.facebook.com/ajax/chat/buddy_list.php?](http://www.facebook.com/ajax/chat/buddy_list.php?) - DIRECT/69.63.190.18 application/x-javascript
1301844336.428  55319 192.168.100.3 TCP_MISS/200 269 GET [http://0.229.channel.facebook.com/x/4246020332/1183398692/false/p_100002133514370=0](http://0.229.channel.facebook.com/x/4246020332/1183398692/false/p_100002133514370=0) - DIRECT/66.220.151.92 text/plain
1301844391.762  55317 192.168.100.3 TCP_MISS/200 269 GET [http://0.229.channel.facebook.com/x/1176916619/1183398692/false/p_100002133514370=0](http://0.229.channel.facebook.com/x/1176916619/1183398692/false/p_100002133514370=0) - DIRECT/66.220.151.92 text/plain
1301844411.392    710 192.168.100.3 TCP_MISS/200 1552 POST [http://www.facebook.com/ajax/chat/buddy_list.php?](http://www.facebook.com/ajax/chat/buddy_list.php?) - DIRECT/66.220.156.18 application/x-javascript


Please Help in this aspect
Thanks in advance

---

### Post by mkhurram92 on 2011-10-25
Manually Creating this directory and restarting SQUID solved this issue

---

