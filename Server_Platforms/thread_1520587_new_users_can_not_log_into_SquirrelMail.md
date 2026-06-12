---
title: "new users can not log into SquirrelMail"
date: 2010-06-29
forum: Server Platforms
---

### Post by geking on 2010-06-29
Hello and thanks for taking a look at this.

My problem is quite simple, when I set up squirrelmail I only had one user on the server, and now that I have created new users, I can not log in to their accounts via squirrelmail

I am using Maildir

System is 10.04 server, running postfix and dovecot.  I origionaly set up 'remote' as a user, I can send and recive mail on that account and log into squirrelmail

any new accounts can send email to remote(via outlook/thunderbird), to be seen in Squirrelmail, but get an invalid username/password when I try to log into squirrelmail

in short, new accounts can not log into squirrelmail

Thanks in advance

---

### Post by lisati on 2010-06-29
A couple of possibilities come to mind:
[LIST=1]
[*]User names and passwords are case-sensitive: for example, "user" is seen by the system as something different to "User" or "uSer"
[*]Sometimes new users don't seem to "take" on a system until there's a restart. Yes, I know it's a pain, perhaps someone else has a better suggestion.
[/LIST]

---

### Post by geking on 2010-06-29
Thank you for your ideas.  I have rebooted the server several times after creating the new users.  Additionally, I have tried different permutations of the usernames, including exactly how it is listed in the users' list.  I know I have the usernames/passwords correct as I can get outlook/thunderbird to work using them.

Thanks, do you have any other suggestions?

---

