---
title: "Cant send emails"
date: 2014-08-26
forum: Server Platforms
---

### Post by bsrcube on 2014-08-26
Hi all,

I am trying to setup a mail-server using "sendmail + dovecot and squirrelmail" setup. 
I have followed the instructions given here - [http://shootthiscomputer.com/edu/sendmailubuntu/](http://shootthiscomputer.com/edu/sendmailubuntu/)

This setup is for a lab in an institute.

Most of it seems to work fine, 
- Mails can be received & sent among different users in the domain (ex: [EMAIL="xyz@mylab.mydept.com"]xyz@mylab.mydept.com[/EMAIL] or [EMAIL="abc@mylab.mydept.com"]abc@mylab.mydept.com[/EMAIL])
- Mails can be received & sent to different labs and departments too (ex: [EMAIL="jkl@mydept.com"]jkl@mydept.com[/EMAIL] or [EMAIL="bnm@somelab.somedept.com"]bnm@somelab.somedept.com[/EMAIL] or [EMAIL="ert@difflab.mydept.com"]ert@difflab.mydept.com[/EMAIL])
- Mails can be received from other domains (tested by sending mails using gmail & yahoo ids)
- Mails can't be sent out to other domains (cant send it to gmail or yahoo. Maybe others too?)

The mailq output mostly contains mails that are to be sent to gmail ids along with the message below,
"(delivery temporarily suspended: alt2.gmail-smtp-in.l.google.com[2404:6800:4003:c01::1a]:25, network is unreachable)"

How do I send out mails to other domains? (I hope I am using the right terms, here I mean gmail or anything outside of our institute)
If any more information is needed, please let me know. 

P.S: I am comfortable with Ubuntu/linux. However, a total noob for server setup kinda work, got into it couple of days ago.

---

### Post by bsrcube on 2014-08-26
Dear All,

I figured it out. The relay host value was missing. After making appropriate entries and restarting the service.
Its all fine.

---

