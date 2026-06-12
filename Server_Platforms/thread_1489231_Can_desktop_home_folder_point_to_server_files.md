---
title: "Can desktop home folder point to server files?"
date: 2010-05-20
forum: Server Platforms
---

### Post by Lori700698 on 2010-05-20
I was curious if I could have the home folder system from a desktop install point to a set of home folders over on the server?  It would streamline my backups and make files a bit more central for accessing.  

Thanks
Lori

---

### Post by HermanAB on 2010-05-21
Yup, search for "NFS home" on [http://google.com/linux](http://google.com/linux)

There is probably a suitable NFS howto at [http://tldp.org](http://tldp.org) as well.

---

### Post by Lori700698 on 2010-05-21
Outstanding solution!  Thank you, took a couple hours because I read through a few How-To-Files to get the whole picture.  This brings up a new question, if I wanted to replace my home folder on my laptop with a home folder on the server all would be fine while I'm on my network, what happens when I'm out?  Is there a way to get it from outside?  I see I would need to open a port, but where would I point to a [http://www.mydomain.com:111](http://www.mydomain.com:111), then how do I check back with the /etc/export because my internal IP would not be right, could I use a mac address or does that change too?

Thanks..sorry I always seem to have more questions:???:
Lori

---

### Post by HermanAB on 2010-05-22
Howdy,

Do not run NFS over the internet - it is for LAN use only (insecure!).  Over the internet, use SSH and 'rsync -e ssh ...'.

Mounting remote directories over NFS requires a static setup, otherwise you'll have trouble each time you boot up and that will get boring pretty quickly.

Regards,

Herman

---

