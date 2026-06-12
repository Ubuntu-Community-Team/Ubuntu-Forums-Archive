---
title: "create user who can't login locally"
date: 2009-02-13
forum: Server Platforms
---

### Post by inphektion on 2009-02-13
I'm trying to create an account on my server that no other account can su or sudo into (except one specified in visudo).  However I want to allow ssh login to this account.

so I created a user with adduser --disable-password test
then I edit visudo to say
mainuser ALL=(ALL) /bin/su test

hoping that mainuser is now the only user who can su to test.  
However this isn't working, still get authentication failure.
The idea is that with the test account when people login to it the .bash_login points to a script that runs a program.  This works well as a general user account my problem is that others with local user accounts on the system can 'su test' and get around the .bash_login and have access to it.  So everyone needs to ssh to the server as test but not su.

any pointers?

---

### Post by inphektion on 2009-02-13
Allow me to rephrase what I want to accomplish.

I have users A, B, C and D.  D is a normal account but the .bash_login runs an interactive program.  
On this server I only want user B to be able to su into user D (even though everyone knows user D's password).  Cause user B is the maintainer of the program.  

Users A and C need to login to D so that the .bash_login will execute the program but I don't want them to be able to bypass this by "su D" and get into the D user's files.

This seems very difficult to do and my attempt above won't work.  
any ideas??

---

### Post by inphektion on 2009-02-13
ok here is what i'm thinking:

```

User_Alias NOSU_D = A, C

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
NOSU_D ALL = /bin/su *, !/bin/su *D*

```

This should work...
but if i login as user A I can still type 'su D' no problem.
must be missing something stupid.

---

### Post by inphektion on 2009-02-13
ok if i login as user A and type 'sudo su D' it tells me i'm not allowed.  So it is working.

Now, how do I force users to need to sudo su instead of just using su as they can now?

---

### Post by inphektion on 2009-02-15
if i create a global alias for su = sudo su does anyone see a problem with this?

---

### Post by hvc123 on 2009-02-15
if you dont want them to have terminal(interactive) access you could set their bash to /bin/false

---

### Post by inphektion on 2009-02-15
The problem with setting to /bin/false is then I can't even login to that account over ssh which needs to happen.  And also the way the program runs is by .bash_login which won't run if bash isnt the shell.

---

