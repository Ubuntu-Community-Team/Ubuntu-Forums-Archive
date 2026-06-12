---
title: "Postfix - send email to virtualmap and real user"
date: 2009-10-05
forum: Server Platforms
---

### Post by Wild-Storm on 2009-10-05
Hi. I created a CatchAll-Account by setting "virtual_maps" in main.cf to /etc/postfix/virtual with the following content: "@domain.de dvusr"

With this option all emails sent to "[wildcard]@domain.de" are forwarded to dvusr. I need this option because i installed an E-Mail Webfrontend ([www.b1gmail.com](www.b1gmail.com)) which supports online registration and works with CatchAll. Now i want to allow my users to access their emails by an external email-client via pop3.
Now, how can i "copy" the emails to the CatchAll-Account and send them as well to my User?

With kind regards

---

