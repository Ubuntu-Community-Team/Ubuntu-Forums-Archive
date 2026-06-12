---
title: "[SOLVED] I can't view my site no more"
date: 2008-11-06
forum: Server Platforms
---

### Post by Fertech on 2008-11-06
I had my website up and running, but today i try to view my website, and it was down. i check dyndns, and thats was good. i type 127.0.0.1 it said page can't be found. i type localhost same thing. the only thing i try to do is run my email server with apache, mysql, php postfix.

---

### Post by cariboo on 2008-11-06
What is the output of /var/log/apache2/error.log? Are there any obvious errors? Did you make any changes to your web site?

Jim

---

### Post by Fertech on 2008-11-06
i figure it out it was the apache it was not off. i just needed to start the apache.

---

