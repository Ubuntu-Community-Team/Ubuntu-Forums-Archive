---
title: "Installed OTRS2. Now how do I log in?"
date: 2008-11-07
forum: Server Platforms
---

### Post by Saul Perdomo on 2008-11-07
Installation of OTRS2 (Open source Ticket Request System) went smoothly. Now, I don't know what username or password to enter in *[http://localhost/otrs](http://localhost/otrs)*. In the process I did create a pwd for the MySQL root user, but I wasn't asked to create an OTRS user.

Now what? I'm sure this must be really simple and I'm probably just being obtuse, but I just can't figure out how to create the first user.

Using Ubuntu 8.10, package otrs2 version 2.2.7-2.

---

### Post by cariboo on 2008-11-07
Have you tried admin without a password?

Jim

---

### Post by windependence on 2008-11-08
> The screen lets you enter a user name and a password. Because no users are created after a fresh installation of the system, you have to login as OTRS administrator first. To login as OTRS admin use "root@localhost" for user name and "root" for password.

Warning	

This account data are default on every new installed OTRS system. For that reason you should change the password for the OTRS administrator as fast as possible! This can be done via the preferences for the OTRS administrator account. 


[http://doc.otrs.org/2.3/en/html/x740.html](http://doc.otrs.org/2.3/en/html/x740.html)

Google is your friend. Hope this helps!

-Tim

---

### Post by Saul Perdomo on 2008-12-04
Thank you for the quick reply, windependence! I couldn't get around to posting an update before, but just wanted to say thanks, and man I guess I just didn't know where to look, you were very helpful.

---

