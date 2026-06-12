---
title: "Sending emails when user logs in/ logs out"
date: 2009-08-20
forum: Security
---

### Post by svittal on 2009-08-20
Hi,

I'm trying to maintain a log of 2 jr admin user activities on the server.
In order to do that, I was planning to have the .profile file of each user 
**mail -s "User admin1 Login" [email]mainadmin@abc.com[/email] < date **

This will send me an email when the admin1 logs in.

In the .bash_logout I have
[B]mail -s "Admin1 Logged out" [email]mainadmin@abc.com[/email] < /home/admin1/.bash_history
>/home/admin1/.bash_history
[/B/

I want to receive an email with the contents of admin1's history.

Question:
1> Is this a good way to do what I'm trying to achieve?
2> When I logout, I get the history from my previous login and not the recent login which should match this logout. Even though I truncate the history file when I logout, it does not happen the way I want. How can you send email of the current history during logout?

---

### Post by svittal on 2009-08-20
> **svittal said:**
> Hi,

I'm trying to maintain a log of 2 jr admin user activities on the server.
In order to do that, I was planning to have the .profile file of each user 
**mail -s "User admin1 Login" [email]mainadmin@abc.com[/email] < date **

This will send me an email when the admin1 logs in.

In the .bash_logout I have
[B]mail -s "Admin1 Logged out" [email]mainadmin@abc.com[/email] < /home/admin1/.bash_history
>/home/admin1/.bash_history
[/B/

I want to receive an email with the contents of admin1's history.

Question:
1> Is this a good way to do what I'm trying to achieve?
2> When I logout, I get the history from my previous login and not the recent login which should match this logout. Even though I truncate the history file when I logout, it does not happen the way I want. How can you send email of the current history during logout?



I got an answer to my 2nd question:

I changes the logout script to :
history |mail -s "User Logout" [email]svittal@abc.com[/email]
>/home/admin1/.bash_history

---

