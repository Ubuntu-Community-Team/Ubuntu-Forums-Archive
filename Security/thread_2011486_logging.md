---
title: "logging"
date: 2012-06-27
forum: Security
---

### Post by uncasual on 2012-06-27
Hi there, I have a question about apache2 logging, it looks like the get / post requests are cut  at 1024 chars, i would like to have the complete request for later research even when te request or post is larger then 1024.
is this possible?

---

### Post by SeijiSensei on 2012-06-27
Modify the log format, or create a custom log, using
[http://httpd.apache.org/docs/2.2/mod/mod_log_config.html](http://httpd.apache.org/docs/2.2/mod/mod_log_config.html)

See if logging the %q placeholder for the query string gets around the length problem.

---

