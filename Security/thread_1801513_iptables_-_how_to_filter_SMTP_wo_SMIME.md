---
title: "iptables - how to filter SMTP w/o S/MIME"
date: 2011-07-10
forum: Security
---

### Post by johnbiddle on 2011-07-10
Does anyone know the iptables statement that will block inbound SMTP messages that are NOT S/MIME encrypted?  Thanks

---

### Post by SeijiSensei on 2011-07-11
I doubt you can do that with iptables.  At best you might find a way to configure the SMTP server to do this.  However tossing away messages for arbitrary reasons like this generally runs afoul of the RFC specifications for mail handling, so it may be hard to find a standards-complaint mail server that will do this for you.

You could throw them away in the delivery phase using [procmail]("http://www.procmail.org/").  Tell it to route any messages without an S/MIME header to /dev/null.

---

