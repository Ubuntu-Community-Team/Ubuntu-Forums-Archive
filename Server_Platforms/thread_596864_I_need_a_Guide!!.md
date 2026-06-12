---
title: "I need a Guide!!"
date: 2007-10-30
forum: Server Platforms
---

### Post by notaloafer on 2007-10-30
Right now I have the following apps installed for my mail server (they are all working perfectly)

[LIST]
Postfix
Postfix SMTP-Auth
Courier-IMAP
Courier-SMTP
[/LIST]

They are all working perfectly fine and everyone is enjoying the email server. What I need to do is upgrade to MySQL-Stored virtual users (yes I have MySQL installed already). I need this because I'm dealing with several domains and need a easier way to administrate users rather than just creating linux system users for all my mail accounts.

What would be a good tutorial to accomplish this? I tried a few on this website but they all want me to use dovecot, or different mail programs to accomplish the same thing. Is there any tutorial that I can use to add on to my installation or do I need to start from scratch again?

Thanks
-Eric

---

### Post by rbprogrammer on 2007-10-30
yes, i would want to go through a tutorial on those as well. :guitar: that would be very helpful on my server.

i hope some one knows of a good one, or at least one..

---

### Post by HermanAB on 2007-10-30
See the postfix website.  There are lots of good howto guides.

I have used postfix exclusively for the past 5 years, but recently abandoned it, since it is just too much trouble to configure and maintain it.  You should look into Citadel: [http://www.citadel.org](http://www.citadel.org)  It is very easy to install, uses a BerkeleyDB database back-end (you can have 256 TB of mail!) and it is zero maintenance.

The reason postfix became popular, was because it is a plug in replacement for sendmail, which is a total abortion.  Postfix is a good learning experience, but there are much better ways to do things.

---

### Post by notaloafer on 2007-11-02
[http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

AWESOME GUIDE!

---

