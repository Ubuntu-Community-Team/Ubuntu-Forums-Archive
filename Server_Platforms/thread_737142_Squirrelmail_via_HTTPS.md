---
title: "Squirrelmail via HTTPS"
date: 2008-03-27
forum: Server Platforms
---

### Post by chrismyers on 2008-03-27
Hi Guys,
 
Does anyone know of a good how-to for getting Squirrelmail to use HTTPS?
 
 
Docs seem to be sparse on the subject. 
 
I searched the net & Found:
 
[http://www.differentpla.net/content/2004/03/securing-squirrelmail-using-https](http://www.differentpla.net/content/2004/03/securing-squirrelmail-using-https)
 
But this refers to the directory:
 
/var/www/webmail
 
This directory does not exist.
 
I'm a bit stuck now. Can anyone help?

---

### Post by anthony.rasat on 2008-03-27
Your question seems will have two answers: One, how to install Squirrelmail. And two, how to setting up a HTTPS webserver.

Well for question one, if you don't mind the rough edges (read: quite long explaination) you may want to check out [Qmailrocks]("http://www.qmailrocks.org"), on section for Debian. It shouldn't be too differ from Ubuntu.

For question two, just Google it a bit, there's lots of useful tips to configure a HTTPS webserver.

Now, apart from those, I think I may points out that there is full blown mail server application -- opensource / free as well as commercially supported -- called [Zimbra]("http://www.zimbra.com") which also capable of HTTPS among lots of other things. And I should emphasize one neat feature of this Zimbra: It has Ubuntu installer.

---

### Post by chrismyers on 2008-03-28
Hi anthony,
 
Sorry. I wasn't clear in my explanation.
 
I allready have a working squirrelmail. I just need to get it to work via https rather than http.
 
I'm googling for squirrelmail https & squirrelmail ssl, which isnt giving me much help.
 
Do you have any tips/links/search keywords?
 
Cheers.

---

### Post by keithweddell on 2008-03-28
Have a look in /etc/squirrelmail/apache.conf.  There are some lines commented out that can be used to redirect squirrelmail to HTTPS.


Keith

---

