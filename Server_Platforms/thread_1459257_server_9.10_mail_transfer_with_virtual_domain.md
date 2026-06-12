---
title: "server 9.10 mail transfer with virtual domain"
date: 2010-04-21
forum: Server Platforms
---

### Post by lucaspr on 2010-04-21
I followed this guide: 

[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

And having set up a basic mail server just before I entered data a thought crossed my mind. How about not giving the domain (virtual) users but forward all (except spam and virus mails off course) to the exchange 2003 server. Can it be done? 

I know I'm cross posting. I also asked this question here:
(but not to many people are seeing it so I posted it here also)
[http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy]("http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy")

---

### Post by lucaspr on 2010-04-22
-bump- 

If anyone has an idea... please share it!

---

### Post by lucaspr on 2010-04-27
-bump-

again, sry!

---

### Post by erwall on 2010-04-27
Not sure exactly what you're going for, but sounds like you'd need to add a transport, like this:

```
yourdomain.com             smtp:[exchangeip]
```

---

### Post by lucaspr on 2010-04-27
> **erwall said:**
> Not sure exactly what you're going for, but sounds like you'd need to add a transport, like this:

```
yourdomain.com             smtp:[exchangeip]
```

Your right, that is what I need, but for the virtual domains in the howto. Is such a transport enough to transport all (scanned) mail to the exchange server? Or do I need to transfer all users to the ubuntu machine, or better the right mysql database? 

I hope I cleared things up! and of course thanx for the answer!

---

### Post by erwall on 2010-04-27
> **lucaspr said:**
> Your right, that is what I need, but for the virtual domains in the howto. Is such a transport enough to transport all (scanned) mail to the exchange server? Or do I need to transfer all users to the ubuntu machine, or better the right mysql database? 

I hope I cleared things up! and of course thanx for the answer!

I didn't look at what that howto says to do w/postfix's main.cf file.  If you don't want users to locally access this box and for the mail to be forwarded onto Exchange then that's probably not the best tutorial to use.  Take a look at [http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-jeos-9.10](http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-jeos-9.10)

You'd want something like this in your main.cf, let's assume your domain is testdomain.com:

```

myhostname = yourubuntumailgateway.testdomain.com
mydomain = testdomain.com
myorigin = $mydomain
mydestination = 
local_recipient_maps = 
mynetworks = exchangeserverip, etc
relay_domains = $mydomain
transport_maps = hash:/etc/postfix/transport

```

Don't forget your transport file must be postmap'd after changes and issue a postfix reload.

---

### Post by lucaspr on 2010-04-28
Will look at that! Thanx for the info!

---

