---
title: "Limit Website access upto specific count"
date: 2013-10-17
forum: Security
---

### Post by chintan2 on 2013-10-17
Hii to all,

I am new to Linux. but i am facing issue with my web server in Ubuntu 11.10.

In my webserver i want to restrict maximum users website access (e.g., suppose i want to restrict users to access web to 250 persons in single time). So can you please suggest me to how to do that in Apache bases web server.

---

### Post by SeijiSensei on 2013-10-17
[http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxclients](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#maxclients)

How many clients are permitted by default depends on how you have the server configured.  Usually the default is 256.

---

### Post by Bucky Ball on 2013-10-17
As this is posted in ***Security Discussions***, I will state the obvious: 11.10 is not supported and doesn't receive updates, including security updates. Advisable to stick with LTS releases for servers and production machines. ;)

---

### Post by chintan2 on 2013-10-17
Thanks SeijiSensei,

Your link helped me to solve issue.

Thanks

---

### Post by Bucky Ball on 2013-10-17
Please mark it as solved then from Thread Tools at top right to help others. Obviously running a vulnerable server is of no consequence to you. Good luck. ;)

---

