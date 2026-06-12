---
title: "Deploy offline web application."
date: 2009-09-25
forum: Server Platforms
---

### Post by rnodal on 2009-09-25
Hello all:

I need to set up a box(laptop) so that an user turns on the computer, logs in and browses a locally hosted website (apache,php,myslq). 
The main concern is protecting the source code so that the user cannot get the username and password for the database. 

I though of a couple of things to accomplish this but I was wondering if someone that may have been in the same situation could share some tips.

So far all I got is this:
- Set password for BIOS so booting from a CD cannot be done.
- Create a very limited account so only the bare minimum activities
 can be performed. (Locked down GNOME).

Any suggestions? 
Thank you very much for your time.

-r

---

### Post by abaden on 2009-09-25
You could install suPHP, so all PHP files must be executed by a specific user. And then simply lock down the directory where you're storing your web files. For example, /home/webuser could be the location of your webfiles, all owned by webuser:webuser. Then, if you give that directory the right permissions (make sure your lockout user can't even view it) you should be good to go. And of course make sure the system is kept up to date and the user you lock down has very, very limited privileges. You could also look into a Jail like Jailkit, though I only have experience with these on Guiless distros.


Alex

---

### Post by rnodal on 2009-09-26
Thank you for taking the time to replay.

I'm not so much concerned about file permisions as I can always use ACLs.
The main concern is since the user has physical access to the machine he/she may bypass anythine that I setup. That's why I mentioned locking the BIOS so the user cannot change the option that allows to boot from a CD but I'm not aware of more ways to prevent the user to bypass any security measure. 

Thank you.

---

