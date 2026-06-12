---
title: "nginx http speed throttle"
date: 2009-05-03
forum: Server Platforms
---

### Post by Wonslung on 2009-05-03
i was wondering if there is any way to throttle the upload speed in nginx for hosting files.

I want to allow users to download files but i've got a slight issue with people using mods like "flashget" and it causes way too much load on my server.

I've been using FTP because of this because i can set how many concurrent connections i allow and the upload speed of each but as some of my users do not have ftp access i'd like to find a way to make http downloads work.

Any ideas?
it was pretty simple in apache but i'm NOT switching back to apache.....nginx with php-fpm is just so much faster on my system 


i've googled this a lot but all i keep finding is articles about "how to speed up your web server"
any help would be greatly appreciated

---

### Post by BkkBonanza on 2009-05-03
You may try the docs on the limit req module. I'm not sure if it will achieve what you want but could be worth experimenting with.

[http://wiki.nginx.org/NginxHttpLimitReqModule](http://wiki.nginx.org/NginxHttpLimitReqModule)

Also I know that is is fairly easy to add a filter at the **iproute** level for rate limiting. I have seen some articles about doing that. It would be outside nginx but if you put your downloads on a different port then an iproute command could limit requests to that port independent of the main server. Try googling for iproute QoS rate limit posts as I have seen them before.

---

### Post by Wonslung on 2009-05-03
> **BkkBonaza said:**
> You may try the docs on the limit req module. I'm not sure if it will achieve what you want but could be worth experimenting with.

[http://wiki.nginx.org/NginxHttpLimitReqModule](http://wiki.nginx.org/NginxHttpLimitReqModule)

Also I know that is is fairly easy to add a filter at the **iproute** level for rate limiting. I have seen some articles about doing that. It would be outside nginx but if you put your downloads on a different port then an iproute command could limit requests to that port independent of the main server. Try googling for iproute QoS rate limit posts as I have seen them before.


yah, i've considered it.

currently i use shorewall for my firewall....it's an amazing package...i absolutely LOVE shorewall...so that is my NEXT stop if there isn't a nginx mod, thanks for you link, i will check it out

---

