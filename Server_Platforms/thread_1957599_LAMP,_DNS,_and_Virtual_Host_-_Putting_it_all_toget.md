---
title: "LAMP, DNS, and Virtual Host - Putting it all together"
date: 2012-04-12
forum: Server Platforms
---

### Post by treckstar on 2012-04-12
Hello everyone!

I was recently given an old server by a company I work for to play around with.  I chose to install the latest version of Ubuntu server based off my hardware configuration (Dell Poweredge 4400).

I am very new to Unix/Linux platform and have been having a great time learning and working with this.

Ultimately, my goal is to setup multiple websites on one server.  For example, I have 3 .com URLs registered with godaddy.com.  I would like to point each one of these URL's to my server, each having its own directory.  From my understanding, this can partly be accomplished using Apache virtual host settings.

At this point, I have been able to install the LAMP on the Ubuntu, forward my router to the server, and linked one of the .coms to my IP address via FreeDns.com (A Records).  I can enter that specific URL and get to the index page of my /usr/www/ directory.

I've found several tutorials about setting up the Virtual Hosts, but am confused about how I should setup the DNS for this type of goal.  Will I need my own DNS server to run alongside the Lamp? I feel I would still need to use to FreeDns.com or similar service to make this work.

Any suggestions, links, tutorials that would push me in the right direction for this type of goal would be greatly appreciated.  I feel I am finding good information just not exactly what I need.

Thank you for reading!

---

### Post by CharlesA on 2012-04-12
You would have to have the A record pointing to the IP of your machine you are hosting the site on.

That is if you are using name-based virtual hosts.

[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

---

### Post by jonobr on 2012-04-12
Best place to look for information on virtual hosts ios on the apache foundation website [Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") under the name based support section

Addtional - CharlesA - Sorry bout that..... You got to the submit first!

---

