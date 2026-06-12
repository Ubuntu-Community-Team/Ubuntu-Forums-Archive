---
title: "Need pointers on how-to start a web server, I'm lost"
date: 2008-09-03
forum: Server Platforms
---

### Post by silent contender on 2008-09-03
Honestly, I am completely overwhelmed by the amount information about web servers.  I don't know where to start.  I am supposed to run a website for my school club.  I plan on running Ubuntu server.  My restrictions:

Server computer would be P4 HT's (~1.5 GHz) with limited RAM (~1Gb)
Firewall/filter that blocks "bad" webpages
Easy to use and maintain
~80GB of HD

My experience:

Web design (ONLY), about 4-5 years
Bits and pieces of programming
4-6 months with Linux (Ubuntu & Xubuntu)
A little knowledge of networking
My sole source of info: "Ubuntu Hack" from O'Reily

I don't know if this all you need to help me.

---

### Post by Titan8990 on 2008-09-03
Web servers are easy. Start with:

sudo apt-get install apache2

Then type localhost or 127.0.0.1 into your web browser. You should get a screen that says "it works."

Your website will be created by placing .html files in /var/www/

You will need to own a domain name. You will also have to point the A records of that domain to your machine's static IP. Your router should forward port 80 traffic to your box.

Many ISPs block port 80 so that will be something you will want to look in to.

---

