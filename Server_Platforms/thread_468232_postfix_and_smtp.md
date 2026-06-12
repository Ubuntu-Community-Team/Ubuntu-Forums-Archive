---
title: "postfix and smtp"
date: 2007-06-08
forum: Server Platforms
---

### Post by bibawa on 2007-06-08
Hello!

This is  my first post here so I hope i've places this in the wright forum.

I've a problem with my postfix configuration, i've installed everything to work with rollernet.us, my server receives mail on port 9999 from rollernet.

The receiving part works fine.

To made the mailserver listen to port 9999 for receiving i've to change a line in /etc/services ..

For the sending part I will use the smtp server of my ISP ( uit.telenet.be ).
When I now send an email from my mailserver I'll see the error "No route to host " in my mail.log.. I think also the outgoing mail takes the 9999 port..

How can I change this so that the outgoing part listens to port 25 instead of 9999?


Kinds regards!

---

### Post by Mr. C. on 2007-06-08
Don't change /etc/services port 25.  It is SMTP, and as you found it, is used by postfix for outbound connections as well.

You want to configure another smtpd listener service in master.cf instead:

9999     inet  n       -       n       -       -       smtpd

restart postfix afterwards.

MrC

---

### Post by bibawa on 2007-06-09
Can somebody post the original /etc/services ? so that I can replace it :)

---

### Post by Mr. C. on 2007-06-09
Attached.

---

