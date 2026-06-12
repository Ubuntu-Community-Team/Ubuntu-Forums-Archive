---
title: "mysql: confusing package information"
date: 2009-12-28
forum: Server Platforms
---

### Post by manolo_asdf on 2009-12-28
after having queried to know which mysql server is installed i get:
5.1.30really5.0.75-0ubuntu1

what does this mean (5.1 vs really5.0)? is it a special ubuntu version. or is the downgrade naming to 5.0 a workaround for other package dependencies?

thanks.

---

### Post by phillw on 2009-12-28
Hi... TBH- I'm not sure

```
mysql -V
``` reports back that I have
> mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (i486) using  EditLine wrapper


But, then again, I'm running 10.04 alpha of Ubuntu - Are you on 9.10 ? If so, I'll pop onto 9.10 and see what it reports & what the latest in Synaptic is.

Regards,

Phill.

---

### Post by manolo_asdf on 2009-12-30
thanks 'mysql -V', shows:

mysql  Ver 14.12 Distrib 5.0.75, for debian-linux-gnu (x86_64) using readline 5.2


still weird why they use 5.1.xxx naming in package...

---

