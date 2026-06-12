---
title: "phplist woes"
date: 2011-11-01
forum: Server Platforms
---

### Post by clegends on 2011-11-01
Hi everyone, having major dramas with my phplist installation.... I just don't understand what's gone wrong. It's been working beautifully for the past month, until trying to send out this last email...

I have been sending out regular emails to our 700+ database, and seems, until now, to have gone fine. Before sending out each email, I click the 'test' button to send it to myself first. For some reason now, I can ONLY receive this as a plain text email, and not as an html. Previously, there has been no problem receiving this as an html email. Furthermore, sending this test email hangs my system... the page won't reload, and I can't log out, or log back in, until I restart apache with: sudo /etc/init.d/apache2 restart

I have tried wiping the database and recreating it from scratch, then wiping the whole install and reinstalling the most recent version of phplist (now .17, I was using .15), and no change whatsoever. The only thing I haven't tried was wiping the database, wiping the install, and trying both again from scratch... 

Any idea what the heck could be going on, and what else could have gotten corrupted to use this? I am running 10.04.1 Ubuntu Server. Thanks in advance for your help, this is driving me nuts.

---

### Post by shubham1 on 2011-11-01
> **clegends said:**
> Hi everyone, having major dramas with my phplist installation.... I just don't understand what's gone wrong. It's been working beautifully for the past month, until trying to send out this last email...

I have been sending out regular emails to our 700+ database, and seems, until now, to have gone fine. Before sending out each email, I click the 'test' button to send it to myself first. For some reason now, I can ONLY receive this as a plain text email, and not as an html. Previously, there has been no problem receiving this as an html email. Furthermore, sending this test email hangs my system... the page won't reload, and I can't log out, or log back in, until I restart apache with: sudo /etc/init.d/apache2 restart

I have tried wiping the database and recreating it from scratch, then wiping the whole install and reinstalling the most recent version of phplist (now .17, I was using .15), and no change whatsoever. The only thing I haven't tried was wiping the database, wiping the install, and trying both again from scratch... 

Any idea what the heck could be going on, and what else could have gotten corrupted to use this? I am running 10.04.1 Ubuntu Server. Thanks in advance for your help, this is driving me nuts.
id mail server using htmlenttities over coming mails
[http://www.w3schools.com/php/func_string_html_entity_decode.asp](http://www.w3schools.com/php/func_string_html_entity_decode.asp)

---

### Post by clegends on 2011-11-01
Hi shubham1, thanks for that. I have looked at that page, however I don't understand what you mean. Are you able to elaborate for me? I am receiving other html mail fine both in my email client and from my server. Having a look at the message source of the email from phplist, it is not in html, but only in plain text. Currently I have set phplist to send out mail itself, rather than route through an smtp server. I would appreciate your further advice, and anymore elaboration. Thanks!

---

