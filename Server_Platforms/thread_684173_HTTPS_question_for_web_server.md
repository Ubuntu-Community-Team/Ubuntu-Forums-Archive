---
title: "HTTPS question for web server"
date: 2008-01-31
forum: Server Platforms
---

### Post by behrk2 on 2008-01-31
Hey guys,

I am running Ubuntu Server 6.06 (LAMP).

I am trying to put a server into production at my school, but first I was told to: "enable https on the server so that at the very least authentication credentials aren't sent in cleartext over http on form submission."

So, I have played around with a bunch of SSL stuff, and I have tried tons of tutorials, but I have gotten nothing to work successfully.

Is SSL even the same thing as enabling https? Or is that going further than what I need done?

Can someone please explain this to me, and perhaps point me in the direction of a good tutorial?

Thanks!

---

### Post by cdenley on 2008-02-01
In order to use SSL encryption, you need to configure apache to use your certificate. You can use a self-signed certificate, but then a user will be alerted that it is self-signed, and will not be able to verify that it is actually your site that is providing that certificate. I don't think there is any way to get an SSL certificate which is signed by a certificate authority for free.

Tutorials aren't hard to find. I used instructions from the site where I purchased my SSL certificate.

---

### Post by James79 on 2008-02-01
Have a look [here]("https://help.ubuntu.com/community/forum/server/apache2/SSL").

---

### Post by Rick Z on 2008-02-22
Thank you James79, I follow the link and got the redirection working.

---

