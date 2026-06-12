---
title: "Creating spam filtering mail proxy."
date: 2009-05-21
forum: Server Platforms
---

### Post by Robmonster on 2009-05-21
Morning all,
   
  I'm looking to use Ubuntu to create a spam filtering mail proxy for my small company.
   
  WE currently pull in email from a multidrop pop3 address which gets delivered directly into Exchange 2003.
   
  I'd like to create a new server that can sit in the middle of that process filtering all mails, running them through SpamAssassin and then delivering them into Exchange again for the end users to manually filter.
   
  Can someone please guide me which packages I need to install, and an overview of how to get them to accept mail, pass it to SA and then pass the results on to the Exchange server?
   
  I've tried working this out on my own, but so far I have not been very successful. I can get an exim server to accept the mail, but it tries to delivery it locally, and I cannot get it to just pass the message through to Exchange for storage.
   
  Any help gladly received,
   
  Rob

---

### Post by ephmanjmm on 2009-05-21
This uses SA and more:

[http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04](http://www.howtoforge.com/the-perfect-spamsnake-ubuntu-8.04)

There are other how-tos there for spam assassin as well.

---

