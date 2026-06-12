---
title: "Update website content using POP3 and Postfix"
date: 2008-12-22
forum: Server Platforms
---

### Post by coffeemist on 2008-12-22
Hi there, I am involved in a website which is undergoing some feature improvements. I am trying to figure out how to receive email content (using Postfix on Ubuntu) and then post the content to a website. The stages would consist of:

receiving an email to [email]notes@subdomain.example.com[/email]
calling a script when the email is received
updating the MySQL database with the content extracted from the email
discarding the original email

I have searched long and hard for something like this-- other websites that do something similar are Tripit.com, basecamphq.com and dopplr.com (among others). If anyone has any idea, pointers and so forth I would be very grateful! thanks.

---

### Post by coffeemist on 2008-12-23
*bump* (please!)

---

### Post by coffeemist on 2008-12-23
I have found an alternative to messing around with postfix (i am reluctant as I am not a good sysadmin!) and also our server has a few users who require the email service... so I don't want to stop that working as well. All of our email is currently forwarded to gmail, so it's possible to use the Atom Gmail reader at [http://gmail.google.com/support/bin/answer.py?answer=13465](http://gmail.google.com/support/bin/answer.py?answer=13465), then an atom reader (maybe [http://www.scriptol.com/rss/atom-reader.php](http://www.scriptol.com/rss/atom-reader.php)) and set a cron job to check the feed every 10 mins or so. 

Dunno whether this is useful for anyone else out there!

---

