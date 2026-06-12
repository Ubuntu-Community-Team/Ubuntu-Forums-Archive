---
title: "HA Heartbeat MailTo problem"
date: 2011-03-28
forum: Server Platforms
---

### Post by Mordachai on 2011-03-28
I have two virtual servers on 2 hyper-v machines for apache/php. I use heartbeat to failover from one to another in case the hardware fails. 

I would like to know when this happens so I added MailTo::myemail@address.com::ASimpleSubject to the end of the line in my haresources file. 

I know there isnt a mailserver installed on my Ubuntu VM's but I have an exchange installed in the same network. 

How can i make heartbeat send an email to my exchange instead of making sure my Ubuntu can send out mail?

---

### Post by calixtine on 2012-05-09
Old post .. but unanswered so ..

Not specifically a question to do with HA, but if you don't want to go to the trouble of configuring Postfix or another "heavy-duty" e-mail server :

 apt-get install nullmailer or something similar (msmtp?) and set up your Exchange server as your smarthost. 

In fact you can do this even if you don't have a handy Exchange server to use and just send the mail directly to your usual mail-server/e-mail address as nullmailer allows you to provide smtp credentials as well.

---

