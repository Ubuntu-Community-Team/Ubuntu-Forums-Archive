---
title: "Quick Mail Server question"
date: 2011-03-10
forum: Server Platforms
---

### Post by jmacgowan on 2011-03-10
I've successfully set up a simple mail server (POSTFIX+DOVECOT) for a private nursing school serving around 19 students.  I have set them up as UNIX users on the machine itself, and the webmail is accessible to them through SquirrelMail.  They can send and recieve mail and everything is peachy.
 
This setup seems to be working great for now, but this is just one campus that was just opened.  Eventually, it would need to expand to around 800 students to serve all other campuses.  Is this feasable by just using UNIX users?  Or is it worth virtualizing things with MySQL?
 
My real question is: Since I am comfortable administrating the mail server the way it's set up now, is there anything "wrong" with just adding 800 UNIX accounts instead of going the MySQL route?  I've had issues in the past with setting it up, and I'd rather not read through hours of HOWTOs
 
Thank you in advance for your time, community.

---

### Post by SeijiSensei on 2011-03-10
I don't see any problem with simple Unix accounts myself.  A bigger question is whether the expansion to other campuses will mean more authentication issues than mail service alone.  Will they be using computers on these other campuses?  Will those computers be running *nix, Windows, OS X?  How will users be authenticated on those machines?

If the answer to those questions is that the students will only be using your server for mail, then I'd say stick with what you know and create standard Unix accounts.  However if you'll eventually be faced with authenticating people using computers scattered across multiple locations, you may want to look into something more robust like LDAP, as painful as that can be to configure.  NIS is a less complex alternative for *nix-only networks.

One nice things about Linux is its use of "pluggable authentication modules," or [PAM]("http://www.linuxjournal.com/article/2120").  You can continue using Unix accounts for the foreseeable future, and if the time comes where you need a central authentication server, you can build that on a separate machine.  When you're ready to switch over, you would reconfigure your mail server to use PAM's LDAP module, as an example, instead of the default module that checks the shadow password file.

---

### Post by jmacgowan on 2011-03-10
The students will be authenticated through the webmail client SquirrelMail, which they can access at [http://mydomain.com/squirrelmail](http://mydomain.com/squirrelmail)
 
The students will access this through either provided computers that I can control in our computer lap or their own personal computers.  A vast majority of these machines, if not all, will be Windows.

---

### Post by SeijiSensei on 2011-03-10
Sounds like you're best off just using Unix accounts, especially if this is the only account a student will have.  

I would suggest you get an SSL certificate so that Squirrelmail logins will be encrypted.  You can create a self-signed certificate and tell the students how to use it, or you can get a commercial one for about $50-60/year that will be supported natively by their browsers.  

You also might consider letting them connect directly to the server with a client like Thunderbird or Outlook.  I believe you can use that same certificate for secure SMTP and IMAP.

I forgot to mention [RADIUS]("http://freeradius.org/") as another centralized authentication option.  I've not used it, but I've heard it's not hard to set up.  As lisati says, having a system that enables you to manage a large number of accounts may be very worthwhile as you grow.

---

### Post by lisati on 2011-03-10
> **jmacgowan said:**
> The students will be authenticated through the webmail client SquirrelMail, which they can access at [http://mydomain.com/squirrelmail](http://mydomain.com/squirrelmail)
 
The students will access this through either provided computers that I can control in our computer lap or their own personal computers.  A vast majority of these machines, if not all, will be Windows.

The fact that the users will be using machines running Windows shouldn't stop them logging into squirrelmail - I've done so successfully with my own email server. Having said that, if I were to sign up a lot of users, I'd probably be looking for ways of keeping the volume manageable and possibly some kind of support system.

---

### Post by jmacgowan on 2011-03-10
Thank you!
 
My understanding that is for one domain, using UNIX users isn't the worst solution.  The problem comes in when you want to handle e-mail for more than one domain you have to virtualize it.  
 
What I really wanted to know is if 800 UNIX users is too much for one box, but I suppose it wouldn't be any different if done virtually.  I have no intention of giving the students any access to the server whatsoever except through the webmail client, and I'm working on getting that to be completely secure.
 
Thanks again for your replies

---

### Post by HermanAB on 2011-03-10
Howdy,

Yes, it will work, but you will be better off using a database based mail system and I don't mean just the user authentication, the whole email system should be database backed, since it is far more efficient.

For example, if someone decides to send a message with a 10 MB attachment (a typical MS Word file) to all students, then your system with 800 users will suddenly use 8 Gigabytes of disk space, while if you use a database  mail system it will only use 10 MB of disk space, since it will only store one copy of the attachment.

So you should look at [http://citadel.org](http://citadel.org).

---

### Post by jmacgowan on 2011-03-10
@Herman,
 
Thank you very much for that link, It looks quite appealing..  I'll read around tonight.

---

### Post by HermanAB on 2011-03-10
BTW, there are some Citadel guides on my web site.

---

