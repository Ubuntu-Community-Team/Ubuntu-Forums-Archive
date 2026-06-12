---
title: "how do I set a user to use a mysql database?"
date: 2009-11-24
forum: Server Platforms
---

### Post by thenetduck on 2009-11-24
Hi 
I created a new user, and a new database, I was wondering how I would be able to set the user I created to use the database for a website I created? 

thanks! 
- The Net Duck

---

### Post by BQAggie2006 on 2009-11-25
Log in to the MySQL prompt with the root account and grant the user privileges on the db. Go to the following site for an in depth guide on how to do this: [http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

A quick example that would grant all privileges to that user to that db would be

```
GRANT ALL ON *dbname*.* TO '*username*'@'*localhost*'
```

---

### Post by slakkie on 2009-11-25
Please be aware that the grant does not allow the OS user access, you'll need to create a user in the mysql db.

[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

---

