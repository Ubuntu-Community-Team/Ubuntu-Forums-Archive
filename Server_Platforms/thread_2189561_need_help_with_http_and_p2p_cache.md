---
title: "need help with http and p2p cache"
date: 2013-11-23
forum: Server Platforms
---

### Post by primejarvis on 2013-11-23
Hello everyone,

I have just installed zorin os and preety much happy with the os ... installed squid and nginx for youtube videos caching but didn't get an idea how to cache p2p traffic .

Squid problem :  sudo tail -f /var/log/squid3/access.log

1385101180.214      1 31.220.4.17 TCP_DENIED/403 3946 GET [http://proxyjudge.info/](http://proxyjudge.info/) - NONE/- text/html
1385115290.297      0 178.19.111.178 TCP_DENIED/403 3471 GET [http://google.pl/](http://google.pl/) - NONE/- text/html

while starting service squid3 

service squid3 start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.80" (uid=1000 pid=24190 comm="start squid3 ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")


I am not getting what the problem might be please help me out guys....

Thankx in advance

---

### Post by salmendar on 2013-11-23
I am pretty new to this myself but the TCP error seems be everywhere.... check the authentication methods and the access files... that might help.. all of the above errors are authentication based.

---

### Post by primejarvis on 2013-11-23
After all installation i was trying it on my own zorin pc that whether the youtube videos are being cached or not is it mandatory to check on client pc side .... 

i have checked it but didnt find anything wrong can u send me any commands which will help me out .... and salmendar do you have any idea about p2p caching ....

Thankx in advance

---

### Post by salmendar on 2013-11-23
check this for squid 

[http://www.squid-cache.org/Doc/config/acl/](http://www.squid-cache.org/Doc/config/acl/)

also check your ports if they are open or not 

[https://accounts.serverpronto.com/knowledgebase.php?action=displayarticle&id=11](https://accounts.serverpronto.com/knowledgebase.php?action=displayarticle&id=11)

---

### Post by primejarvis on 2013-11-23
netstat -nap | grep  8081
tcp        0      0 127.0.0.1:8081          0.0.0.0:*               LISTEN      26334/nginx     

its is ok .....

Salmendar if you could please tell me how to start caching p2p traffic ... i.e., on my client side every bittorrent pc peer list should have the caching solution ip [B]

"After all installation i was trying it on my own zorin pc that whether  the youtube videos are being cached or not is it mandatory to check on  client pc side ...."[/B]

I am write not just trying to test whether everything goes well or not and to be very frank starting is not good ....

---

### Post by salmendar on 2013-11-23
[http://manpages.ubuntu.com/manpages/lucid/man5/apt-p2p.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/apt-p2p.conf.5.html)

this will guide you to p2p caching and also the solve the authentication error that you were facing

---

### Post by primejarvis on 2013-11-23
Salmendar U really helped me a lot .....

If in near future i need help ... if u dont mind can i contact u

Please send me any email-id or skype id so that i can contact u ...

Thankx in advance

---

