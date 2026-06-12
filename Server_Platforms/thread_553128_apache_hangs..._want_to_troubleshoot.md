---
title: "apache hangs... want to troubleshoot"
date: 2007-09-17
forum: Server Platforms
---

### Post by tocleora on 2007-09-17
We make hundreds of requests an hour to a web page on an internal ubuntu server that in turns makes an external call to a web site (via api, similar to cc processing) and returns values.  For some reason though probably once a day (and it's already happened twice today), apache will hang and I have to restart it.  sometimes I have to restart the server all together.  I looked in /var/log/apache2/error.log and other than references to the restart there's nothing in there.  How else can I trouble shoot what might be causing this?  is there something I can turn on that will provide additional information or somewhere else I can look?  thanks in advance...

---

