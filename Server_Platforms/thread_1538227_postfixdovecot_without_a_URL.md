---
title: "postfix/dovecot without a URL"
date: 2010-07-24
forum: Server Platforms
---

### Post by Carleas on 2010-07-24
I'm setting up a postfix/dovecot server, but my URL is tied up in another server (I'm migrating).  I wanted to get postfix set up before I switch the URL over because it's my first time setting up an email server and I want to test it before it goes live.  Is there a way to set it up without the domain name, so that emails can be sent to/from the IP address, and then add the domain name later?

---

### Post by Bachstelze on 2010-07-24
No, email is largely dependent on DNS.  Can't you just set up an another A record in your domain for the new server?

---

### Post by Carleas on 2010-07-25
Something like 'mailtest.mysite.com'?  Would I need both an A record and an MX record, or would I put the MX record on the new server?

---

### Post by Bachstelze on 2010-07-25
> **Carleas said:**
> Something like 'mailtest.mysite.com'?  Would I need both an A record and an MX record, or would I put the MX record on the new server?

You need an A record on the IP of the new server, then to change the MX record from the old server to the new one.

---

