---
title: "added new user, but new user cannot log in"
date: 2014-02-03
forum: System76 Support
---

### Post by jfholla on 2014-02-03
I was setting up my new ratel perfomance desktop and everything was going great when I had hit a snag when I added a new user to the machine. I've got system admin privileges and the new user has "standard" privileges.  
 

 The new users' name shows up on the login screen and her password is recognized, but each time when she logs in she is thrown back to the login screen. I tried to login using her password and got the same results. [Yes, neither she nor I misstyped the password]
 

 What is curious is when I set up her up as new user and logged into her account the login went as expected. The problem started after I copied her home directory (backed up from an old machine running Ubuntu 9.10) over to the new machine using rsync. I copied my files from that same old machine using rsync, but in my case everything went as expected.

 

 Any suggestions on how I can fix this?

---

### Post by steeldriver on 2014-02-03
Did you ensure the copied home directory has the correct ownership and permissions?

---

### Post by nothingspecial on 2014-02-03
You probably need to change the ownership of her home to her new user. What can catch you out is that the username doesn't matter, it's the numeric id that's important. With Ubuntu, the first user that you create when installing is 1000 and the next is 1001, then 1002, 1003 etc etc

You can check this with the id command

---

### Post by PotatoHead007 on 2014-02-03
> **steeldriver said:**
> Did you ensure the copied home directory has the correct ownership and permissions?

Second that. If you did that correctly, it might be a Xorg problem. Not sure exactly how to fix it, but if you need me to i can do some digging(got tonnes of time, cause i do not wanna do school) :P

---

### Post by jfholla on 2014-02-05
Thanks for every ones help on this problem.

As iturned out it was a permissions problem and also a file ownership problem.

The permissions problem was resolved using the GUI and file ownership problem was resolved using the chown command.

---

