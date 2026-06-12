---
title: "logout by script (root) for Xubuntu LTSP"
date: 2007-08-08
forum: Server Platforms
---

### Post by flygin on 2007-08-08
To use LTSP (5) and Xubuntu Desktop for a internet kiosk, I wrote a few shellscripts to manage account of customers. 

All scripts work fine, countdown, credit, warning message, automatic creation of homedir during login, etc. but I could not find anything about 
FORCED LOGOUT when the credit and grace time for a customer is finished. 
A script (by root) should be able to log out a user. 

I thought about a pkill for the user plus killing the ssh session.

1.   any more graceful ways?

2.   What about kiosk software for Xubuntu LTSP?


thanks in advance

---

### Post by koenn on 2007-08-08
I don't know how you set things up, but when the user has logged in through a display manager (gdm, xdm, ...), stopping the display manager is effectively a logout. 

/etc/init.d/gdm stop

---

### Post by flygin on 2007-08-12
the login manager in ltsp 5 is ldm and there might be more than one user logged with ltsp, so stopping the ldm would  (can't test it at the moment) log out all users.

found little help about ldm - no in depth instruction of how it works.


b.t.w. is this the right place of LTSP related stuff?

---

### Post by koenn on 2007-08-12
yes, that's true. 
so you'd have to terminate a specific session ... 
no ideas here. 

and I also don't know if there's a better place to ask edubuntu questions.

not much help eh ...

---

