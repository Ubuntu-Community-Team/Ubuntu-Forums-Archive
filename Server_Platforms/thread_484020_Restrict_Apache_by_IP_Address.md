---
title: "Restrict Apache by IP Address"
date: 2007-06-25
forum: Server Platforms
---

### Post by 1oki on 2007-06-25
Ok so here is the deal. I have an internal website for people to access some files as read only in one office. I would like to set it up so my other offices can access this site. I know how to port forward and all that jive... I was wondering if there was a way I can restrict access to my Apache-ssl based on IP addresses. All my offices use a static IP so they wont be changing anytime soon, and I would like to add them to some kind of list so just they can see these pages...(IPtables?) 

If there is a way, which i believe there should be, can someone point me in the right direction. Thanks

-L

p.s. vpn's and tunneling are out of the question... So I would much rather have it setup as a website with IP blocking. Also, if you have other security hints feel free! :)

---

### Post by 1oki on 2007-06-25
nevermind! I figured it out...


 Order deny,allow
    Deny from all
    Allow from xxx.xxx.xxx.xxx
    Allow from xxx.xxx.xxx.xxx
    Allow from xxx.xxx.xxx.xxx



^^^^
That did it :)

---

