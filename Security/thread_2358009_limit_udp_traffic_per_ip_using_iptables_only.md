---
title: "limit udp traffic per ip using iptables only"
date: 2017-04-08
forum: Security
---

### Post by obada3 on 2017-04-08
i am currently making test udp flood on my ubuntu server as we see in screenshot below

[IMG]https://i.stack.imgur.com/4Bxcc.png[/IMG]

in this screenshot we see the ip attacker is 162.222.73.109 and this ip is consumed all trafic (100mbps)


my question how can i limit traffic per ip/second ?


i mean if he made udp flood he just get 1 mb/second not full 100mb/second


Aattacker screenshot

[IMG]https://s7.postimg.org/vxx2d422z/chrome_2017-04-08_08-16-38.png[/IMG]

---

### Post by rickr0ll on 2017-07-30
iptables --limit   I am not sure how to traffic shape but I am interested in what you have been able to do. I know there is mention of doing it on the router end is easier then on iptables.  but if your server is a VPS then how would you do that. i certainly have has servers effected and would like to have something in place. in reality once one is DOS'd there is not much you can do beyond turning off your website and redirecting the domain to null or something liek that to keep the costs down. unless your cloudflare and have the resources.. 

iftop screen shot (handy tool)

---

### Post by HermanAB on 2017-08-08
Here is nice looking guide on the iptables limit filter:
[https://thelowedown.wordpress.com/2008/07/03/iptables-how-to-use-the-limits-module/](https://thelowedown.wordpress.com/2008/07/03/iptables-how-to-use-the-limits-module/)

---

