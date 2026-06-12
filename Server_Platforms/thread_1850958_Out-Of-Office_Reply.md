---
title: "Out-Of-Office Reply"
date: 2011-09-27
forum: Server Platforms
---

### Post by martin.fletcher on 2011-09-27
Hi All,

I have just successfully configured an Ubuntu mail server with Postfix/Dovecot/Squirrelmail.

Currently, i am trying to solve the riddle of out-of-office replies.

What i would like, is for users to be able to send an email to 'out-of-office@example.com' with the message that they want to be placed in the out-of-office reply. This would activate the service and place their custom text into the auto response email.

Upon their return, users be able to send an email to 'back-in-office@example.com' which would stop the service.

Is this possible? I am OK with linux and dabble with python, but this is a very stressful problem to solve.

Any help would be amazing!

Thanks in advance

Martin

---

### Post by SeijiSensei on 2011-09-28
First, you should become acquainted with the "[vacation]("http://packages.ubuntu.com/lucid/vacation")" package.  It's the most commonly used autoresponder in *nix.  See this [man page](http://manpages.ubuntu.com/manpages/lucid/man1/vacation.1.html) for details.

I had to write a system like this from scratch using PHP and a database (PostgreSQL in my case).  Users who want to set up an out-of-office message visit a web page to specify the starting and ending dates of their vacations and the announcement they wish to send.  These are stored in the database.  Each night another PHP script runs at midnight, checks the database, and creates/deletes the appropriate .forward file in the users' home directories that activates or deactivates the announcements.  I'd post the code here, but it's a bit complex because of the various components involved.

---

### Post by martin.fletcher on 2011-09-29
Hey,

Thanks, 

If i give you my email address, would you be able to email me the code to take a look at?

Would be a good starting point for me i think.

Thanks again,

Martin

---

### Post by SeijiSensei on 2011-09-29
I've sent you a PM.

---

