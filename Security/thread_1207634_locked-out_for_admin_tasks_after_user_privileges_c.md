---
title: "locked-out for admin tasks after user privileges change"
date: 2009-07-08
forum: Security
---

### Post by beesblaas on 2009-07-08
This is my fix for a problem I had in Jaunty 9.04, I hope it could help others,
of course, the experts are very welcome to comment and correct.
(This is not about logging in as root in GUI, its about restoring back normal user settings after
stuffing it up).

I changed user permissions:
"users and groups" > user privileges > 
I unclicked "administer the system", thinking that I'll make this user "safe", and leave administrative tasks
for root alone.

I had a password for root assigned before, thinking that I can then log in as root for admin tasks. 
I was stuffed - you cannot use the normal GUI log-on as root, for security reasons.
So I could not log in to change back user privileges:
" The configuration could not be loaded "
" You are not allowed to access the system configuration. "

I searched the web and got a lot of stuff that pointed me in the wrong direction:
(Maybe they were for other problems or packages), i.e.
editing the file /etc/sudoers to add the user did not help at all.
and running: "sudo users-admin", and "gksu users-admin" did not help either. 
(You do get the "users and groups" menu, but you still cannot change it.) 
The error messages are not related to "dbus" problems either.

finally I got the right clue here:
[http://ubuntuforums.org/showthread.php?t=687720&highlight=users+groups](http://ubuntuforums.org/showthread.php?t=687720&highlight=users+groups)

So I opened a command-line window and issued the command:
sudo adduser <username> admin
(it will promt you for psw, and will then add your name in the file /etc/group for admin)

I then rebooted the system. Then it was OK.
Lesson: Always leave admin rights for at least one user, not root. "root" is a special kind of thing in Ubuntu.

---

### Post by cdenley on 2009-07-08
Logging into a graphical interface as root is a horrible idea. Every distribution should disallow it by default, even if they don't use ubuntu's sudo scheme. You should only escalate privileges for the processes needed to perform the admin task by using sudo, su, or policykit. Logging into the GUI as root results in many processes running as root which don't need to.

---

