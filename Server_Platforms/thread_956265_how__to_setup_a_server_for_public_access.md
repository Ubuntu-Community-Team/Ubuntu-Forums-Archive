---
title: "how  to setup a server for public access?"
date: 2008-10-23
forum: Server Platforms
---

### Post by crazydiver on 2008-10-23
Hello,

  It seems that building a server is my next challenge but there are somethings that I don't understand. 

If I want to setup a server to be accessible on the internet so that I can access it any where in the world, how do I do this? Do I need to contact my ISP or something like that?

Second, as a beginner, I am trying to set up a home server at first before going online. However, I have no clue how to this. Can anyone please help? 

Thank you...

---

### Post by bluefrog on 2008-10-23
howtoforge.com is a place of many tutorials

---

### Post by crazydiver on 2008-10-23
cool.. I'll check that out! Thanks!

---

### Post by lykwydchykyn on 2008-10-23
Well, first off, what kind of server?  Web server?  File server?  Game server?

If you have a regular, residential non-business type account with your ISP, then most likely:
 - Your Public IP is dynamic, meaning it changes regularly
 - Incoming default ports for common services, like HTTP or SMTP, are probably blocked.
 - It's very likely against your terms of service to run certain kinds of public services from your home account.  

You can use a service like dyndns.org to get around the dynamic IP problem, and you can use nonstandard ports to get around the second.  But you may want to look over the TOS for your ISP to make sure you aren't going to get dropped for doing whatever it is you want to do.

---

### Post by ezacon on 2008-10-23
I think this should be your 1st reading
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

