---
title: "Email software"
date: 2012-04-06
forum: The Cafe
---

### Post by magodiafano on 2012-04-06
Hello
I was looking for a tool with whom I could send mails to people subscribed to my mailing list.
I found sendblaster, it was good but limited only to 100 mails per day. I was looking for at least 1000 mails per day.
Do you have advices?

---

### Post by Primefalcon on 2012-04-06
> **magodiafano said:**
> Hello
I was looking for a tool with whom I could send mails to people subscribed to my mailing list.
I found sendblaster, it was good but limited only to 100 mails per day. I was looking for at least 1000 mails per day.
Do you have advices?
could set up a webhost and roll yor own using php

Otherwise you ould do web search and come across something like this... [http://codestips.com/simple-free-mass-mailer-sender-php/](http://codestips.com/simple-free-mass-mailer-sender-php/) like I just did

---

### Post by F.G. on 2012-04-06
you could write a bash script using the 
> mail 
or 
> mailx
commands iteratively to go through a file including a list of emails. you could run it as a cron job and then just have to edit the text file containing the content text (you would probably also need a file to hold the 'subject' if you wanted to automate it).

---

### Post by Ludd1te on 2012-04-06
I think the best course will be to host your own site and mail client.

[Zimbra]("http://www.zimbra.com/products/desktop.html") might be an open source option, or just good ol' [command lining it]("http://www.linuxquestions.org/questions/linux-general-1/mail-program-sending-multiple-emails-900637/")

---

### Post by Paqman on 2012-04-06
> **magodiafano said:**
> at least 1000 mails per day.


I think you'd be ok with 1000, but the "at least" suggests there's a possibility it could be somewhat higher than that. If that's the case, check with your ISP first. If they suspect you of spamming, they'll cut you off.

---

