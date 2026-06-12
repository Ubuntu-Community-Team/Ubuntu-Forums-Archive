---
title: "problem in installing openvas-server"
date: 2008-08-29
forum: Security
---

### Post by mails4nilesh on 2008-08-29
Hi All,

I am facing problems in installing openvas-server on ubuntu-7.10

I had installed nessus-libraries, openvas-libraries, openvas-libnas* and  openvas-server.  After installation, I got an error of "libraries".  Can anyone faced any problems while installing OPENVAS in Ubuntu-7.10

---

### Post by mwiegand on 2008-09-05
> **mails4nilesh said:**
> Hi All,
I had installed nessus-libraries, openvas-libraries, openvas-libnas* and  openvas-server.  After installation, I got an error of "libraries".  Can anyone faced any problems while installing OPENVAS in Ubuntu-7.10

I haven't tried installing openvas-server on 7.10 yet (which packages are you using?), but it could be nessus-libraries conflicting with openvas-libraries. Openvas-server does not need nessus-libraries anymore since they are (for the most part) just older versions of openvas-libraries.

Does this solve your problem?

Regards,

Michael

---

### Post by qwertyytrewq on 2009-02-06
I cant install the openVAS server, the repos don't support it as they do with the client. I am using ubuntu 8.10

---

### Post by wirelessmonkey on 2009-02-06
The OpenVAS site docs say that OpenVAS is still being ported to Debian based distributions, you can build it yourself, or wait until a package is available.

---

### Post by adam98 on 2009-02-07
Can you give instructions (for dummies) how to built it myself?

---

### Post by hackertarget on 2009-07-02
Ask and you shall receive.  :)

I put together some notes for openvas from source on Jaunty.

[http://hackertarget.com/2009/06/guide-to-openvas-on-ubuntu-904/](http://hackertarget.com/2009/06/guide-to-openvas-on-ubuntu-904/)

---

