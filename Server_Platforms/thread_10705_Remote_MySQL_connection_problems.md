---
title: "Remote MySQL connection problems"
date: 2005-01-10
forum: Server Platforms
---

### Post by savetheclocktower on 2005-01-10
I'm trying to set up a server at work that'll be used only for database queries.  (The server we host our site on is not in our control and doesn't have MySQL installed, so this is what we'll have to do if we want database-driven content on our site.)  Ubuntu grabbed an IP for the server via DHCP upon installation, and some time later I changed it to the static IP that the server has been assigned.

Since I've made that change, I've been unable to connect to the mysql server from other computers.  Localhost connections work just fine, but it doesn't even look like mysql is listening on port 3306.  Apache works fine, ssh works fine... so what am I doing wrong?

---

### Post by moquist on 2005-01-10
I'm a complete mysql beginner myself, but did your hostname change when you changed the IP address?

That may present a problem, since mysql users are identified by username/hostname pairs.

You can try adding a new user to the database, and see if that user can log in.  If so, then you might have to run 'mysql' and use SQL commands to update your old users to have the new hostname (if that is possible to do, which I presume it is).

--matt

---

### Post by jdodson on 2005-01-10
[QUOTE=savetheclocktower]I'm trying to set up a server at work that'll be used only for database queries.  (The server we host our site on is not in our control and doesn't have MySQL installed, so this is what we'll have to do if we want database-driven content on our site.)  Ubuntu grabbed an IP for the server via DHCP upon installation, and some time later I changed it to the static IP that the server has been assigned.

Since I've made that change, I've been unable to connect to the mysql server from other computers.  Localhost connections work just fine, but it doesn't even look like mysql is listening on port 3306.  Apache works fine, ssh works fine... so what am I doing wrong?[/QUOTE]

check the mysql docs.  they tell you how to have mysql accept queries from the outside world.  though i would recommend studing the security implications as well.

---

### Post by savetheclocktower on 2005-01-10
[QUOTE=moquist]I'm a complete mysql beginner myself, but did your hostname change when you changed the IP address?

That may present a problem, since mysql users are identified by username/hostname pairs.

You can try adding a new user to the database, and see if that user can log in.  If so, then you might have to run 'mysql' and use SQL commands to update your old users to have the new hostname (if that is possible to do, which I presume it is).

--matt[/QUOTE]

This isn't the problem -- I've got the GRANTs set up correctly, but the connection isn't getting that far.  MySQL isn't even listening on port 3306.

---

### Post by savetheclocktower on 2005-01-10
Never mind -- fixed it. There was a "skip-networking" line in my.cnf (for security reasons) that I had not seen. Thanks for the help.

---

### Post by JackDog on 2005-01-10
[QUOTE=savetheclocktower]Never mind -- fixed it. There was a "skip-networking" line in my.cnf (for security reasons) that I had not seen. Thanks for the help.[/QUOTE]


Yup unfortunately most distributions preset this to off. Causes a lot of confusion, but it does force the admin to realize its an open port I guess.

---

