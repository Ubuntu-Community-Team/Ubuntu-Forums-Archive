---
title: "Best e-mail server software combination"
date: 2011-01-22
forum: Server Platforms
---

### Post by vatzec on 2011-01-22
Hey! I'm planning to set up a mail server for both sending and receiving e-mail on a Debian box. What would, in your opinion, be the best server programs combination for this (and why is it better than the rest)?


Thanks! :-)
vatzec

---

### Post by wongo888 on 2011-01-22
What are your requirements? A server for a small business of 5 people is going to have a different "best" than a server for a medium sized university with 16,000 students.

If I were setting up a mail server for a small business of five staffers I'd just go with hosted GMail or maybe a Mac Mini Server. If the mail exchanger was to mail notices for a web app I'd probably go with postfix or exim on a different domain (to avoid spam blacklisting).

---

### Post by cariboo on 2011-01-22
If you have your own domain name, and need less than 50 email addresses, [Google Apps]("http://www.google.com/apps/intl/en/group/index.html") is the way to go, it's free.

---

### Post by vatzec on 2011-01-22
I'm trying to avoid third parties any way I can, because there's no need to rely my group's data to them ;-) and having a local SMTP server is one of the things that I would want to have.

The mail servers will serve a rather small (though sometimes slightly growing) group of university students just for the sake of enabling them to send mail from their accounts and receive mail too, just in case they need the latter.


Thanks for your responses! :-)
v

---

### Post by HermanAB on 2011-01-23
Citadel of course.

It installs in about 20 minutes and does all email protocols ever invented this side of Betelgeuse, with all you mail and configuration data in a proper database that can handle up to 256 terabytes.  

Any other mail system will keep you happily reading man pages and running little experiments for weeks on end and eventually you may have half the features sortof working...

---

### Post by vatzec on 2011-01-23
Citadel looks great! I think I haven't heard of it. Have you tried it yourself? Is it a system resource hog?

---

