---
title: "Email Archival"
date: 2010-01-26
forum: Server Platforms
---

### Post by computer13137 on 2010-01-26
Hey Ubuntu enthusiasts. :P  I've always had pretty good luck with getting responses to my questions from these forums...so I decided I'd come back and ask a new question. :)

The short version:
I'm running Sendmail as my MTA.  How do I archive all email messages forever?

The long version:
I'm setting up a web\email server for a small government organization.  They are required by law to maintain copies of all emails as public record, the same way any documents related to the township would have to be saved.  I would like an easy way to implement this kind of "total archival" of all emails.  Preferably both sent and received...preferably fairly easy to go back and access in case the need ever arises.  
I'd considered just setting up some kind of cron job to copy the mailboxes and maintain a snapshot backup, per say, but I don't know how much I'm inclined to want to go back to the raw files if there's ever a FOIA request for one of the emails.  It occurred to me that there might be software, or even a setting in Sendmail somewhere, which would make email archival an easy task.  I'm not familiar with anything like that.  In fact, this email server is the first time I've ever set up a mail server and so far everything is going smoother than I expected, I just need to find a way to save their emails because they're a government organization.
I installed Sendmail because I was slightly more familiar with it than Postfix.  I'd prefer an option for Sendmail.
I'd also prefer some nice, free open source software.  They're a small township.  Their server has RAID5, it's good enough.  I see no reason to buy some outside service to archive their emails when it should be a fairly easy task on the server itself.

I'd appreciate any thoughts anyone may have on how I could go about doing this reliably and with limited ease. :)  

Thanks!

Kirk

---

### Post by HermanAB on 2010-01-27
"Always BCC" is an option.

---

### Post by Grenage on 2010-01-27
Take a look at "mailarchiva" - it rocks.

---

