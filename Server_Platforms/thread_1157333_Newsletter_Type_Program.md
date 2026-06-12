---
title: "Newsletter Type Program?"
date: 2009-05-12
forum: Server Platforms
---

### Post by MontyV on 2009-05-12
Is there a newsletter type of program that I can use with Ubuntu Server?  Something where I can custom design them on my own and send it out with a subscribe and unsubscribe links.

Also is there any special setup so to not get blacklisted especially since this is legit and people actually signed up for it?

I've used services like ConstantContact and VerticalResponse but I wanted to know if it was possible to do this on my own.

Thank you for any help.

Monty

---

### Post by lykwydchykyn on 2009-05-12
I set up phplist for our public library newsletter, and it works pretty well though getting it fully set up with our email system took some doing.  It's basically a LAMP application and installs like most LAMP applications: untar the app, tweak the configuration file, run a database setup script, and then the rest is setup through the admin controls.

As for getting blacklisted and so forth, it's really a question to work out with your ISP.  Presumably you're going to be connecting to their SMTP servers, so it depends how finnicky they are about mass mailings.

Things are always a bit hairy when you deal with email and stuff.

---

