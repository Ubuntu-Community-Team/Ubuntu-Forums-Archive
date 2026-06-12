---
title: "Mariadb configuration"
date: 2016-03-05
forum: Server Platforms
---

### Post by Lexion45 on 2016-03-05
I have installed ubuntu server 15.10 minimal install.
Apache2 went great.
Mariadb installed fine as well. It says 'active' (running) in green.

I am stuck at Phase 3/6: Running 'mysql_fix_privilege_tables' on second to last line.
Last line is the command prompt with ------'testserver: "$'
I tried running an update command but it said command not found.
I know I have to update and remove or rename 'test' but I'm not sure what to do next.
I don't want to shut down or move on to php5 until I get this configured so I can install Joomla.
    Please help, I don't want to loose it now and I tried looking on Google with not much luck so far. :(   

Thank you so much :)

---

### Post by darkod on 2016-03-06
You should have linked which tutorial are you using because I have no idea what phase 3/6 means. One note that you should be careful about, is whether commands are meant to be run from the server CLI or the mysql/mariadb prompt. If a command needs to be run from the mysql prompt, you usually can enter in it with something like:
```
mysql -u root -p
```

It will ask you for your mysql root password after which you are inside the mysql prompt.

On another note, if you plan to run this server longer and for production, why are you installing 15.10? Use only LTS releases for servers because non-LTS have only 9 months support.

---

