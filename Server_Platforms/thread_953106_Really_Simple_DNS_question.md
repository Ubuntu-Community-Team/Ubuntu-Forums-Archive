---
title: "Really Simple DNS question"
date: 2008-10-19
forum: Server Platforms
---

### Post by winrowc on 2008-10-19
Ive been having trouble getting the DNS on my sites to function properly. I have 9 different sites, and Ive been having difficultly accessing them in different ways. For the most part all my sites can be accessed by typing in [http://www.example.com](http://www.example.com).

My first problem is that one of my sites gives the shared IP error when I do this, but I can access it by typing in [http://www.example.com/index.php](http://www.example.com/index.php).

My second problem is that none of my sites can be accessed by just typing in [http://example.com](http://example.com). Some go to the parking page from name.com, and others give the shared IP error but none work. For the A record I have [www.example.com](www.example.com) = the server's IP and then another A record with example.com = the server's IP (the hostname is left blank)

I am using name.com to host my domains and know that I need to add some DNS record but Im not sure what.

All of my sites work by typing [www.example.com](www.example.com) when I set the A record on name.com's website for the site to hostname www, record answer: my public IP address.

---

### Post by winrowc on 2008-10-20
Nevermind, it was a silly mistake on my part.

---

