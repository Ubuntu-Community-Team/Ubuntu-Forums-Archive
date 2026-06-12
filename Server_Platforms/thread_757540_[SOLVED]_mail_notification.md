---
title: "[SOLVED] mail notification"
date: 2008-04-17
forum: Server Platforms
---

### Post by Kissell on 2008-04-17
I've tried to setup my file server to mail me if I have disk failures.  But it never works.  :(

my SMTP server belongs to my ISP, and it requires authentication and it doesn't use port 25.  

All the guides I've followed for sendmail or exim4 don't address the issues of authentication or alternate port usage.  

Please help!!!

#-o

---

### Post by hyper_ch on 2008-04-17
with postfix you can change the port easily... never used exim or sendmail

---

### Post by Kissell on 2008-04-18
I finally got it working...  I didn't need a full blown mail service, all i needed/wanted was a quick easy setup that would allow monitoring programs to send e-mail notifications to me when things break.  

I setup ESMTP for that...  extremely easy and quick, does exactly what I wanted, and nothing more, which makes it very uncomplicated.

put these lines into a /etc/esmtprc file and copied a ca.pem into ~/.authenticate folder, and was able to use TLS authentication with an external SMTP server while specifying the port, and not requiring I have my own domain registered on the internet (which this particular server does not)

        hostname="smtp.gmail.com:587"
        username="***.***@gmail.com"
        password="***"
        starttls=required

---

