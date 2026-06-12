---
title: "Apache -&gt; Squirrelmail not accesable from internet"
date: 2010-05-04
forum: Server Platforms
---

### Post by Demented ZA on 2010-05-04
I set up a mail server today. Everything works except I can't access the damn squirrelmail web interface from the internet.

I followed this guide here: [https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

I can access [http://192.168.0.50/squirrelmail](http://192.168.0.50/squirrelmail) just fine from a computer on my local network.

*BUT*

When I access [http://mywanip/squirrelmail](http://mywanip/squirrelmail), i get a connection timeout. 

When I access [http://mywanip](http://mywanip), I get the standard Apache "IT WORKS!" Page. (Rules out port forwarding)


According to the guide, that should allow me to access squirrelmail from the internet on my server. Its as if Squirrelmail is only available on my local interface and not on my wan interface? How do I check?

I tried searching on google for a solution, but all hits are not related to my exact situation.

Its late, I'm tired, maybe I'm not thinking clearly anymore, lol :confused:

---

### Post by Demented ZA on 2010-05-04
I tried diagnosing myself and so far it seems to be an Apache problem. 

I have webmin running on this server which is also inaccesible from the internet. All my other services like ssl, sftp and imaps is working. I also installed openwebmail and it gives the same problem.

I'm thinking of removing Apache, doing a purge, and then installing it again. Other than that, I'm not clued up enough on apache to solve it.

Any help would be greatly apprecieted before I try a "shot in the dark" sollution attempt and hit something I don't want to....

---

### Post by lisati on 2010-05-04
It could be that you need to set up port forwarding on your router. 

Are you able to see the "It works" web page from outside your network? Usually forwarding port 80 to your server will be sufficient.

Webmin uses a different port number: I had to set my router to forward port 10000 to my server.

---

### Post by Demented ZA on 2010-05-05
> **lisati said:**
> It could be that you need to set up port forwarding on your router. 

Are you able to see the "It works" web page from outside your network? Usually forwarding port 80 to your server will be sufficient.

Webmin uses a different port number: I had to set my router to forward port 10000 to my server.


I quote from my first post:

"When I access [http://mywanip]("http://mywanip/"), I get the standard Apache "IT WORKS!" Page. (Rules out port forwarding)"

Aside from that, my wan ip belongs to the second network card inside my server. In other words, no port forwarding needed as my server is directly accesible in the internet. 

Thanks for the reply though :-)

---

### Post by Demented ZA on 2010-05-05
Just an update:

All services to my server work fine, including webmin(must have been mistaken earlier).

I decided to do a "sudo apt-get remove --purge squirrelmail" and do the same to apache2.

I'll post my findings.

---

### Post by Demented ZA on 2010-09-09
I was having problems due to my isp. Please refer [here.]("http://ubuntuforums.org/showthread.php?t=1396852")

Thanks for everyone's help! =D>

---

