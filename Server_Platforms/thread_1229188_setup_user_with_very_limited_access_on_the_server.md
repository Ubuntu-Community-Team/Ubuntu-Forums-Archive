---
title: "setup user with very limited access on the server"
date: 2009-08-01
forum: Server Platforms
---

### Post by boondocks on 2009-08-01
On a Ubuntu 8.04 server, I want to create a user "dataentry".
Being a server, "dataentry" can only login via the command line.

I want the "dataentry" user to have very limited acess:
[LIST=1]
[*]He logs in.
[*]System will immediately run the "/home/dataentry/tasks" application.
[*]He exits this application.
[*]System will immediately log him out.
[/LIST]
So this user is severly restricted:
[LIST]
[*]He cannot have any kind of shell access.
[*]He cannot run any application except "/home/dataentry/tasks".
[/LIST]

How do you create this user?
How do you configure/apply these restrictions?

---

### Post by fakrulalam on 2009-08-02
Hi
~/.bashrc is the file which define all the configuration/environment variable after a user login. You can run the  "/home/dataentry/tasks" application from this location after user logged in. The automatic exit can be done from your "/home/dataentry/tasks" application by just adding exit command when user exit to the application.

---

### Post by boondocks on 2009-08-02
I cannot modify the "/home/dataentry/tasks" application.

But, if I the last 2 lines in "~/.bashrc" are:
```
/home/dataentry/tasks
exit
```
Will that be enough?

---

### Post by boondocks on 2009-08-03
> **fakrulalam said:**
> Hi
~/.bashrc is the file which define all the configuration/environment variable after a user login. You can run the  "/home/dataentry/tasks" application from this location after user logged in. The automatic exit can be done from your "/home/dataentry/tasks" application by just adding exit command when user exit to the application.

I put "/home/dataentry/tasks" as the last in ~/.bashrc
But that did not do anything.

So I put "/home/dataentry/tasks" as the last in ~/.bash_profile
But that did not do anything either.

What did I miss?

---

