---
title: "Starting / Stopping MySQL For .cnf change"
date: 2005-07-06
forum: Server Platforms
---

### Post by beatyou on 2005-07-06
This may seem like an elementary question for experienced *nix users but this baffles me as I have zero experience and thought ubuntu would be a great way to get into Linux.

I'm having trouble with allowing remote connections in MySQL so I learn I need to comment out the skip-networking in my.cnf. I chmod my.cnf to the correct permissions allowing me to edit/save but even then I get a message saying my.cnf can't be saved. I'm assuming I need to shut down mysql to save the file, then restart mysql. Can anyone help me out? Thanks

---

### Post by beatyou on 2005-07-07
[QUOTE=beatyou]This may seem like an elementary question for experienced *nix users but this baffles me as I have zero experience and thought ubuntu would be a great way to get into Linux.

I'm having trouble with allowing remote connections in MySQL so I learn I need to comment out the skip-networking in my.cnf. I chmod my.cnf to the correct permissions allowing me to edit/save but even then I get a message saying my.cnf can't be saved. I'm assuming I need to shut down mysql to save the file, then restart mysql. Can anyone help me out? Thanks[/QUOTE]
 Ok I eventually got this one and commented out the skip-networking but it still gives me an error saying "192.168.1.25 is not allowed to connect to this mysql server"

---

### Post by jbarton on 2005-07-08
Have you made the necessary changes in your users table to allow connections form this host? By default, mysql permissions only allow connection from localhost.

---

### Post by gruepig on 2005-07-08
[QUOTE=jbarton]Have you made the necessary changes in your users table to allow connections form this host? By default, mysql permissions only allow connection from localhost.[/QUOTE]
 Yes, you need to modify the user table (and also maybe the db table). Also try setting the 'bind-address' in your my.cnf (e.g., 'bind-address = 192.168.0.2', if your server is 192.168.0.2). You'll then need to restart mysqld.

---

### Post by beatyou on 2005-07-08
[QUOTE=gruepig]Yes, you need to modify the user table (and also maybe the db table). Also try setting the 'bind-address' in your my.cnf (e.g., 'bind-address = 192.168.0.2', if your server is 192.168.0.2). You'll then need to restart mysqld.[/QUOTE]
 Thanks for the replies, What I ended up doing is editing the user table through phpmyadmin, its extremely useful.

---

