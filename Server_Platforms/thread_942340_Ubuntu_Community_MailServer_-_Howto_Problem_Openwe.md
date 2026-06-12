---
title: "Ubuntu Community MailServer - Howto Problem Openwebmail"
date: 2008-10-09
forum: Server Platforms
---

### Post by Paul_Ottar on 2008-10-09
Hi!

My question is fairly simple, but the problem gives med pain in the head!


I have installed OpenWebMail with the .deb packed. dpkg -- install openwebmail.package.thing.

In the HOWTO listed on the Community pages it is said that thats all you have to do.

Then I go to [http://mydomain.com/openwebmail](http://mydomain.com/openwebmail) to log in. But the URL does not show my LOGIN page. It just shows an exact replica of the [Http://openwebmail.org/](Http://openwebmail.org/) page!

Does anyone know if there is a magical solution to this?


best regards

Paul Ottar

---

### Post by Paul_Ottar on 2008-10-09
[http://komsys.hib.no/openwebmail/](http://komsys.hib.no/openwebmail/) <-- Should show a login page. But it does not.

Looked around, and found a file called redirect.html.
Tried komsys.hib.no/openwebmail/redirect.html
and that took me to [http://komsys.hib.no/cgi-bin/openwebmail/openwebmail.pl](http://komsys.hib.no/cgi-bin/openwebmail/openwebmail.pl)

everything seems to work now, but I want the login page to show in [http://komsys.hib.no/openwebmail/](http://komsys.hib.no/openwebmail/)

Any suggestions?

---

### Post by Paul_Ottar on 2008-10-09
deleted the index.html file and renamed redirect.html to index.html

had to change from maildir to mbox, since OWM dont support maildir

---

