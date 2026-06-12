---
title: "pass traffic through servers"
date: 2020-07-16
forum: Server Platforms
---

### Post by bardiamgtgc on 2020-07-16
i have 2 servers one of them is my main that i have my project and other stuff on second one doesnt have anything special
now i want my users to connect to second server http proxy with port 3128 or any other port then their traffic gets passed through first server so they connect to proxy for example 10.0.0.1:3128 then when they access internet they have ip 10.0.0.2 which is second servers ip for example
these servers arent local it was just an example also my main server is running java and 4 lamp + shoutcast
one of servers running ubuntu 18.04 other one centos 6.5 
any help?

---

### Post by SeijiSensei on 2020-07-16
[https://httpd.apache.org/docs/2.4/howto/reverse_proxy.html](https://httpd.apache.org/docs/2.4/howto/reverse_proxy.html)

---

### Post by bardiamgtgc on 2020-07-16
thanks for your response 
i was actually looking for something that user can connect to with their proxy settings not just search in browser to see content 
but still thanks for your help

---

### Post by SeijiSensei on 2020-07-17
It's not very clear what you are trying to accomplish. The other major proxying application is [Squid]("http://www.squid-cache.org/").

---

### Post by bardiamgtgc on 2020-07-17
think of it like a socks5 proxy or something like that or even a http proxy that can be made with squid but the traffic gets passed through another linux machine

---

### Post by LHammonds on 2020-07-17
I am not really getting what you are trying to accomplish either...such as purpose.

You have two servers that "are not local" which means they are outside your LAN and outside your firewall.

You want your PCs to use Linux box #1 as your proxy destination on your PCs but instead of providing them access to the internet from this proxy server, you want to route those requests to Linux box #2 and then out to the Internet?

So you want the Internet routing to look like this?:

PC -> LAN Firewall -> Web-facing Linux Box #1 -> Web-facing Linux Box #2 -> Final destination

---

### Post by bardiamgtgc on 2020-07-17
exacly
so in if we look at it its stupid to do this
but in our country because of protesting they block everything except servers and websites hosted inside our country 
vps and vds that are hosted inside country still have network no traffic filtering for these
well im not a big fan of this block thing i want to play online games and learn stuff online so this was the first thing that came to my mind
currently we have no idea when this will happen but it happened before which was the first time they did this and we had no way to connect to outside www for about a month or two which was a very boring time(before quarantine)
when they mess with network then we will have no access to any website to buy any kind of server and we know these information about server network because of some people that bought their servers before goverment messed up with the internet
people are protesting again and some cities dont have access to internet either they can just use some useless websites thats why i really want to do this right now

---

### Post by LHammonds on 2020-07-18
Vpn?

---

### Post by bardiamgtgc on 2020-07-18
if youre saying that i can use a vpn then no it didnt work back then
if youre saying that this pass through would be like a vpn then yes but i have no idea how to set t up

---

### Post by wildmanne39 on 2020-07-18
Hello bardiamgtgc  
> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Given that our forums could be used by people at work and school we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for both.
The above rules also apply to circumventing ones local laws, we are sympathetic to your situation but we do not allow this type of discussion here, we are living in hard times and it is very unfortunate that there are countries doing this, I recommend asking for help on another site.

Thread Closed!

---

