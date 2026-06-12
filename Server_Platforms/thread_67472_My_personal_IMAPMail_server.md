---
title: "My personal IMAP/Mail server"
date: 2005-09-20
forum: Server Platforms
---

### Post by kivu on 2005-09-20
Despite all available howto's walkthroughs and other documentation I could not find a straightforward description to setup fetchmail, postfix and cyrus imap server togehter on a Ubuntu machine (Hoary 5.04 installed as server).

Therefor I created my own doc [http://home.kivu.nl/imap_setup.html](http://home.kivu.nl/imap_setup.html)
from many other docs.

Hope it is usefull for Ubuntu users.

I have a few POP3 accounts which I can now access from every location with my laptop and soon by webmail too.

Still todo setting up Squirrelmail for webmail access and some spam filtering but for now it works fine. MediaWiki would be nice too, should be easy to write stuff on my site.

---

### Post by dcostelloe on 2005-09-20
Thanks been looking for something like this.

 \\:D/

---

### Post by kivu on 2005-09-21
I have added some explanation about Postfix and SASL authentication to the doc. I forgot to mention that you have to disable chroot mode for smtp, otherwise you have to go through a great deal of hassle to get it working.

On the Postfix site it also advised to not run in chroot mode if you want to use SASL authentication.

---

### Post by kivu on 2005-09-21
Sorry my server is down because of a power outage :( will be up in a few hours or so.

---

