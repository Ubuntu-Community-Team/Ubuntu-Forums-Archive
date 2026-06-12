---
title: "problems with XAMPP"
date: 2012-07-31
forum: Server Platforms
---

### Post by darkdragonfly on 2012-07-31
I installed XAMPP on /opt/lampp
I start the services but I can't access to mysql or phpmyadmin
in the browser i put localhost/phpmyadmin and the message is:
**Access forbidden!**

            
     [COLOR=red]New XAMPP security concept:[/COLOR]
     Access to the requested directory is only available from the local network.
     This setting can be configured in the file "httpd-xampp.conf".


And then i try the mysql console client

(bin folder) mysql -u root -p -h localhost
then it asks for the password and i press enter because by default xampp doesnt set a password for root
and the message is 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

THANK U ALL

---

### Post by dakshbhatt21 on 2012-08-31
hey buddy go through this link and then if not solved then tell me . . .

[http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html](http://daksh21ubuntu.blogspot.com/2012/07/new-xampp-security-concept-problem-in.html)

---

### Post by dagpag2 on 2012-08-31
So the solution for this is as follows:
1) Open httpd-xampp.conf which is at /opt/lampp/etc/extra/
2) Find <Directory "/opt/lampp/phpmyadmin">
3) Now just add Require all granted before </Directory>
4) So the code will look like this
<Directory "/opt/lampp/phpmyadmin">
AllowOverride AuthConfig Limit
Order allow,deny
Allow from all
Require all granted
</Directory>
4) Now finally Restart the xampp with this command /opt/lampp/lampp restart

---

