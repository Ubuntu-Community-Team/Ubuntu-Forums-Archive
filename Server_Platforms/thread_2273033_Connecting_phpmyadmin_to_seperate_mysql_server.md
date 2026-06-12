---
title: "Connecting phpmyadmin to seperate mysql server"
date: 2015-04-10
forum: Server Platforms
---

### Post by Xiah on 2015-04-10
Hi i've got what's probably a very easy question to solve, but i've been stuck on it for a few days now.

I've got 3 servers running in a small network, DNS, HTTP and MySQL. I've got apache2 and PHP5 installed on the HTTP server and MySQL on the MySQL server. I'm trying to install phpmyadmin on the apache2 server but when I try, i get error 2002 (hy000) because "/var/lib/mysql/mysql.sock" cannot be found, obviously because it isn't installed on that server.

I understand phpmyadmin requires both apache2 and MySQL to run, however is there a way I can install it on either server while still keeping the servers separated? Ideally on the apache2. Thanks in advance!

---

### Post by nerdtron on 2015-04-11
You need to point the phpmyadmin config to use a separate host to database. Usually, phpmyadmin defaults to localhost that's why it is looking for the mysql on the server itself.
See here these for ideas:
[http://stackoverflow.com/questions/16801573/how-to-access-remote-server-with-local-phpmyadmin-client](http://stackoverflow.com/questions/16801573/how-to-access-remote-server-with-local-phpmyadmin-client)
[http://stackoverflow.com/questions/1722064/connect-to-external-server-by-using-phpmyadmin](http://stackoverflow.com/questions/1722064/connect-to-external-server-by-using-phpmyadmin)

Also, the phpmyadmin user should have the appropriate permissions on the remote database server since it is not connecting from localhost.

---

