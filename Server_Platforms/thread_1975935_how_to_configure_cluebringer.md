---
title: "how to configure cluebringer ?"
date: 2012-05-08
forum: Server Platforms
---

### Post by yavuz.maslak on 2012-05-08
hello 
i have a ubuntu12.04 lts server.
is there a document about cluebringer ( conf, examples, howto )?
you know it is built on the server but i can't use its throttling feature.

---

### Post by anonymouschief on 2012-05-08
> **yavuz.maslak said:**
> hello 
i have a ubuntu12.04 lts server.
is there a document about cluebringer ( conf, examples, howto )?
you know it is built on the server but i can't use its throttling feature.

"**Policyd v2** (codenamed "**cluebringer**") is a multi-platform policy server for popular MTAs."

Please check here: [http://www.policyd.org/content/installation]("http://www.policyd.org/content/installation")

---

### Post by yavuz.maslak on 2012-05-09
Thank you I read it but it seems a bit old. it mentions accounting in cluebringer.conf. Yet there is no longer that feature in the  cluebringer.conf. Besides i set some values for throttling over [https://serverip/cluebringer](https://serverip/cluebringer) i can't run throttling.

is there any fresh documents or conf ?

---

### Post by yavuz.maslak on 2012-05-19
Hi 

I can manage to run throttling.
But I can't do "defer operation" 
I use [http://serverip/cluebringer](http://serverip/cluebringer) and quotas tab
if I select DEFER to delay for mails exceeded the limit at the verdict.
postfix rejects mails exceeded my limit
Namely cluebringer behaves as reject about that.

How can I fix the issue ?

---

