---
title: "Ubuntu component servers help."
date: 2008-07-03
forum: Server Platforms
---

### Post by richardd2137 on 2008-07-03
Hello. I was wondering how would I make a server for Mail(Postfix), another one for MySql, Another one for DNS, another one for APACHE. How would I go about doing this and connecting them together? Any answers welcome thx.

---

### Post by furlabs on 2008-07-05
That's a very broad question so I'm not sure if anyone is going to answer you in detail. But basically:

To make a mail server, apt-get install postfix
To make a mysql server, apt-get install mysql-server
To make a DNS server, apt-get install bind9
To make a web server, apt-get install apache2

Documentation and howtos are available for each, eg try googling "postfix howto" and you will get plenty of results. If you run into a specific problem, by all means come back to the forums and ask.

Also I should point out that it is not necessary to have these all running on separate servers. There is no reason why you can't install all these services on the same physical server, and that will also eliminate some of the issues in getting them to talk to each other.

---

### Post by superprash2003 on 2008-07-05
yea.. better to have them all in one server.. save on costs and maintenance..

---

