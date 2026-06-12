---
title: "Restart trouble"
date: 2013-01-17
forum: Server Platforms
---

### Post by Mikkel66 on 2013-01-17
Hi,

I got in a situation that is strange and i hope i could get some help. This is server/Postgresql related

What I did is kinda simple, I added a post to pg_hba.conf which is
Code:
```
host all all xx.xx.xx.xx(local IP) trust
```

to give access to another user.

After that i run command: 
Code:
```
sudo /etc/init.d/postgresql-8.3 restart
```


It says [OK]

But when i try to access the website i get this error:

could not connect to database

Please, I need some help to get the website back again, did I do something wrong? Or do I need to restart the server itself as well? This is an bigger database running lvs cluster


Some additional information, it says that it is online:

Code:
```
# sudo /etc/init.d/postgresql-8.3 status
```

8.3 main 5432 online postgres /var/lib/postgresql/8.3/main /var/log/postgresql/postgresql-8.3-main.log


But still can't access db or see the site

---

### Post by tarkawebfoot on 2013-01-28
Check your db logs. Sounds like the server is running fine, but it's not allowing the connections. Can you connect directly from psql both locally on the db server and from your remote machine? What user are you connecting as? Has that user been created in the db? psql will usually give you better error messages.

You may also need to check postgresql.conf for the listening address. It should look like this unless you're being more restrictive:

listen_addresses = '*'		# what IP address(es) to listen on;

Since this question isn't Ubuntu specific, you might get better response from the PostgreSQL forum or StackOverflow.

Brian

---

