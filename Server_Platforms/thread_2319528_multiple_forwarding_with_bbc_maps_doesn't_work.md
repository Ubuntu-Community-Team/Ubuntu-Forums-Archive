---
title: "multiple forwarding with bbc_maps doesn't work"
date: 2016-04-05
forum: Server Platforms
---

### Post by lukas34 on 2016-04-05
Hi,
I'm trying to forward to multiple mail addresses when sending to one using recipient_bcc_maps.** It works when using one-to-one forwarding. **
When I try to use more than one recipient like this:
```
to-all@domain.com 1@domain.com 2@domain.com 3@domain.com
```
or this:
```
to-all@domain.com 1@domain.com, 2@domain.com, 3@domain.com
```
it doesnt work anymore.
Any suggestions welcome :)

---

### Post by lisati on 2016-04-05
According to the [Postfix documentation]("http://www.postfix.org/postconf.5.html#recipient_bcc_maps"), multiple results for a lookup aren't supported.

---

### Post by Graham_Willis on 2016-04-05
I didn't really test this configuration but you may find the following discussion useful:

[http://stackoverflow.com/questions/22537523/postfix-recipient-bcc-maps-multiple-recipients-how-to](http://stackoverflow.com/questions/22537523/postfix-recipient-bcc-maps-multiple-recipients-how-to)

---

### Post by lukas34 on 2016-04-06
that solved it. thx!

---

