---
title: "Viewing site if server is run virtually"
date: 2009-06-03
forum: Server Platforms
---

### Post by ticknubbs on 2009-06-03
Does anybody know if there is a way to view a site that is being built on ubuntu server running in virtual box in the regular host os web browser rather than on the server in the virtual box? Thanks.

---

### Post by LepeKaname on 2009-06-03
Just edit your /etc/hosts accordingly to the virtual IP your server has:

For example:

```
192.168.0.5   mytestserver.com mywebsite otherdomain.net
```

and so on...

---

