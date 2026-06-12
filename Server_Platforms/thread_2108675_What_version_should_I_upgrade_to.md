---
title: "What version should I upgrade to?"
date: 2013-01-25
forum: Server Platforms
---

### Post by awbarnett on 2013-01-25
I have a home server that is used strictly to host my Web Site.
I am currently using the Ubuntu operating system, Version 10.04.04
It's my understanding that support for this version ends in April of this year (2013).
My Ubuntu knowledge and expertise is very limited.
 
What version should I upgrade to?
Thanks, Anthony

---

### Post by ibjsb4 on 2013-01-25
The next LTS it 12.04 and supported for 5 years.

---

### Post by howefield on 2013-01-25
Thread moved to the "*Server Platforms*" forum.

---

### Post by Impavidus on 2013-01-25
If it's 10.04 server edition it will be supported until April 2015. Currently most recent LTS version is 12.04.

---

### Post by tgalati4 on 2013-01-25
If everything works the way you want it, then wait until April 2015.  If you need newer frameworks (php, ruby, AJAX, jquery, etc) or if want a newer content management system (CMS) then upgrade now to 12.04.

Find another machine to build and put on 12.04 and start adding services.  Have both machines running with different http ports (say 80 and 8080).  Once you have the new machine running will all of your services, then shut off the old machine and switch the http port to 80.  Otherwise, expect some down time when migrating from 10.04 to 12.04.

---

### Post by awbarnett on 2013-01-25
[COLOR=black][FONT=Tahoma]I thank everyone for their response. Everyone has given me great information.[/FONT][/COLOR]
 
Thanks again.

---

