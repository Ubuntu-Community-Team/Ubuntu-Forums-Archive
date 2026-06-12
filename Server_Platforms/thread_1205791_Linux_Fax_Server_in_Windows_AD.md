---
title: "Linux Fax Server in Windows AD??"
date: 2009-07-06
forum: Server Platforms
---

### Post by CNLiberal on 2009-07-06
I've been tasked with setting up a fax server.  I'd rather not spend money on a product in Windows.  I'd like to know what others have done for their environment.  I found this while googling:

[http://linuxgazette.net/issue79/fraile.html](http://linuxgazette.net/issue79/fraile.html)

However, there aren't detailed instructions.  I'd like to do something similar to his setup.  I want a samba printer that I can assign to a Windows machine as a normal printer.  When someone prints to it, they're sent an email to a webpage where they fill out destination phone number and asked for a cover page.  This would mean that the hylafax server would need to query AD for the users email address, then create a webpage specifically for that job.  I'm not really familiar with the querying process, let alone the scripting required for the "one-time" webpage.  Has anyone seen anything similar or something that would work well?  I'd prefer not having to install a piece of software on every machine that would need to fax.  I would also like all incoming faxes emailed to a certain address.  That person would be responsible for distributing faxes.  Thanks!

---

### Post by CNLiberal on 2009-07-11
Has anyone done anything similar to this at all?  How do others use linux as a fax server in a Windows environment?

---

### Post by HermanAB on 2009-07-11
Hylafax and email.

---

### Post by CNLiberal on 2009-07-12
Yes, I want to setup Hylafax and email.  However, how do you get Hylafax to send an email to the person that submitted the fax job?  Thanks!

Jim

---

### Post by CNLiberal on 2009-07-15
Does anyone have any ideas?  I'd love to use Ubuntu, but not if it won't deliver what I need.  Has anyone done anything similar to this?  Thanks!

Jim

---

