---
title: "Ubuntu Logging"
date: 2010-07-22
forum: Server Platforms
---

### Post by ubila on 2010-07-22
Hello all :)
 
After reading this pdf on top 5 things to log for security, ive decided to attempt this for my webserver.
 
I was wondering if anyone could give me a run down on how i might setup some logging systems to do these tasks.
 
Basic things i need to be able to do:
Record things like password attempts on htaccess files, from what IP address, and how many attempts there were.
 
Any useful links anyone can think of to get me started? Im a student programmer at university so any programming i should be able to cope fine.
 
Cheers!

---

### Post by ruffEdgz on 2010-07-23
I can only assume that you have a basic apache server running so the first thing I would do is make sure you have this line in your htaccess or configuration files:

```

ErrorLog /final/destination/of/your/error/logs

```

As long as you have this in there, this should hold any error that happens on your apache server including failed login attempts.

If this does not answer your question, please update on a new post what is your current setup and maybe some configuration files posted using the CODE tags.

I hope this helps.

---

### Post by ubila on 2010-07-23
Hello, thanks for the reply,
Im running apache2, your suggestion didnt seem to work, i got a 500 server error :<
But i have noticed my apache error.log is recording all this information anyway...
 
Am i able to configure the apache logs to seperate out certain errors to certain files?
For example, failed login attempts, to login.log
Failed file lookups to files.log
 
If so how would i do this?
 
Cheers!

---

