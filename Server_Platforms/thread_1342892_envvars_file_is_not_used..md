---
title: "envvars file is not used."
date: 2009-12-01
forum: Server Platforms
---

### Post by Raupe on 2009-12-01
Hello,

I have a Ubuntu 9.10 VServer and like to set the group of the newly created file to a new group.

I found out that it should be changed in the /etc/apache2/envvars file.

there I change the export APACHE_RUN_GROUP=www-data to my new group.

Then I restarted the server as root with apache2ctl restart .. no errors .. but the newly created file hast the old group.

Any guesses where the fault is?

Thx

Max

---

### Post by Raupe on 2009-12-02
I tested some things

I change in /etc/apache2/apache2.conf the line: User ${APACHE_RUN_USER} 

to *User myUser* and it worked .. apache runs as this user

I changed it back and delete the line 

export APACHE_RUN_USER=myUser

in the *envvars *file and get the error the 

apache2: bad user name ${APACHE_RUN_USER}

So it seems the envvars is read but why is the variable not set to my user? 

Thx for your advice 

Max

---

### Post by qajaq on 2009-12-11
I am having the same difficulty, but my interpretation of the results is slightly different.

If the line ```
export APACHE_RUN_USER=MyUser
``` is deleted from the **envvars** file, *and* the subsequent error message cites ${APACHE_RUN_USER} as the bad user name, it seems to me that the envvars file is not being read. The format of the variable (with the $ and {} signs) is in the apache2.conf file, in the line ```
User ${APACHE_RUN_USER}
``` That, to my way of thinking, is where the system is pulling the "bad user name."

In fact, having substituted a user-name in apache2.conf for those variables, and having made a typo in the user-name, I got a similar error message, except that my misspelled user-name was listed as the "bad user name" rather than ${APACHE_RUN_USER}.

So that leads to the original question: Why is envvars not being read?

---

