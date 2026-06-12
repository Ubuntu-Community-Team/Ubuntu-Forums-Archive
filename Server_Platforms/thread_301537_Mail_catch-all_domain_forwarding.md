---
title: "Mail catch-all domain forwarding"
date: 2006-11-17
forum: Server Platforms
---

### Post by kenzie on 2006-11-17
I'm running a web server with 6.06 and want to enable email domain forwarding with a catch-all without setting up a full blown mail server. So I would point a few domain.tld MXs at this box and the server could relay each email to an external address based on the domain.

i.e. mail to [email]*@internaldomain.tld[/email] is relayed to [email]john@externaldomain.tld[/email]

I have Postfix setup for internal SMTP only right now. Can someone explain the steps I need to take, or direct me to a resource with specific information? I don't seem to have the mail server vocabulary to search for what I'm looking for.

Thanks!

---

### Post by Child of Wonder on 2006-11-17
You need to set up virtual alias domains in Postfix.  Follow these directions.

[http://www.postfix.org/VIRTUAL_README.html#virtual_alias](http://www.postfix.org/VIRTUAL_README.html#virtual_alias)

It's pretty simply.  In /etc/postfix/virtual, just add the following for each domain:

@internaldomain.tld  [email]john@externaldomain.tld[/email]

---

### Post by kenzie on 2006-11-17
Exactly what I'm looking for, thanks! One more question; can I do this?

@internaldomain.tld  @externaldomain.tld

So that [email]joe@internaldomain.tld[/email] is mapped to [email]joe@externaldomain.tld[/email], and [email]jane@internaldomain.tld[/email] is mapped to [email]jane@externaldomain.tld[/email].

---

### Post by Child of Wonder on 2006-11-17
No, I think each address needs to be listed individually.

---

