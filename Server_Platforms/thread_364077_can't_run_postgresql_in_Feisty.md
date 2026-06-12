---
title: "can't run postgresql in Feisty"
date: 2007-02-17
forum: Server Platforms
---

### Post by goneskiing on 2007-02-17
I just installed feisty and added postgresql 8.2 from synaptic -  I then tried using commands that I have used with previous versions

created a new user 
sudo su postgres -c createuser <me>
then I went to create a database 
sudo su postgres -c createdb <dbname>  ERROR database postgres already created

I tried to run initdb but that command is not found

any ideas ?  thks.

---

### Post by allyson on 2007-03-26
Hi - I'm having the same problem - did you solve it, in the end?

---

### Post by spier on 2007-04-03
With dapper server, postgres 8.1 installed from the repos, came to the same problem, too. 

Not sure if its the right way, but, analog to createdb, createuser, and other pg commands, I created initdb as a symlink to pg_wrapper:

sudo ln -s /usr/share/postgresql-common/pg_wrapper /usr/bin/initdb

So far, its working!

---

