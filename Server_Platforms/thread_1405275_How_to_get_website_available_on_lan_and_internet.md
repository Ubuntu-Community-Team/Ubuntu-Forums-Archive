---
title: "How to get website available on lan and internet"
date: 2010-02-12
forum: Server Platforms
---

### Post by karmic-koala on 2010-02-12
I am running ubuntu server in a virtual environment (vmware) and have setup apache and got mediawiki up and running which I can access on host machine by going to 172.16.170.130. But this is only available on my host machine and not elsewhere on the network. How do I make it available to others on LAN and eventually on the internet (associated with my host IP address?)

---

### Post by joberly on 2010-02-12
Are they on the same network? From the ubuntu VM post the output of ifconfig, and do the same from the host machine, and another machine on the network.

---

### Post by anubis3000bc on 2010-02-12
I need major help lol, i&#314;l write what i need done in steps.

1.Setup a DNS Server with domain name
2.Link my website to the Domain name
3.Upload a website i have saved to the directory for Apache to see it
4.Config Apache the correct way so i can host the site from my server
5.The correct way to config bind so it can manage my DNS
6.Get the site seen by others on the world wide web

I heard that you can use Dynamic dns to get a name which i have done that and now when i type in my ip in the address bar it redirects to a site i put inside my index.php file that&#347; in my etc/var/www folder. I just need head getting it seen on the world wide web because i have a server so i wouldn´t need any other site to host it for me. So if you can help me please get back to me ASAP i&#7743; all open ears to this matter and want to do it correct.

---

### Post by karmic-koala on 2010-02-13
thanks joberly, your post set the cogs in motion. i wasn't thinking about it this way and indeed they were not on the same network. i switched from nat to bridged and got a 192.168.x.x address

ps a little hint iptables should help

---

