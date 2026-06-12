---
title: "Courier Email Aliasing?"
date: 2006-10-04
forum: Server Platforms
---

### Post by backu on 2006-10-04
I have a working version of Courier + eGroupWare running on my system. However, I haven't been able to get the system to forward email from [email]address1@host.tld[/email] to [email]address2@host.tld[/email]. Can anyone help me get this figured out so that I can have email forwarded?

---

### Post by kidders on 2006-10-05
What's handling your SMTP?

If it's postfix for instance, you could maybe use the "alias_maps" or "alias_database" directive.

---

### Post by backu on 2006-10-07
I'm not sure, it's the entire Courier Package.

---

### Post by kidders on 2006-10-07
Hmmm... Courier SMTP isn't something I'd use, out of choice. I found this, however:

[http://www.courier-mta.org/?makealiases.html](http://www.courier-mta.org/?makealiases.html)

One of the ways of forwarding mail from one address to another within the same domain, is to use aliasing.

I hope this is more helpful than my last post!

---

