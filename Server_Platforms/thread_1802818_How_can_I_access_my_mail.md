---
title: "How can I access my mail?"
date: 2011-07-12
forum: Server Platforms
---

### Post by Cloudaz on 2011-07-12
I have setup Postfix as my SMTP server.

I sent myself a test mail from the outside world, and I can see it in the mail spool in '/var/mail'. The question is, how can I now access that from a mail client?

---

### Post by dino99 on 2011-07-12
usually we use either Evolution or Thunderbird

---

### Post by philinux on 2011-07-12
> **Cloudaz said:**
> I have setup Postfix as my SMTP server.

I sent myself a test mail from the outside world, and I can see it in the mail spool in '/var/mail'. The question is, how can I now access that from a mail client?

Is this a server setup or desktop.

Either way this might help.
[http://www.zulius.com/how-to/set-up-postfix-with-a-remote-smtp-relay-host/](http://www.zulius.com/how-to/set-up-postfix-with-a-remote-smtp-relay-host/)

---

### Post by Cloudaz on 2011-07-12
My box is the server.

---

### Post by philinux on 2011-07-12
> **dino99 said:**
> usually we use either Evolution or Thunderbird

But not on a Server. :)

---

### Post by Cloudaz on 2011-07-12
Huh? My box is my PC - which is a server. I just want to be able to access my mail via IMAP. How can it be done with Linux? On Windows I am using Mercury Mail. Now I want to migrate to Linux.

---

### Post by Cloudaz on 2011-07-12
How can I allow relaying of mail for a single IP address with Postfix?

---

### Post by philinux on 2011-07-12
Threads Merged. Please don't start duplicate threads.

---

### Post by SeijiSensei on 2011-07-12
> **Cloudaz said:**
> I sent myself a test mail from the outside world, and I can see it in the mail spool in '/var/mail'. The question is, how can I now access that from a mail client?

I think the best command-line client is **alpine**.  You can even have it open an mbox folder directly from the filesystem.  It has nice menus at the bottom as well.

If you're talking about using a remote client like Thunderbird, you need to install a POP/IMAP server like **dovecot**.

---

