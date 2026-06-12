---
title: "accessing blog on local network and internet"
date: 2010-06-29
forum: Server Platforms
---

### Post by skipi-gz on 2010-06-29
hi all, this is my firs thread on this site and im still a beginner on ubuntu.

i have php5 and mysql on ubuntu server which is hosting a WordPress blog. i activated it remotely over the internet and it works fine still over the internet. now im home and using my local network again and now when i try to go into it with its local IP, it just shows some text (blog title, posts and so on) with NO pictures.

any help would be appreciated :)
skipi

---

### Post by BobVila on 2010-06-29
Sounds like you've got a config file hardcoded with the domain name or external IP. If, when inside your local network, you go to the dns name ([http://www.example.com](http://www.example.com)), do you see what you'd expect?

---

### Post by skipi-gz on 2010-06-29
oh lol, i found my problem. wordpress uses a default domain so that everytime i tried to access it locally, it would redirect me to the internet IP, im guessing thats what you mean by a hardcoded IP. to solve the problem I edited the hosts file on my client pc(in /etc/hosts) and redirected example.com to the server's local IP :P. thanx anyway

---

