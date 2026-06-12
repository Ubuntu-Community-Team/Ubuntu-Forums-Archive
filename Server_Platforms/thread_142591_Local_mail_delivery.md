---
title: "Local mail delivery"
date: 2006-03-10
forum: Server Platforms
---

### Post by shamrock_uk on 2006-03-10
Not quite sure if its the right forum, but we don't appear to have a mail or networking one! 

Mostly for my own education, I'm trying to make use of native linux tools to fetch my email and archive it on the hard drive. I've successfully retrieved it using fetchmail and the imap protocol...judging by the output all has gone well. 

I've installed sendmail which I think is now my local MTA, but having a bit of a problem finding where my mail has been sent / how to set it up so it delivers correctly. 

Judging from searches, I was expecting to find a folder in /var/spool/ but nothing has appeared (or in /var/mail either). 

I've investigated several walkthroughs for setting up sendmail, but they all seem excessively complicated as I only need the server for local deliveries. All the walkthroughs want lots of information about domains and a static IP, none of which I have at present or seem relevent.

If anyone could point me in the right direction re. any of the following, that would be great!

1) A link to a walkthrough/howto on setting up sendmail (or another MTA) purely for local delivery.

2) A command to check/change the current MTA...I've seen ```
alternatives --config mta
``` for a FC4 system, but nothing equivalent for Ubuntu.

3) A quick description of where my local mail will end up. 

4) If it's nice and simple, a quick point towards the right config file and what information will be needed would be very helpful!

Thanks in advance :)

---

### Post by Glut on 2006-03-12
The best fix is to remove sendmail and replace with something nicer. The sendmail config files - even when using m4 are a good way to give yourself a headache. I strongly recommend something like postfix. Exim is popular, too. 
1) If you insist on sendmail, any config walkthrough will do. A quick google points to this one: [http://www.create3.com/sendmail.html#sendmail](http://www.create3.com/sendmail.html#sendmail) I have no idea if it's any good. If you must continue configuring, O'Reilly publishes a decent sendmail book. Buy that and the 8.13 addendum.
2) From memory, aptitude only allows one MTA to be installed at a time. telnetting to port 25 should confirm.
3) /var/mail/*username*
4) you need to edit /etc/mail/sendmail.mc and some other files. There is no easy way to configure sendmail by hand (try installing webmin or something if you must use sendmail) I strongly recommend another mail agent, think of the children!

---

### Post by shamrock_uk on 2006-03-19
Sorry Glut, I seem to have completely missed your message. 

I had actually moved on from sendmail in the end, and currently have postfix installed. I'm about 80% towards getting it all working perfectly, got a busy week ahead but will see if I can't nail it after that. 

Thanks for the advice :)

---

