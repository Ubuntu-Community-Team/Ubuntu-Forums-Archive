---
title: "PHP password"
date: 2009-04-08
forum: Server Platforms
---

### Post by happyhacker on 2009-04-08
I've now got access to phpmyadmin from my laptop (XP) over the network. I had to guess the uname/pwd as admin/(blank) which got me in. It shows mysql as being there so I assume I am ready to go except I want to change the phpmyadmin pwd to conform to my system rules. I think this changes the mysql pwd as well.

I have not installed the mysql client.
I have not configured any conf files except apache to recognise phpmyadmin.
phpmyadmin shows me as having "No privaleges".
phpmyadmin conf is set for cookies working.
I have not created any users in mysql yet so working root.
I have not touched the mysql conf files.

How do I change the phpmyadmin/mysql password given these params?

PS I have looked at privaleges and this is what I see:

[COLOR="Blue"]User		HOST		PWD	Glob Priv	GRANT
Any 		%	 	-- 	USAGE 	No
Any 		(servername) No 	USAGE 	No
Any		 localhost 	No 	USAGE 	No
debian-sys-maint localhost 	Yes SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, REPLICATION SLAVE, REPLICATION CLIENT, EXECUTE 						Yes
root 		127.0.0.1 	No 	ALL PRIVILEGES Yes
root 		(servername) No 	ALL PRIVILEGES Yes
root 		localhost 	No 	ALL PRIVILEGES Yes[/COLOR]

Should I also do some security config here?

---

### Post by JochenJung on 2009-04-16
mysqladmin -u root -p'oldpassword' password newpass

---

### Post by happyhacker on 2009-04-16
Thanks, done.

---

