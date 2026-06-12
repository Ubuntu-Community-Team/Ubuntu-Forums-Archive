---
title: "Strange Apache log entries"
date: 2009-11-23
forum: Server Platforms
---

### Post by dwasifar on 2009-11-23
I have a Jaunty LAMP server with five domains hosted using virtual hosts.  Some of them are inactive; the web pages are just "nothing here right now" placeholders.  Each domain has its own activity log.

The other day I was in there doing some maintenance (dropping one domain, adding another, and adding SSL to a third) when I noticed the logs for one of the inactive domains were larger than I expected.  I had not been watching the logs on that domain because there's nothing hosted there.  But the logs were full of entries like this, over and over and over:

```
::1 - - [15/Nov/2009:07:41:25 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"
::1 - - [15/Nov/2009:07:41:25 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"
::1 - - [15/Nov/2009:07:41:25 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"
::1 - - [15/Nov/2009:07:43:23 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"
::1 - - [15/Nov/2009:07:51:38 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"
::1 - - [15/Nov/2009:07:51:59 -0600] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (internal dummy connection)"

```

I have no idea what caused this.  It stopped after I did my maintenance changes and restarted Apache.  But it had been doing it for about ten weeks before I noticed it (yeah, Mr. Alertness, that's me); there were thousands of them in each log; it was only doing it for that one domain, not any of the others; and, weirdest of all, it appears to have started coincident with when the log rolled over.  The .10.gz log has them from beginning to end, but the .11.gz log has none at all.

What was Apache doing?

---

### Post by Bag-O-Stuff on 2009-11-23
These are normal log entries.  This wiki page from apache explains why they happen and how to stop them from being logged.

[http://wiki.apache.org/httpd/InternalDummyConnection](http://wiki.apache.org/httpd/InternalDummyConnection)

---

