---
title: "Is this sign of DOS attack?"
date: 2010-05-09
forum: Security
---

### Post by and12345 on 2010-05-09
Guys, have been running squid for a few month with rocks until some suspicios IP makes our network slowing down

This is the log of my squid system (the IP address below is from somewhere on china when i do the trace - i never knew it)

> 1273429225.121  73118 220.136.82.16 TCP_MISS/200 962 CONNECT 61.222.149.157:25 - DIRECT/61.222.149.157 -
1273429225.264   4041 220.136.82.237 TCP_MISS/200 215 CONNECT 203.188.197.10:25 - DIRECT/203.188.197.10 -
1273429225.638   9416 220.136.81.206 TCP_MISS/504 0 CONNECT 168.95.5.26:25 - DIRECT/168.95.5.26 -
1273429225.664  55621 118.168.139.222 TCP_MISS/200 107 CONNECT 210.56.84.58:25 - DIRECT/210.56.84.58 -
1273429225.930    698 118.168.131.88 TCP_MISS/504 0 CONNECT 80.69.67.46:25 - DIRECT/80.69.67.46 -
1273429226.579  66555 220.136.84.150 TCP_MISS/200 504 CONNECT 202.216.228.144:25 - DIRECT/202.216.228.144 -
1273429226.855  21681 220.136.82.169 TCP_MISS/504 0 CONNECT 61.57.242.230:25 - DIRECT/61.57.242.230 -
1273429227.231  60184 220.136.81.206 TCP_MISS/504 0 CONNECT 168.95.6.160:25 - DIRECT/168.95.6.160 -
1273429227.231  60183 220.136.82.131 TCP_MISS/504 0 CONNECT 174.129.241.215:25 - DIRECT/174.129.241.215 -
1273429227.658   1426 118.168.142.205 TCP_MISS/200 215 CONNECT 203.188.197.10:25 - DIRECT/203.188.197.10 -
1273429228.083  23910 220.136.82.131 TCP_MISS/000 0 CONNECT 168.95.5.65:25 - NONE/- -
1273429228.119  22946 118.168.139.57 TCP_MISS/200 75 CONNECT 91.192.55.129:25 - DIRECT/91.192.55.129 -
1273429228.361  23187 118.168.193.145 TCP_MISS/200 39 CONNECT 210.71.187.212:25 - DIRECT/210.71.187.212 -
1273429228.672  23498 220.136.78.224 TCP_MISS/000 0 CONNECT 199.171.54.246:25 - NONE/- -
1273429228.734 298169 118.168.140.74 TCP_MISS/200 133 CONNECT 209.81.9.14:25 - DIRECT/209.81.9.14 -
1273429228.842  23668 220.136.81.11 TCP_MISS/000 0 CONNECT 168.95.6.187:25 - NONE/- -
1273429229.109  23936 118.168.135.181 TCP_MISS/000 0 CONNECT 168.95.5.59:25 - NONE/- -
1273429229.238 901009 220.136.81.28 TCP_MISS/200 81 CONNECT 209.85.217.5:25 - DIRECT/209.85.217.5 -
1273429229.238   4005 220.136.81.161 TCP_MISS/200 166 CONNECT 117.120.20.163:25 - DIRECT/117.120.20.163 -
1273429229.295  21112 118.168.193.145 TCP_MISS/200 102 CONNECT 211.20.183.47:25 - DIRECT/211.20.183.47 -
1273429229.391  21207 220.136.78.21 TCP_MISS/200 39 CONNECT 211.20.183.36:25 - DIRECT/211.20.183.36 -
1273429229.398  21214 220.136.82.135 TCP_MISS/000 0 CONNECT 168.95.6.135:25 - NONE/- -
1273429230.561  63513 220.136.73.4 TCP_MISS/200 491 CONNECT 217.28.176.107:25 - DIRECT/217.28.176.107 -
1273429231.242  60188 220.136.82.165 TCP_MISS/504 0 CONNECT 168.95.5.26:25 - DIRECT/168.95.5.26 -
1273429231.385  19178 118.168.131.88 TCP_MISS/200 1010 CONNECT 65.55.92.136:25 - DIRECT/65.55.92.136 -
1273429231.449  89486 220.136.84.150 TCP_MISS/200 258 CONNECT 72.14.213.27:25 - DIRECT/72.14.213.27 -
1273429231.709  16486 118.168.197.90 TCP_MISS/000 0 CONNECT 202.133.248.207:25 - NONE/- -
1273429231.964  16741 118.168.131.88 TCP_MISS/000 0 CONNECT 168.95.6.182:25 - NONE/- -
1273429232.607   4372 220.136.81.88 TCP_MISS/200 215 CONNECT 203.188.197.10:25 - DIRECT/203.188.197.10 -
1273429232.608   4373 118.168.133.165 TCP_MISS/200 39 CONNECT 210.59.228.173:25 - DIRECT/210.59.228.173 -

if this is DOS attack, any way to overcome this attack?

---

### Post by DGortze380 on 2010-05-10
> **and12345 said:**
> Guys, have been running squid for a few month with rocks until some suspicios IP makes our network slowing down

This is the log of my squid system (the IP address below is from somewhere on china when i do the trace - i never knew it)



if this is DOS attack, any way to overcome this attack?

It's TCP Traffic. So it's not a DOS in a traditional 'Ping Flood' sense. If it's slowing your network, and you have no authorized users at that IP address, block it.

Also consider Fail2Ban or similar. A lot of times that kind of traffic is generated when someone is running scripts against your server.

---

### Post by DGortze380 on 2010-05-10
double post, sorry.

---

### Post by cdenley on 2010-05-10
It looks to me like squid is being used to connect to a bunch of random smtp servers, probably for spam or phishing scams. I'm not very familiar with squid, so I could be mistaken. Those are definitely proxy connection attempts to a bunch of SMTP servers, though, and most of them seem to get a successful 200 response, while some time out (504).

---

### Post by and12345 on 2010-05-14
after i shutdown the server for one night and disable the DMZ setting on my modem, the problem is gone. 
Any other suggestion to overcome this problem?

---

### Post by Grenage on 2010-05-14
Is your proxy open, accessible from the outside?

---

### Post by cdenley on 2010-05-14
> **Grenage said:**
> Is your proxy open, accessible from the outside?

+1

As I already said, you appear to be allowing remote users to send spam through your proxy. If this is a problem, don't allow it.

---

### Post by and12345 on 2010-05-14
i'm opening port 80 and some port to allow my user access our web server, 

is there any specific way to block the spammer?

---

### Post by Grenage on 2010-05-14
You'll want to use some sort of authentication.

---

### Post by uRock on 2010-05-14
This Link may be your answer. I was helping the author test his set up and even the simplest scan would blacklist my IP aka block me from connecting to his server.
[http://blog.bodhizazen.net/linux/nids-psad-and-fwsnort/](http://blog.bodhizazen.net/linux/nids-psad-and-fwsnort/)

---

### Post by cdenley on 2010-05-14
> **and12345 said:**
> i'm opening port 80 and some port to allow my user access our web server, 

is there any specific way to block the spammer?

You mean you want keep your proxy open, but filter that specific spammer? That is kind of pointless, since other people will inevitably find and abuse your open proxy. I suspect you didn't configure squid to function as you intended it to. I'm not familiar with squid, and you never said what you are using it for, so I can't help you with that.

---

### Post by zexelon on 2010-05-14
For the record, an open (to the outside) squid system is a problem as it allow spammers free reign to use your network to spam... on a side note in some areas this can get you in trouble.

Check your access lists in your squid config and lock it down to anything not inside your network. If you need outside access to your proxy I would recommend using ssh with the dynamic port option to create a SOCKS proxy.

---

