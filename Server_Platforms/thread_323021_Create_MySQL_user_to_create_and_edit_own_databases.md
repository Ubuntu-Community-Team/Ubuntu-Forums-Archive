---
title: "Create MySQL user to create and edit own databases only"
date: 2006-12-21
forum: Server Platforms
---

### Post by Brazen on 2006-12-21
I have a developer who has a history of using our Production machines for testing and breaking them.  I've set up a new web and database environment that I want to limit his access to, but it is necessary that he be able to create his own databases and edit them however he wants.

I'm using phpmyadmin to administer MySQL.  What permissions do I need to give his user account so he can create and edit his own databases, but not touch any server settings or other databases?

---

### Post by kidders on 2006-12-21
Hi there,

Afaik something like **GRANT ALL ON dbname.* TO 'user'@'%.domain.tld' IDENTIFIED BY 'password';** should do the trick. If you wanted to, you could change "ALL" to something more restrictive, or play with the part after the "@" to control where the user can access the database from.

**Edit:** Assuming the user starts off unable to access anything at all, you can use individual GRANT statements like this to open up access on a database by database (or even table by table) basis.

---

### Post by Brazen on 2006-12-21
From what I understand, that would only give him permissions on databases named "dbname.*" which would mean I would have to create those databases before he can use them.  I need for him to be able to create and destroy his own databases.

---

### Post by kidders on 2006-12-21
Oops... sorry... I forgot to mention that, in addition, you can allow users to create databases in a similar way, but tbh, you should really think about *not* granting that right to "unreliable" users, since permission to create & destroy databases is very global. In the event he wants a new database, you can create it for him with a single command.

**Edit:** By the way, have you thought about running a separate MySQL server? It might seem like a strange thing to do, but when it comes to the safety of important data, peace of mind is worth a lot! I don't know if this would apply to your individual circumstances, but imagine for the sake of argument that you have a critical MySQL service that you don't want damaged by careless devs. At the same time, your developers can't do much if they don't have access to all of the data on the "critical" server. One possibility might be to think about creating a dedicated development server, and replicating the real one into it.

Would that be far too much trouble?

---

### Post by tturrisi on 2006-12-21
run this query in phpmyadmin, it will allow him to create databases & tables and do anything he wants with them, but he has NO admin privledges.  You can do the same thing via phpmyadmin by Privledges > Add User > and check all privledges EXCEPT any in the Admin section.
```
CREATE USER 'test-guy'@ '%' IDENTIFIED BY 'password';

GRANT SELECT , 
INSERT ,
UPDATE ,
DELETE ,
CREATE ,
DROP ,
FILE ,
INDEX ,
ALTER ,
CREATE TEMPORARY TABLES ,
CREATE VIEW ,
SHOW VIEW ,
CREATE ROUTINE,
ALTER ROUTINE,
EXECUTE ON * . * TO 'test-guy'@ '%' IDENTIFIED BY '********' WITH MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0 ;
```

---

### Post by Brazen on 2006-12-21
Setting up a development server isn't going to fix the issue.  He has a development environment set up on his local machine, but the problem is when something doesn't work and a user has a problem, he likes to go messing with server settings, even when the problem is something local to that person's workstation.

Management wants all the techs and devs to have full access to all the servers.  I'm slowly making headway on this, gradually trying to keep them out of things they shouldn't be in anyway without them noticing much.  When I first got here, nearly all my time was spent fixing problems caused by techs messing with the serveres (I later found out the previous guy had a nervous break down and went psycho, like just started smashing stuff, and I could understand why).  But this is a whole nother discussion.

Anyway, I followed tturrisi instructions.  I tested it out and his user account can mess with other databases, but at least the server will be safe.  I would rather just create the databases for him and give permissions to just those databases, but he already whined when I said that is what I was going to do.  I'm afraid if he takes it to management they will make me undo all the safeguards I've put in place and leave everything wide open again.

To give you an idea of how bad it is, I've been trying to get them to let me put a password on the SA account for our MS-SQL server and to quit having our users log in with the SA account.  Yes, that's right, no SA password at all!

---

