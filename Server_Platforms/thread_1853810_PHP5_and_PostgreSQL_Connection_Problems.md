---
title: "PHP5 and PostgreSQL Connection Problems"
date: 2011-10-03
forum: Server Platforms
---

### Post by nickleboyblue on 2011-10-03
Here's my problem:  I have apache2 installed with the php5 modules working on clean new server.  I installed PostgreSQL on the server and attempted to connect to the database using a website I am writing.  That connection fails when I execute the connection script in my browser, but when I execute it using the command line, it executes fine.  Same code, same file in both cases, the only difference is what triggers execution.

-How do I check if the php5-postgresql module is working and loaded?
-Is there a setting somewhere that I should switch to enable connections to the database from websites?
-Why would the script run perfectly from the command line but not from the browser?

Please help!

---

### Post by nickleboyblue on 2011-10-09
I fixed it, sort-of.  At this point, I just need to look into what the phppgadmin package installs as dependencies.  For now, it works to simply install phppgadmin, which sets everything right for connecting to PostgreSQL from PHP5.

---

