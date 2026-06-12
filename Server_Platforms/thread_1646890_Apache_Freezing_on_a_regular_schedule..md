---
title: "Apache Freezing on a regular schedule."
date: 2010-12-16
forum: Server Platforms
---

### Post by bonius on 2010-12-16
Hello.  I'm having a strange problem with Apache2 that I'm hoping someone may have come across before.

I'm running Lucid (server edition) in a VMware Vsphere 4.0 VM.  I have a number of virtual sites setup in apache to serve moodle.

For the past several days, users are complaining that they can't get to moodle between roughly 11:30 and 12:00 every day.  This happens every day at about the same time.

I looked in the /var/log/apache2/access.log and nothing gets logged during that time, not even the "internal dummy connection" stuff that gets logged every second or so the rest of the day.

Here's a snippet from the access.log, where you can see the time jump from 11:34:3 to 11:50:40.  Almost as if Apache took a nap for 16 minutes,```


X.X.X.X - - [16/Dec/2010:11:33:52 -0500] "GET /login/index.php?SAMLRequest=fVJNT8JAEL2b%2BB82e29L0ajZ0BqEGElQGygevC3boV2yH3VnC%2FrvLQUCHuT69s37mJ3B47dWZAMOpTUJ$
127.0.0.1 - - [16/Dec/2010:11:33:55 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Dec/2010:11:33:57 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
X.X.X.X - - [16/Dec/2010:11:34:39 -0500] "GET /login/index.php?SAMLRequest=fVLJTsMwEL0j8Q%2BR79lahJDVpApUFZVYojZw4OY6k2DkJXicFv4eN21VONDr8%2FNbZmYy%2FVIy2IBFYX$
X.X.X.X - - [16/Dec/2010:11:50:40 -0500] "get" 501 297 "-" "-"
127.0.0.1 - - [16/Dec/2010:11:50:49 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Dec/2010:11:50:50 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Dec/2010:11:50:51 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Dec/2010:11:51:09 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
```

During this time, I can ping the server, and ssh into it, but apache seems like it's frozen or something.  The problem goes away within 20 minutes or so on it's own, even if I don't do anything at all.

Any ideas?

Thanks,
Adam

---

