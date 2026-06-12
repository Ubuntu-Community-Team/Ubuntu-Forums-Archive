---
title: "Security for  Ubuntu Web Server"
date: 2009-01-19
forum: Server Platforms
---

### Post by seagullplayer77 on 2009-01-19
I turned an old Dell Dimension I had sitting around into a web server by partitioning XP and installing Ubuntu 7.10 (just regular Ubuntu---not the server edition). I have the LAMP stack installed and I'm using Joomla! for content management.

I've done a little bit of Googling about how to make my server secure---it's for my church, so it would be ideal if I could prevent...umm...less than Christian content from mysteriously appearing ;)---and I didn't come up with very much. It sounds like Ubuntu is a pretty secure platform, but I'd still like some tips on how to make my server more difficult to hack. I'm using DynDNS because I have a dynamic IP and the server is on my home network which consists of (in addition to the Ubuntu server) one more Ubuntu machine and two boxes running XP. 

Any hints/tips for me? Websites with good tutorials? Hit me up!

---

### Post by seagullplayer77 on 2009-01-20
Bump

---

### Post by ibutho on 2009-01-20
You could start by tinkering with the firewall (you can use the command line tool ufw or install gufw which is a gui). Make sure that only ports being used by your services are open. Also make sure that root logins are disabled for things like ssh, ftp etc (I know the root account is locked by default, but its better to be safe than sorry).

---

### Post by seagullplayer77 on 2009-01-20
Since it's strictly a web server (no FTP and I don't use it for local storage or as a mail server), I'm guessing that the only port that should be open is 80, for http? Probably a bad guess, so let me know if I'm wrong!

---

### Post by ibutho on 2009-01-21
Yes, thats correct. If you plan to login remotely via ssh, then you will need to have port 22 open (or whatever port you are using for ssh).

---

