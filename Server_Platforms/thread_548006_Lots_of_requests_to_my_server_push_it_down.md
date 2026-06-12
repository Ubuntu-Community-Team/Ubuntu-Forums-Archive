---
title: "Lots of requests to my server push it down"
date: 2007-09-10
forum: Server Platforms
---

### Post by arkopII on 2007-09-10
Hello all, 

I have a Feisty server and since some days my server is being attacked mainly the apache service but also for any other service that I start no matter what port I use. Can anyone help me? I have no idea about this.

This is a snippet of the output of netstat just after I stopped apache:

```
tcp        0      0 ubuntu:www              66-199-241-162.re:59895 TIME_WAIT
tcp        0      0 ubuntu:53886            www.kchomepage.com:www  FIN_WAIT2
tcp        0      0 ubuntu:www              66-199-241-162.re:36855 TIME_WAIT
tcp        0      0 ubuntu:www              66-199-241-162.re:37273 TIME_WAIT
tcp        0      0 ubuntu:www              222.82.74.4:4881        TIME_WAIT
tcp        0      0 ubuntu:www              217.205.136.109:42277   TIME_WAIT
tcp        0      0 ubuntu:www              200.131.211.26:55367    FIN_WAIT2
tcp        0      0 ubuntu:58177            ev1s-67-15-25-170.e:www TIME_WAIT
tcp        0      0 ubuntu:58176            ev1s-67-15-25-170.e:www TIME_WAIT
tcp        0      0 ubuntu:54843            egomania.nu:www         TIME_WAIT
tcp        0      0 ubuntu:www              218.127.232.72.sta:2629 TIME_WAIT
tcp        0      0 ubuntu:35266            magica1.uol.com.br:www  TIME_WAIT
tcp        0      0 ubuntu:www              66-199-241-162.re:34688 TIME_WAIT
tcp        0      0 ubuntu:59958            host-57-123-237-87.:www TIME_WAIT
tcp        0      0 ubuntu:www              204.13.169.9:3259       TIME_WAIT
tcp        0      0 ubuntu:www              75-92-136-43.sea.c:1257 TIME_WAIT
tcp        0      0 ubuntu:www              66-199-241-162.re:60547 TIME_WAIT
tcp        0      0 ubuntu:www              c-68-34-190-131.hs:4104 TIME_WAIT
tcp        0      0 ubuntu:52887            216.36.250.87:www       TIME_WAIT
tcp        0      0 ubuntu:www              216.249.77.180:4368     TIME_WAIT
tcp        0      0 ubuntu:www              host36.201-252-159:4439 TIME_WAIT
tcp        0      0 ubuntu:37620            client3.member.mud.:www TIME_WAIT
tcp        0      0 ubuntu:www              216.255.176.186-c:52197 TIME_WAIT
tcp        0      0 ubuntu:www              66-199-241-162.re:34949 TIME_WAIT
tcp        0      0 ubuntu:www              d2.4d.5646.static:49627 TIME_WAIT
tcp        0      0 ubuntu:www              capitalit.com:44629     TIME_WAIT
tcp        0      0 ubuntu:41572            8.15.231.6:www          TIME_WAIT
tcp        0      0 ubuntu:www              169-73-15-204-Dedi:3058 TIME_WAIT
tcp        0      0 ubuntu:www              bas13-toronto12-1:61200 TIME_WAIT
tcp        0      0 ubuntu:www              218.83.161.220.boa:2615 TIME_WAIT
tcp        0      0 ubuntu:www              194.16.232.72.sta:47653 TIME_WAIT
tcp        0      0 ubuntu:www              c-98-198-44-214.h:60707 FIN_WAIT2
tcp        0      0 ubuntu:www              cpe-69-205-55-81.:61620 TIME_WAIT
tcp        0      0 ubuntu:www              77-56-63-92.dclie:34626 TIME_WAIT
tcp        0      0 ubuntu:52987            65.182.209.224.stat:www TIME_WAIT
tcp        0      0 ubuntu:56074            dvjc.org:www            TIME_WAIT
tcp        0      0 ubuntu:www              98.199.36.72.stat:49050 TIME_WAIT
```

I think I have thousands of attacks, the list of netstat is really long and I think they are increasing.

Thank you very much in advance.

---

### Post by ddrichardson on 2007-09-10
The command```

iptables -A INPUT -s <Source IP> -j DROP
```is the first step - but in this case it appears to be a DDoS, so there are multiple IPs to drop. There were a number of concerted attacks this afternoon, incedentaly.

You're also going to need to contact the datacentres the IPs are from to notify them.

---

### Post by HermanAB on 2007-09-11
Google for 'iptables rate limiting'.  Then use that technique to throttle the server response to new connections.

---

