---
title: "Django powered websites down after changing IP address"
date: 2013-05-21
forum: Server Platforms
---

### Post by bayasakh on 2013-05-21
Hello all,
Recently I changed external IP address of my ubuntu server 12.04 LTS.
After changing IP address all websites are down running through apache2 server.
I configured IP address in /etc/network/interfaces and now network works fine, but websites are still down.
I think it's apache issue but I have no clue what's going on.

Please help if you have any ideas.

---

### Post by DJ_Max on 2013-05-21
Did you change your Apache settings? What do your logs say?

---

### Post by gordintoronto on 2013-05-21
More details! What do you mean by "down"? What ip addresses? Do you need to change the setting at the site where you purchased the domain name?

---

### Post by bayasakh on 2013-05-21
All websites are not working. And yes I changed to new IP address of all domain names. Also I changed "ServerName localhost" into /etc/apache2/apache.conf file.
Is there anything else to change? Maybe I forgot to change more settings? Please advice

---

### Post by CharlesA on 2013-05-21
How did you have those sites configured?

---

### Post by bayasakh on 2013-05-21
Configured through Virtualhost.

---

