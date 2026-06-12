---
title: "LAN Dns"
date: 2006-04-01
forum: Server Platforms
---

### Post by gmclachl on 2006-04-01
I have a small network at home with 5 machines on it, I have been thinking of having some type of internal DNS server so I don't have to keep updating the hosts files on the machines. 

 I have never looked at Bind before, does anyone know of a good Howto for this type of thing. 

 George

---

### Post by spanishwasabi on 2006-04-07
Hi,

It's not difficult (once you know the trick :-P ).
What I did is look for example files, try to understand a bit what they were doing, copy/paste to my server, adapt them and they worked pretty well.
[http://www.madboa.com/geek/soho-bind/](http://www.madboa.com/geek/soho-bind/)

Under Ubuntu, you must almost not touch anything. Just add your ISPs DNS servers and create bind files for your domain (again, it's just a copy/paste-adapt process).

Good luck,

G

---

### Post by gmclachl on 2006-04-07
Thanks, I will check that out.
 
 George

---

