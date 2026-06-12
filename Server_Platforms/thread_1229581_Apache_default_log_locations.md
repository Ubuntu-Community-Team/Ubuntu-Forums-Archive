---
title: "Apache default log locations"
date: 2009-08-02
forum: Server Platforms
---

### Post by cmwslw on 2009-08-02
Right now my VirtualServer tags contain things like 
```
ErrorLog /var/log/apache2/pro.error.log
LogLevel warn
```
But I was wondering if I could just leave these out and use the default location if there was one. So what is the default ErrorLog location and what is the log level?

Thanks in advance
-cory

---

### Post by zemon_ on 2009-08-02
var/log/apache2/error.log

---

### Post by cmwslw on 2009-08-02
Thanks for answering my noob question

---

### Post by cmwslw on 2009-08-02
Sorry for the second post, but is there a default access.log?

---

### Post by credobyte on 2009-08-02
List of all Apache log files ( some might be somewhere else .. depends on your configuration ):
```
cd /var/log/apache2 && ls -l

```

---

