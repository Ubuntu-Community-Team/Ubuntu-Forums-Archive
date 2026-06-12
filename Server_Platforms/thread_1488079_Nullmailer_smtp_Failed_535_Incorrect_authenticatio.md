---
title: "Nullmailer smtp: Failed: 535 Incorrect authentication data"
date: 2010-05-19
forum: Server Platforms
---

### Post by gertjuhh on 2010-05-19
I installed nullmailer on our server so we can push mails out using an external mail server.
However getting the following messages in syslog
```
May 19 22:55:04 <hostname> nullmailer[12435]: Rescanning queue.
May 19 22:55:04 <hostname> nullmailer[12435]: Starting delivery: protocol: smtp host: mail.<ext domain> file: 1274300169.10819
May 19 22:55:06 <hostname> nullmailer[12494]: smtp: Failed: 535 Incorrect authentication data
May 19 22:55:06 <hostname> nullmailer[12435]: Sending failed:  Permanent error in sending the message
May 19 22:55:06 <hostname> nullmailer[12435]: Delivery complete, 1 message(s) remain.
```/etc/nullmailer/remotes contains the following:
```
mail.<ext domain> smtp --port=25 --user=<user>@<ext domain> --pass=<pass>
```Using webmail i can login with details provided in remotes file.
Any clues?

---

### Post by teh_drizzle on 2010-05-19
Might need to use port 587 for authenticated SMTP. Not sure how your external SMTP is set up, just a thought.

---

### Post by gertjuhh on 2010-05-19
Can't connect to port 587, seems to be blocked. Same with 465.
I'm not 100% sure on how the external server is configured as it came with the hosting we already had.

---

