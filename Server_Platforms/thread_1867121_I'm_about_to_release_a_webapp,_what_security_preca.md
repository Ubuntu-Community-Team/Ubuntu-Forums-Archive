---
title: "I'm about to release a webapp, what security precautions should I take?"
date: 2011-10-22
forum: Server Platforms
---

### Post by garfonzo on 2011-10-22
Hi Folks:

I'm about to provide a fairly comprehensive webapp running on the Django framework on a Ubuntu server. It will be used exclusively by a business with around 4-5 employees. The webapp deals with all of their business processes and financial tracking. They access it from within their office and outside of their office. So, I need to keep security high. 

As it is now, the security I have is as follows:
[LIST]
[*]The office is behind a dedicated firewall
[*]The entire webapp site is password protected
[*]The entire webapp site is secured through an SSL certificate
[*]All users will be required to have a strong password, and will need to change it periodically
[*]The database behind the webapp will be backed up nightly to a second hard drive on the system, and then weekly to an offsite server
[/LIST]

I was wondering if you had any "best practices" that you think are important to follow.

---

### Post by Lars Noodén on 2011-10-22
Security is a process and should be part of the development to work effectively not an add-on.  It usually fails when attempts are made to take precautions after the system is built. 

That said,

* Validate all data on the way in, every time.

* Use your programming language's [taint checking](http://gunther.web66.com/FAQS/taintmode.html).  All data from or in contact with the outside world is tainted until cleaned.

* [Escape](http://www.php.net/manual/en/function.mysql-real-escape-string.php) all data on the way out, every time.  That includes when writing to a database.

* Use [Prepare/](http://dev.mysql.com/doc/refman/5.1/en/sql-syntax-prepared-statements.html)Execute statements with the appropriate API for your database.

That should get most of the possible problems with your web app.

---

### Post by garfonzo on 2011-10-22
> **Lars Noodén said:**
> Security is a process and should be part of the development to work effectively not an add-on.  It usually fails when attempts are made to take precautions after the system is built. 


Sorry, I should have mentioned the items you listed. I kind of take them for granted since they are already part of every step of development. I have taken all of those steps to ensure that data is clean. I guess I feel like I am taking the proper steps to keep things secure, but wanted to see if I have missed anything. 

Maybe I'm in good shape?

---

### Post by erixnow on 2011-10-22
being on the other end for a bit..... data parsing is a huge part.  also like mentioned besides proper data parse look to see what other server modules could be potentially accessed by the app.  most attacks are by script kiddies doing overflows.  But..... It never hurts to skim your cgi to see what resources can actually be accessed from your server side and with what privilege. oh and the obvious is keeping things at as low of a priv as possible.  some times when I had to I used a middle man script that had no privilege to pass on my data to my server app.  you can use a few tools to do an audit on yourself.



Eric Peyser

---

