---
title: "apache/mapserver/postgresql security"
date: 2008-03-25
forum: Security Discussions
---

### Post by Go_Bucks on 2008-03-25
I work for a small environmental consulting firm and for one of our projects I have been tasked with setting up a gis database in postgis (which uses postgresql as a back end). The data in this database will be viewable on a website with a built in Mapserver application. I have all of the stuff set up with no problems. 

My issue is that I am no expert on internet security. My intention was to avoid any port forwarding by setting up the client on a private hamachi network (which I am also familiar with because we use it for telecommuting), but I would prefer not to have to walk them through setting that up on their computers.

Is it possible to forward port 80 on our router without potentially exposing the entire office network and our document server to havoc? If so, how? All computers in the office, including the main document server, are windows computers. The computer which would serve the html pages and maps is a linux computer (as is my own computer).

BTW, we have a static IP (in case anyone was tempted to ask).

---

### Post by Dr Small on 2008-03-25
Simply Forward port 80 to the server's IP Address. This does not allow outsiders to access any other computer except to the one you forwarded the port to. As long as your webserver is secure, forwarding port 80 should not cause a security threat.

Dr Small

---

### Post by Go_Bucks on 2008-03-25
So would having that set up restrict any hack attempts to the directories related to the website that are pointed to by apache? Would other content on that specific computer be secure?

---

### Post by Go_Bucks on 2008-03-25
I may have answered my own question. Looking through the documentation for Apache, it appears that I can password protect the website to only let in authorized users. That would allow me to forward port 80 from my router to the server and simply give clients the hyperlink to our static IP as well as a username and password to login to the site. Are there other vulnerabilities inherent in that?

What about in the case of forwarding port 5432 as well (postgis/postgresql) for which all of the databases are password protected? I am asking that because it is currently accessed through a hamachi network, but the hamachi servers seem to be overloaded a lot recently and that has caused problems for those of us working out of our homes to access the server.

---

### Post by hyper_ch on 2008-03-26
> **Go_Bucks said:**
> That would allow me to forward port 80 from my router to the server and simply give clients the hyperlink to our static IP as well as a username and password to login to the site.
If you have a static IP address, why not buyuing a domain and point it to there? Or use some dyndns service like no-ip.com or dyndns.org


> **Go_Bucks said:**
> Are there other vulnerabilities inherent in that?
There might be security holes in the apache code... but that's not something you can fix and it would impact lots of servers...
Another thing you might want to add is fail2ban or hosts deny. Those two check ssh logins and if there are too many invalid attempts from a given IP within a certain period of time that IP will be blacklisted...

---

