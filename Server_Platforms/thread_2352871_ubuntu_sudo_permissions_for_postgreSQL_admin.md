---
title: "ubuntu sudo permissions for postgreSQL admin"
date: 2017-02-16
forum: Server Platforms
---

### Post by rufflechip on 2017-02-16
Hi:

Ubuntu Server 16.04.1 LTS & postgreSQL that came with the install package

I'm new to Ubuntu, and am very rusty with unix & have very minimal SQL experience so please forgive any obvious newbie questions.

I'm working with a friend, I have the linux server at my home (I'm the sudo user), he will be remoting into the terminal (via windows mobaxterm).  He will be setting up a postgreSQL database & running the administration of it (we will both be using R, python, java, c, etc. to manipulate the data).  
1)  Would you recommend giving him full sudo privileges?  Or is there a better way to handle the permissions he'll need to perform his admin tasks?  
      a)  If the later, are there any obvious permissions I should give him to prevent from overly annoying him?  
      b)  FYI, we will be performing a daily pull data from a website like google or yahoo and updating the SQL database.

My concerns:
1)  Security, even though we're using mobaxterm with ssh keys, I'm not sure if allowing him full sudo access via the internet is a good idea.
2)  While he is very familiar with SQL, he's not familiar with unix/linux, & I don't want him doing something really wrong by accident

Please help!

---

### Post by SeijiSensei on 2017-02-16
If you create an account in Linux, that account can create and manage PG databases.
```

sudo adduser someuser
sudo -u postgres "createuser -d someuser"

```
That runs the PostgreSQL createuser command as the master PG user postgres.  The "-d" switch lets that user create databases.  If you want to add an additional password to that account in PostgreSQL, add the "-P" switch to the command.  Generally speaking that is overkill in a situation like yours.

Now log in to Linux as someuser and run 
```
createdb somedbname
psql somedbname

```
You'll now be logged into somedbname and can enter SQL commands at the prompt like CREATE TABLE, SELECT, etc.

The easiest method is for both of you to connect as someuser when working with somedbname.  Otherwise take a look at the discussion of "roles" in [https://www.postgresql.org/docs/current/static/user-manag.html](https://www.postgresql.org/docs/current/static/user-manag.html).

Under this model he does not need root ("sudo") privileges to the rest of the machine.

If your friend logs in with SSH, then I don't think you'll have any other permission issues.  If he wants to use any sort of client program over the network, you'll have to edit /etc/postgresql/[version]/main/pg_hba.conf.  That file has extensive annotations describing how to set up network permissions.  By default only local connections are permitted.

---

### Post by cariboo on 2017-02-16
Moved to Server platforms.

---

### Post by rufflechip on 2017-02-17
Thanks for the help & for the quick response!

---

### Post by rufflechip on 2017-02-18
Hi Everyone:

I typed in the above code & created an account named bogus, when I try the 2nd line of code I get a command not found error.

$ sudo -u postgres "createuser -d bogus"


sudo: createuser -d omegaman: command not found

Should I run the below command?  I have the postreSQL that come with the [COLOR=#000000]Ubuntu Server 16.04.1 LTS [/COLOR]install.

sudo apt-get install postgres-xc

not sure how to proceed. . .
Please help!

---

### Post by SeijiSensei on 2017-02-19
On my 14.04 machine, createuser is in the postgresql-client-common package.  You should install 
```
sudo apt-get postgresql-client*
```
and see if that fixes the problem.

---

