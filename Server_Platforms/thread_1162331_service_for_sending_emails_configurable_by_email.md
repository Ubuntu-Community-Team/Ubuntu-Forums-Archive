---
title: "service for sending emails configurable by email"
date: 2009-05-17
forum: Server Platforms
---

### Post by dummzeuch on 2009-05-17
Hi,

I am looking for a service/daemon that does the following:

* Receive request emails sent to it (e.g. [email]remindme@mydomain.com[/email]) containing a date and optionally a time, e.g. "date: 2009-05-18 time: 10:00"
* Parse these emails and store the date/time, the sender and the rest of the message
* Optionally send a receipt on the result of the parsing
* On the date/time specified send an email to the person who originally sent the request containing the message from the request email
* If it also contained a web based UI for managing these reminders, that would be perfect.

I found several online services that offer this service on the internet (e.g. LetterMeLater.com, Deadline, YourLi.st) but was unable to find a linux program for this.

Note: This is about a server based service, not a desktop program. The desktop is not Ubuntu but Windows. Also, requesting reminders by email are a requirement, I do not want a web based only tool.

twm

---

### Post by HermanAB on 2009-05-17
Howdy,

Use Citadel.  It has calendars and scripts and can receive email into any folder (room), filter and do whatever.  It also has a web based GUI in which you can configure most things.  I'm using Citadel on a number of mail servers and I'm sure you can configure it to do what you want if you poke around with it for a while.

---

### Post by dummzeuch on 2009-05-17
> **HermanAB said:**
> 
Use Citadel.

Hm, looks like overkill to me, but if I can't find anything more lightweight, I'll give it a try. Thanks.

twm

---

