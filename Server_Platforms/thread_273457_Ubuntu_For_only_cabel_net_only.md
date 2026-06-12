---
title: "Ubuntu For only cabel net only"
date: 2006-10-08
forum: Server Platforms
---

### Post by hightpak on 2006-10-08
i have my own cable net in my area . i was useing windows 2003 server. but now i want to migrate form it to ubuntu server but i have  a littel problem for internet connection sharing ,restricting the user bandwidth and restrict the users from the porn web sites. can any member help on this topics in details

---

### Post by Macchi on 2006-10-09
Hello HighPak,

Disclaimer: these are not ready recipes, I only list here a few thoughts and recommendations. Adding new functions to a server can be risky and time consuming, but provides very good learning experiences! 


If I may rephrase your question, I believe that you are asking for: 

   Content filtering and bandwidth control for a local area network
   using an ubuntu server. It could also work as a gateway and firewall.

Actually I would like to hear more about your requirements:

Have you considered sharing your Internet connection through a router with  a firewall? It would provide improved performance, security and reliability for your whole network. The additional cost is worth for equipment can be easily recovered by saving you time and preventing the headache of having all your network traffic pass through a server all the time. 

Later you may close web ports on the router+firewall and allow only approved contents to pass through the server. Additionally add caching of pages frequently visited by clients on your local network (web proxy). This will improve bandwidth usage for everyone.

Other questions would be: How many computers? How many users? Any approximate bandwidth characteristics and requirements for your internet connection and for clients in your network?


Anyway here are a few things to start with:

Server:
Ubuntu server install

Firewall:
FireHOL 

Web Proxy:
Squid

Content Filtering (also less suitably called "Parental Control"):
DansGuardian, (maybe Willow)

Se an example at [http://www.ubuntuforums.org/showthread.php?t=226298&highlight=parental+control](http://www.ubuntuforums.org/showthread.php?t=226298&highlight=parental+control)


Bandwidth Control:
Wondershaper -> [http://ubuntuforums.org/archive/index.php/t-25911.html](http://ubuntuforums.org/archive/index.php/t-25911.html)

Trickle -> [http://monkey.org/~marius/pages/?page=trickle](http://monkey.org/~marius/pages/?page=trickle)

Forgot to say: Look at the material from the guys at the "Ubuntu Christian Edition", they have content filtering out-of-the-box, as I understood. 


This list could be made very long

---

