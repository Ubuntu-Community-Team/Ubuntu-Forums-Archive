---
title: "Need an improvement for my mail system"
date: 2011-09-23
forum: Server Platforms
---

### Post by trongbang on 2011-09-23
Hi guys,
Please read my post entirely before you quit! I'm here not to ask you to do my assignment but just to give a suggestion if possible.
Thanks in advance!

This is an opened question: I need to set up a system involving at least 2 networked computers. The system need to simulate a real world system which must be useful.

I have decided to install an email server which will operate as follows:

> AIM: To set up an email server with LDAP Integration
SOFTWARE:
+Dovecot email sever
+Postfix SMTP server: mail transfer agent
+SquirrelMail WebMail 
[IMG]http://img40.imageshack.us/img40/8599/sshot4b.png[/IMG]

SETUP:
+ We will set up an email server for domain mydomain.com
+The layout will be like in the diagram.
+A user will then can configure his email client to send and receive emails using the mail server.
+Admin can add, edit, and delete users on the mail server.

However, my teacher said this is a very simple example which needs more elaboration.

Can you guys give me some hints as to what I can add to my email server please?

I have only 2 weeks to finish the setup. That's why I don't know exactly what I can do for my assignment which is feasible.

Kind Regards,

---

### Post by hansdown on 2011-09-24
Welcom to the forum, trongbang.

Homework assignments are a no-go, on this forum.

Sorry, buddy.

---

### Post by trongbang on 2011-09-24
> **hansdown said:**
> Welcom to the forum, trongbang.

Homework assignments are a no-go, on this forum.

Sorry, buddy.

No worries! :) 

Cheers! :D

---

### Post by hansdown on 2011-09-24
You're pretty cool, dude.

stick around, friend.

Hope this gently guides you.

[http://en.wikipedia.org/wiki/Email_client](http://en.wikipedia.org/wiki/Email_client)

---

### Post by ian dobson on 2011-09-24
Hi,

Maybe add a spam filter using a sql database for the filter software (spamassassin with the bayers database on a mysql server)?

Regards
Ian Dobson

---

### Post by iponeverything on 2011-09-24
there are many improvements that can be made.

Look at file systems - find the best choice for your needs.
Look at special tuning options for the file system you choose.
Look at redundancy and options for failure/recovery.  
etc. etc. etc.

use your imagination -- there are dozens of different ways you can look at the problem.

---

### Post by trongbang on 2011-09-24
OMG! 
Thanks guys!
I thought there would be no replies.

Yes, according to your suggestions, I can get a better view of what I can do.

Kind Regards,

---

