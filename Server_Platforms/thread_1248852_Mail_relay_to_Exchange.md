---
title: "Mail relay to Exchange"
date: 2009-08-24
forum: Server Platforms
---

### Post by supanatral on 2009-08-24
I'm trying to setup Ubuntu 9.04 with Postfix as a mail relay to Exchange 2007. Is there a good tutorial on that? I'm pretty new to postfix so if there's an easier way I'm open to other ideas as well.

---

### Post by HermanAB on 2009-08-24
If the only thing you need to do is relay to a specific mail server, then nullmailer would be the simplest solution.  You only need to configure two things: Who are you and where to send the mail to.  Google will find it for you.

---

### Post by supanatral on 2009-08-25
Can I somehow test it? how do I make sure that it doesn't become an open relay for spam?

---

### Post by HermanAB on 2009-08-25
What, nullmailer?  It is too simple to do anything wrong - like I said, there are only two things to configure: Who you are and where to send the mail to.  Google the web site and read all about it.

---

### Post by scuzzell on 2009-11-06
@HermanAB: THANK YOU! I have been fighting with sendmail trying to get it to relay mail for two days now. For some reason it would relay for some addresses but not others no matter how I configured it. I already have a fully functional mail server running on my LAN so nullmailer works beautifully for allowing php to send mail through my existing mail server from apache. Elegantly simple. I never want to look at /etc/mail/sendmail.mc again ;)

~Russell

---

