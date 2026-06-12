---
title: "SMTP enabled?"
date: 2008-08-19
forum: Server Platforms
---

### Post by CrusaderAD on 2008-08-19
How do you enable smtp on a ubuntu linux server? I know in IIS it's just a matter of checking an enable feature.

---

### Post by Ximbiot on 2008-08-19
> **raptormanad said:**
> How do you enable smtp on a ubuntu linux server? I know in IIS it's just a matter of checking an enable feature.

I'm not sure exactly what you are asking for here.  Any SMTP client should work out of the box.  If you are looking to add a mail server to queue and forward only local SMTP requests, you can try installing the nullmailer package:

```
apt-get install nullmailer
```

If you need a full-blown mail server, you can try installing the postfix package, but mail server configuration configuration tends to be pretty complicated:

```
apt-get install postfix
```

---

### Post by windependence on 2008-08-19
Maybe he means SNMP?

-Tim

---

### Post by CrusaderAD on 2008-08-20
> **Ximbiot said:**
> I'm not sure exactly what you are asking for here.  Any SMTP client should work out of the box.  If you are looking to add a mail server to queue and forward only local SMTP requests, you can try installing the nullmailer package:

```
apt-get install nullmailer
```

If you need a full-blown mail server, you can try installing the postfix package, but mail server configuration configuration tends to be pretty complicated:

```
apt-get install postfix
```

I'll give these a shot. We need an smtp server installed on our LAMP server.

---

