---
title: "apache2 proxy problems maybe hacking???"
date: 2009-05-27
forum: Server Platforms
---

### Post by ant284 on 2009-05-27
Hi,
 
I have a problem with apache2 and apparently mod_proxy!
When I start apache2 /etc/init.d/apache2 start 
it starts fine!
 
then when i type top to see the "active" process list, I see 8 apache2 running
which consumes my MEMORY!!
 
22647 root 20 0 8504 4120 2312 S 0.0 1.6 0:00.06 apache2
22648 www-data 20 0 7600 2384 584 S 0.0 0.9 0:00.00 apache2
22652 www-data 20 0 7920 2224 464 S 0.0 0.8 0:00.00 apache2
22653 www-data 20 0 8876 3944 1752 S 0.0 1.5 0:00.06 apache2
22654 www-data 20 0 8736 3472 1568 S 0.0 1.3 0:00.00 apache2
22655 www-data 20 0 8844 3860 1740 S 0.0 1.5 0:00.04 apache2
22656 www-data 20 0 8876 3848 1732 S 0.0 1.5 0:00.02 apache2
22657 www-data 20 0 8804 3792 1756 S 0.0 1.4 0:00.02 apache2
 
now if stop apache2 
i have still about 3-6 apache2 instances running!! (I checked again via top) 
 
my webserver told me, my server is being used as a web proxy and the mod_proxy has been misconfigured!!! 
I never modified the mod_proxy at all and eventhough I RE-installed apache2 several times 
I still have the same problem, and in apache2 mods-enabled I removed all the proxy things 
so I'm very lost on how to fix the problem
 
any ideas, maybe change the user www-data to something else??
 
thank you

---

### Post by windependence on 2009-05-27
I don't know why people think re-installing a thousand times will magically fix someting that has been misconfigured, I mean, I don't mean to be nasty but This ain't Windoze guys. If something isn't working right, post it on the board and we'll take a stab at it. Shotgunning from the hip is just gonna get you more messed up.

Can you tell me where you got the idea you were an open proxy? FYI, Apache will always start several processes to handle multiple requests. Even one person accessing your site will have many requests back an forth with the server. The processes will gracefully shut down when you stop them, and it may take a few minutes. That is the way it's supposed to work, especially if the process is in the middle of a request thread.

As for your memory, we have posted this many times. Linux will use ALL your memory. It does not use the same memory management that Windoze does, so if you just look at what's free you will freak out like you did. This is normal.

I'm afraid at this point, you have the config so messed up by removeing all things "proxy" that if I were you, I would start fresh one more time. Do ONE thing at a time. If that doesn't work, put it back the way it was and do ONE more thing and so on. We are here to help, but this kind of thing gets frustrating.

-Tim

---

### Post by ant284 on 2009-05-27
Hi,
 
I'm sorry didn't mean to offend, but I re-install to how it was before, looking more into the logs, my server is being used as a proxy
similar to this site 
[http://www.akadia.com/services/prevent_abuse_proxy.html](http://www.akadia.com/services/prevent_abuse_proxy.html) 
 
except It does not redirect to adult websites...
the strange part why I wanted to installed everything
is that 
if I stop apache2 and I look into "top" i still see apache2 instances running, 
if i do stop and pkill apache2 then everything stop, but then moment later apache2 returns on its own... 
 
so basically my server is being use as a proxy server that is for sure.
I'm getting something similar to 
62.158.172.221 "GET [http://www](http://www).**sexranking**.de/sexranking.js 
62.158.172.221 "GET [http://www.sexranking.de/cgi/weblist.cgi](http://www.sexranking.de/cgi/weblist.cgi)
62.158.172.221 "GET [http://www.sexranking.de/cgi/ads.pl](http://www.sexranking.de/cgi/ads.pl)
62.158.172.221 "GET [http://home.t-online.de/**eroticgirl**/hardcore.gif]("http://home.t-online.de/eroticgirl/hardcore.gif") 
 
and the logs file get massive in couple of seconds
 
about the memory issues, is that my system's memory get so full that I have to reboot it everytime i have apache2 running for a couple of days
 
and I made sure that on proxy.conf in mod-enabled 
I had " **ProxyRequests Off " **
I also know I have to do more to prevent, but I'm quite lost now
 
thanks

---

