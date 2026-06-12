---
title: "Mailbox + grep = mysql insert?"
date: 2009-06-16
forum: Server Platforms
---

### Post by Karny on 2009-06-16
Hi all!

I've got an interesting situation, and a crazy idea (which might work!)... and I'm hoping that maybe you could either tell me that I'm on the right track... or tell me that I'm crazy and should consider another route.

So, here goes!

I get a number of emails sent to me each day, each with a csv attachment. I manually open these files and insert the contents into a mysql database. This is time consuming and I'd rather spend that time messing around with linux than copy and pasting from spreadsheets!

So, my idea was to setup a mailbox on our ubuntu box, and then have a shell script that would grep that mailbox and insert the contents into the mysql database directly.

This _should_ work right? Mailbox files are just text right? So I should be able to just grep them and then just insert the results into mysql?

I'm not sure how to search for stuff relating to this... or maybe I'm looking at this far to simplistically, but I'd really appreciate any comments or links to howtos for similar things.

Thanks!
Adrian

---

### Post by iponeverything on 2009-06-16
Setup procmail and then you can have it automatically match those messages and pass them off to a script to do the database insert.

---

### Post by sprouty on 2009-06-16
Theres actually a program called "grepmail" should do the job perfect. and a few lines of perl you should be laughing.

Any problems give me a shout

---

### Post by Karny on 2009-06-16
Thanks for the all the feedback! I'd be lost without your help.

I've made 'some' progress, I've got the box downloading the messages via getmail into a maildir, which is a positive step in the right direction. However, now it seems there's an unforeseen issue... The attachments are base64 encoded! Which means I can't grep the contents of them... so there will need to be an additional step.

Is there some way to unencode these files?

---

### Post by iponeverything on 2009-06-17
uudecode or you could do it in a perl script.

---

