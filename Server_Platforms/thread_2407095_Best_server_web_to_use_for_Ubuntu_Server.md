---
title: "Best server web to use for Ubuntu Server?"
date: 2018-11-29
forum: Server Platforms
---

### Post by juanferaviles on 2018-11-29
Good afternoon, according to your experience with Ubuntu Server 18.04, what do you think is the best web server to use?

---

### Post by TheFu on 2018-11-29
"Best" is highly subjective.  Depends on the required tasks. 

 Sometimes a minimal perl or python web server is best. Sometimes Apache and sometimes nginx.  Pick the right tool for the right task.  Are you running static pages?  A web-app in a specific language?  Do you need to host multiple virtual domains?  What about SSL considerations?  Are multiple IPs available or just one?  Does language support matter?  Any need for CGI support?

See the issue? "Best" is different for each specific use.

---

### Post by SeijiSensei on 2018-11-30
If you've never run a webserver before, I suggest starting with Apache as it is the most widely supported option.  If you expect to build applications in PHP that use a database, a quick-and-easy solution is to run
```
sudo apt install lamp-server^
```
The "^" is required.

That will install Apache, PHP, the MySQL database server, and the software needed to link them all together.  WordPress, for instance, is built on this platform.

Personally I prefer PostgreSQL over MySQL for most database tasks, but some software like WordPress doesn't support Postgres.

---

