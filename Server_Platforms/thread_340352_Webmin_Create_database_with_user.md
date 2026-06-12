---
title: "Webmin: Create database with user?"
date: 2007-01-17
forum: Server Platforms
---

### Post by tomplast on 2007-01-17
I'm running a web server at my local school and I have found that Webmin is a great tool to use for handling the server and all of it's components. 

Though I have one problem, I have told Webmin to sync so each time I create a new user account through Webmin it also creates a MySQL account for that newly created user.

I love this sync option though I'm missing a very important thing here. I would like a database (with the same name as the newly created user) to be created at the same time so when the user logs in at the MySQL server they find themself with a empty database.

My second wish if it's possible is to find out how to let each user create new databases and delete their old ones, when I have done this before all databases have been visible to all users and I don't like setting special permissions for every newly created user. I would like Webmin to take care of all of this.

Scripting is not welcome in this case because I have allready made Webmin do the most allready and having a two-way solution doesn't attracts me. So if someone knows how to do this stuff then please reply.

---

### Post by tomplast on 2007-01-19
Hello? If you know the answer of think you do then please answer! This is very urgent as this server is a vital part in the education where several classes uses the web and database services.

So please, help. I have managed to hack webmin so a new database is created each time a new user is created but I can't get the syntax for granting the new user all rights on his/her new database (with the same name as the user).

---

