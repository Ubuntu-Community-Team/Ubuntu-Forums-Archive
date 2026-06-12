---
title: "Securing my box"
date: 2006-04-19
forum: Server Platforms
---

### Post by pug_205 on 2006-04-19
I recently installed XAMPP on my box, and I, unfortunately, decided to make very little effort to secure my system (everything was default as the installation was done in the morning right before I left for work, and I told noone, except a few close friends, that the server was up and running). The end result was, that I was hacked into oblivion. Can anyone give me some solid information on how to properly secure Ubuntu? It would be much appreciated. My apologies if there is already a thread on this topic, I searched desperately and could not find one.

---

### Post by alamba on 2006-04-19
[QUOTE=pug_205]Can anyone give me some solid information on how to properly secure Ubuntu? [QUOTE]

Security XAMPP is available on their website:
[http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)

I typically also run nmap to see which ports my servers are listening on and close any unneccessary services. Basic hygiene of passwords is also a good idea. Depending on what your needs are from the server you might also want to look into setting up your IPtables (firewall).

A

---

