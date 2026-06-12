---
title: "Strange outbound traffic from my gateway"
date: 2014-01-17
forum: Security
---

### Post by Sandy_Moreno on 2014-01-17
Hi,
I have a linux gateway at office with iptables and squid in transparent mode. All current traffic is routed through this gateway. and all worked without problems
I checked squid logs and I noted somes strange ips and permanet outbound traffic.
The server (ubuntu 12.04) is configured with two network cards. 
eth0 - internet ip
eth1 - internal ip 192.168....
I set some iptables rules:
iptables -vnL
Chain INPUT (policy ACCEPT 25643 packets, 17M bytes)
 pkts bytes target     prot opt in     out     source               destination         
24798   13M ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2370  261K ACCEPT     all  --  eth1   *       192.168.1.0/24       0.0.0.0/0           


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 51398 packets, 23M bytes)
 pkts bytes target     prot opt in     out     source               destination    


An this is and extract of traffic that is been generated (squid3 logs)....

1389996928.235   7461 127.0.0.1 TCP_MISS/302 627 GET [http://www.baidu.com/link?](http://www.baidu.com/link?) - DIRECT/180.76.3.151 text/html
1389996930.642   7264 127.0.0.1 TCP_MISS/301 602 GET [http://blog.sina.com.cn/u/71ce1f5c0101b4zj](http://blog.sina.com.cn/u/71ce1f5c0101b4zj) - DIRECT/218.30.115.254 text/html
1389996932.620  31524 127.0.0.1 TCP_MISS/200 116397 GET [http://www.baidu.com/s?](http://www.baidu.com/s?) - DIRECT/180.76.3.151 text/html
1389996992.800 120100 127.0.0.1 TCP_MISS/000 0 GET [http://www.860527.com/forum.php?](http://www.860527.com/forum.php?) - DIRECT/222.187.220.12 -
1389996994.238  72761 127.0.0.1 TCP_MISS/503 4074 GET [http://login21.cpsserv.com:8082//SaasAuthentication/dynlogin.jsp?](http://login21.cpsserv.com:8082//SaasAuthentication/dynlogin.jsp?) - DIRECT/103.5.198.218 text/html
1389997011.066 120101 127.0.0.1 TCP_MISS/000 0 GET [http://sou.bbs.chinanews.com/index.php?](http://sou.bbs.chinanews.com/index.php?) - DIRECT/61.135.137.116 -
1389997012.345 120100 127.0.0.1 TCP_MISS/000 0 GET [http://shangluo.hsw.cn/system/2013/12/23/051823706.shtml](http://shangluo.hsw.cn/system/2013/12/23/051823706.shtml) - DIRECT/125.76.242.174 -
1389997029.384 120100 127.0.0.1 TCP_MISS/000 0 GET [http://www.cnr.cn/newscenter/gjxw/gnews/201401/t20140117_514681539.shtml](http://www.cnr.cn/newscenter/gjxw/gnews/201401/t20140117_514681539.shtml) - DIRECT/125.39.86.17 -
1389997031.420 120100 127.0.0.1 TCP_MISS/000 0 GET [http://2131775.blog.hexun.com/91112383_d.html](http://2131775.blog.hexun.com/91112383_d.html) - DIRECT/61.183.12.69 -
1389997035.194 120002 127.0.0.1 TCP_MISS/000 0 GET [http://news.search.hexun.com/cgi-bin/search/blog_search.cgi?](http://news.search.hexun.com/cgi-bin/search/blog_search.cgi?) - DIRECT/123.150.92.48 -
1389997038.173 120047 127.0.0.1 TCP_MISS/000 0 GET [http://ltsfgs.zjol.com.cn/shufa/system/2013/12/09/019749047.shtml](http://ltsfgs.zjol.com.cn/shufa/system/2013/12/09/019749047.shtml) - DIRECT/ltsfgs.zjol.com.cn -
1389997045.396 120031 127.0.0.1 TCP_MISS/000 0 GET [http://blog.sina.com.cn/u/bfc5def50101cany](http://blog.sina.com.cn/u/bfc5def50101cany) - DIRECT/218.30.115.254 -
1389997045.913 120100 127.0.0.1 TCP_MISS/000 0 GET [http://liaoba.people.com.cn/topic.html?](http://liaoba.people.com.cn/topic.html?) - DIRECT/58.68.146.40 -
1389997047.157 120100 127.0.0.1 TCP_MISS/000 0 GET [http://www.cnr.cn/jingji/gundong/201401/t20140103_514559054.shtml](http://www.cnr.cn/jingji/gundong/201401/t20140103_514559054.shtml) - DIRECT/www.cnr.cn -
1389997047.697 120100 127.0.0.1 TCP_MISS/000 0 GET [http://s.rednet.cn/?](http://s.rednet.cn/?) - DIRECT/125.77.194.146 -
1389997053.056 231537 127.0.0.1 TCP_MISS/200 361260 GET [http://tieba.baidu.com/f?](http://tieba.baidu.com/f?) - DIRECT/180.76.2.36 text/html
1389997160.005 270999 127.0.0.1 TCP_MISS/200 4086 GET [http://liaoba.people.com.cn/topic.html?](http://liaoba.people.com.cn/topic.html?) - DIRECT/58.68.146.40 text/html
1389997170.993 286579 127.0.0.1 TCP_MISS/200 753 GET [http://search.tianya.cn/bbs?](http://search.tianya.cn/bbs?) - DIRECT/124.225.65.186 text/html
1389997174.227 337264 127.0.0.1 TCP_MISS/200 127206 GET [http://bbs.ifeng.com/forumdisplay.php?](http://bbs.ifeng.com/forumdisplay.php?) - DIRECT/220.181.35.201 text/html
1389997174.373 312286 127.0.0.1 TCP_MISS/200 159627 GET [http://tieba.baidu.com/f?](http://tieba.baidu.com/f?) - DIRECT/180.76.2.36 text/html
1389997818.613 922848 127.0.0.1 TCP_MISS/200 8996 GET [http://liuyan.people.com.cn/list.php?](http://liuyan.people.com.cn/list.php?) - DIRECT/58.68.146.60 text/html
1389997828.865 941541 127.0.0.1 TCP_MISS/200 26340 GET [http://life.jschina.com.cn/system/2012/12/11/015515252.shtml](http://life.jschina.com.cn/system/2012/12/11/015515252.shtml) - DIRECT/58.213.153.154 text/html
1389997833.625 944785 127.0.0.1 TCP_MISS/200 37328 GET [http://forum.home.news.cn/detail/130482883/1.html](http://forum.home.news.cn/detail/130482883/1.html) - DIRECT/203.192.9.12 text/html
1389997833.912 940565 127.0.0.1 TCP_MISS/200 18198 GET [http://www.soso.com/q?](http://www.soso.com/q?) - DIRECT/218.30.103.111 text/html
1389997833.912 923435 127.0.0.1 TCP_MISS/200 14582 GET [http://blog.qq.com/qzone/133327755/1374467381.htm](http://blog.qq.com/qzone/133327755/1374467381.htm) - DIRECT/23.201.103.25 text/html

**Could you tell me what's going on?**
Thanks.

---

### Post by bertan2 on 2014-01-18
I'm not familiar with squid, but I notice you have a policy of ACCEPT for your INPUT chain. It's possible someone has used that opening to hack into your sytem and install some rogue software.

---

### Post by Sandy_Moreno on 2014-01-19
Thank you, I'll check that.

---

### Post by 1clue on 2014-01-19
Do these events coincide with a time you or somebody in your network browses the web?

One of the easiest to start and hardest to maintain ways to deal with this is to edit your /etc/hosts to add lines like this:

127.0.0.1 liaoba.people.com.cn people.com.cn .cn

And then make sure your local box has no http server on it and REJECTs http.

That works for a single host.

I wish there were a way to blacklist anything going to or from China, Nigeria or a few other countries, but it's not quite so easy as that.

OK maybe let Nigeria in but not out.  I love hearing about long-lost millionaire relatives who just left me their fortune.  Gotta read all of them.  Maybe I need psychological help?  :)

---

