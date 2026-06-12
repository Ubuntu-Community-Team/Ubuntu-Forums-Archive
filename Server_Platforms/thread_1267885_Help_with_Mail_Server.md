---
title: "Help with Mail Server"
date: 2009-09-16
forum: Server Platforms
---

### Post by LRT on 2009-09-16
Here is what I'm trying to do. We have a small network of about 20 users. We have an email host provider that we use for our email accounts. I want to be able to setup a server in our network that will be able to route emails from our network and destined for our network without having to go through our email host provider. So for example, if [email]user1@abc.com[/email] wants to send an email to [email]user2@abc.com[/email], the email will be routed inside our network and won't ever reach the host provider.

Hope this makes sense. Is this possible? I know very little about mail servers.

---

### Post by Lars Noodén on 2009-09-16
Take a look at any of these three MTA packages.  The result you are proposing is one of the options during the installation:

Dovecot
    [http://www.dovecot.org/](http://www.dovecot.org/)
Postfix
    [http://www.postfix.org/](http://www.postfix.org/)
Exim
    [http://www.exim.org/](http://www.exim.org/)


If you are looking for big, ugly all-in-one mail,calendar,contacts then the above will be a small component inside one of these:

Kolab
    [http://www.kolab.org/](http://www.kolab.org/)

Citadel
    [http://www.citadel.org/](http://www.citadel.org/)

Dingo Calendar Server
    [http://andrew.triumf.ca/dingo/](http://andrew.triumf.ca/dingo/)

Darwin CalendarServer
    [http://trac.calendarserver.org/](http://trac.calendarserver.org/)

Bedework
    [http://www.bedework.org/](http://www.bedework.org/)

---

### Post by LRT on 2009-09-16
thanks for your reply... i know i'm probably going to have to dive into some documentation for this since i've never done anything like this. out of the first three you mentioned (dovecot, postfix, exim) which one or (or maybe others) do you recommend for simple beginner setups?

---

### Post by ainsworth_t on 2009-09-16
If you're looking for documentation to help out with setting up a mail server, check out:
[LIST]Ubuntu Community Documentation - Servers: [https://help.ubuntu.com/9.04/serverguide/C/email-services.html](https://help.ubuntu.com/9.04/serverguide/C/email-services.html)
[/LIST]
[LIST]
[*]Ubuntu Server Guide - Email Services: [https://help.ubuntu.com/community/Servers#Mail,%20Groupware,%20and%20Chat%20Servers](https://help.ubuntu.com/community/Servers#Mail,%20Groupware,%20and%20Chat%20Servers)
[/LIST]

---

### Post by LRT on 2009-09-16
thanks.. i really would like to know if anyone has experience with what i'm trying to do (see post #1) and can perhaps provide some more detailed technical guidance if possible... thanks

---

### Post by noway2 on 2009-09-16
The programs mentioned in a post above, at least postfix and dovecot, serve different purposes, but work together to implement an email server.  Postfix is what is called an MTA, or mail transfer agent.  It acts as your SMTP server and receives incoming emails and files them for local delivery as well as forwarding outgoing emails to the next hop in the chain.  Dovecot implements the POP and IMAP functions to allow someone to retrieve their emails.  Chances are you would want both.

There are a number of threads in this forum on the subject to give you some material for initial research.  Hint: search for postfix and / or dovecot.  The posts will also reference many of the excellent how to documents to help get you started.

---

