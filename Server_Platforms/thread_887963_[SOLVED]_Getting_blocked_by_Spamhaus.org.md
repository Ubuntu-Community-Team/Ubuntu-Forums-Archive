---
title: "[SOLVED] Getting blocked by Spamhaus.org"
date: 2008-08-12
forum: Server Platforms
---

### Post by baudday on 2008-08-12
I don't know how to solve this problem, but certain mailboxes will not accept e-mails sent from my server. This is definitely a problem. Does anyone know how I can fix it. Here's what they say:
[http://www.spamhaus.org/pbl/query/PBL191838](http://www.spamhaus.org/pbl/query/PBL191838)

---

### Post by MJN on 2008-08-12
Your only option is to relay your outgoing mail through your ISP's (Comcast) SMTP server (or, of course, someone else's). If you are using Postfix this is done using the **relayhost = [name of Comcast SMTP server]** directive.

The reason you cannot do anything about the Spamhaus listing is that Comcast have declared that none of their customers (identified by their IP address) should be sending out mail directly from their machines and hence receiving MTAs who consult this list (PBL) should consider such mail as potentially being spam. Some anti-spam policies/strategies will take this particular list as a certainty, rather than a risk, that the mail is spam and hence drop it without a second thought.

Mathew

---

### Post by baudday on 2008-08-12
I really do not like comcast. Thanks for the help again. Haha

---

### Post by windependence on 2008-08-12
They're not high on my list either. Try [www.speakeasy.net](www.speakeasy.net). They are Linux friendly and they don't block your ports. Rates are reasonable too. Customer service is great.

-Tim

---

### Post by lisati on 2008-08-12
> Email sent by Comcast subscribers using a mail program such as Outlook Express are required to send the email through Comcast.
But you're not using an email program like Outlook/Outlook Express......

Should the person who wrote the quote get their flame-resistant clothing ready?

How about this one from my ISP, who use Yahoo for some of their stuff:
> If you wish to submit your report via email, please choose the form and fill out the required fields located at:

 [http://telecom.custhelp.com/cgi-bin/telecom.cfg/php/enduser/ask.php](http://telecom.custhelp.com/cgi-bin/telecom.cfg/php/enduser/ask.php)

Which is it, send by email, or use a form?

---

### Post by baudday on 2008-08-12
ha if my dad wasn't in charge of the ISP stuff I'd probably switch to something more friendly to Linux. I'm sure he'll consider changing now though

---

