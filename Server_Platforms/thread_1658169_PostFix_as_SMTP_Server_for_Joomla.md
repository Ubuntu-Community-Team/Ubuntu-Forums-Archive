---
title: "PostFix as SMTP Server for Joomla?"
date: 2011-01-02
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-01-02
Hi everyone, thats my first message here :p

I am setting up an ubuntu server, in order to use it with Joomla.

Does someone knows if is possible to use PostFix as SMTP server for Joomla? :confused:

If does; would be necessary to install IMAP or POP3, Webmail etc if I just want to send automatics mails via Joomla.

Thanks in advance :p

---

### Post by jgedeon on 2011-01-02
Yes you can set up Postfix as a SMTP server for joomla.  Joomla would be set to use local host as the smtp server.  Postfix will then be set up as a Satellite System and use a SMTP Relay Host.  You may need to set up authentication to use your SMTP Relay Host.

---

### Post by Calimo on 2011-01-02
Hi acastrolorenzo!

Postfix is just a server implementing the [SMTP](Simple Mail Transfer Protocol) protocol. And Joomla needs just any SMTP server. Both will work fine, but you could really use any SMTP server here: qmail, exim, sendmail, etc.

The SMTP server is used to send messages. It will make sure they arrive to the destination host. This host may be a file on your system. IMAP and POP are for retrieving messages after they are received on your server. If you intend to receive messages, then you need either an IMAP or a POP server. But if you'll use Joomla to send messages to your users or visitors, it is not your job to setup the reception: that will be handled elsewhere!

---

### Post by acastrolorenzo on 2011-01-02
Thanks :)

---

