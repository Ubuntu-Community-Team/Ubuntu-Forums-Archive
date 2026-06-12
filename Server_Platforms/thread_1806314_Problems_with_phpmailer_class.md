---
title: "Problems with phpmailer class"
date: 2011-07-17
forum: Server Platforms
---

### Post by tjharrison on 2011-07-17
I've just taken delivery of a new website with a PHPmailer class that should be sending out emails through a gmail account. It was working on the design companies servers but doesn't on the dedicated ubuntu 9 server that i've moved the site to. The process works as its supposed to, but without sending the emails and also without returning any errors (thanks devs). Could there potentially be a problem with the server settings? Or, being  as the class is set up to go through Gmail would this be irrelevant?

---

### Post by tjharrison on 2011-07-17
Ok, well I still have no idea whether this might be the cause of the problem but port 25 on the server isn't responding. How can I unblock this?

---

### Post by Ryan Dwyer on 2011-07-17
I'm under the impression that if you send mail out using Gmail then you need to use SMTP authentication (ie. the Gmail account's username and password). I would start by finding where they are in the code and test them to make sure they work.

Gmail's SMTP server appears to be smtp.gmail.com. I can connect to it on port 25. Check that the hostname in the code is correct.

---

