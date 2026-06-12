---
title: "How to send email to external systems?"
date: 2012-08-16
forum: Server Platforms
---

### Post by le_jawa on 2012-08-16
Just a quick question:

What needs to be done to get the mail agent to send mail to accounts external to the Ubuntu server?  I know in Fedora/RH you had to add a package to get sendmail to communicate with the outside world, but what about on Ubuntu?

Thank you,

Jason

---

### Post by LHammonds on 2012-08-16
I use the package called sendemail

See my sig for some of my servers that use it.

With an extra library or two you can even have it make use of gmail!

LHammonds

---

### Post by le_jawa on 2012-08-17
LHammonds,

Thanks for the response.  I kept troubleshooting the problem and discovered that my SMTP config on the server was off and that our internal DNS wasn't setup correctly.  After I fixed that, everything worked great.

---

