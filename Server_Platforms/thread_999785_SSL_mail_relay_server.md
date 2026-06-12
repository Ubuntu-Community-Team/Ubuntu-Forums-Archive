---
title: "SSL mail relay server"
date: 2008-12-02
forum: Server Platforms
---

### Post by jontz on 2008-12-02
Here's the situation:

I have 6 Lanier multi function copier/fax machines that can send faxes by email.  We don't have an email server at the school I work at, we use google for our email.  In order to send email through google via smtp, you have to use SSL, which the Laniers don't support.  Is it possible to set up a Ubuntu mail server to relay the plain email fax from the Lanier and send it SSL to google?  How would I go about it?  Thanks!

---

### Post by MJN on 2008-12-02
Sure, use Nullmailer. It is a lightweight relaying mail service with full support for SSL and authentication.
 
Install it, configure it to work with Google's mail servers, and point your Lanier's at it.
 
Mathew

---

### Post by jontz on 2008-12-09
Thanks for the info, I appreciate it.

---

