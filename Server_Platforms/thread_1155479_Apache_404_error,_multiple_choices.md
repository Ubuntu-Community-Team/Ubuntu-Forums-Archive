---
title: "Apache 404 error, multiple choices?"
date: 2009-05-10
forum: Server Platforms
---

### Post by jamieh on 2009-05-10
While trying to find a site that streams Futurama for free, I came across "watchfuturamaonline.co.uk". Anyway, I clicked a link and ended up here:

[http://watchfuturamaonline.co.uk/s05e01.html](http://watchfuturamaonline.co.uk/s05e01.html)

It looks like their 404 page is set to show similar pages, and why that page is shown (mistyped, etc).

How can I get my Apache to do that?

Thanks

---

### Post by mbeach on 2009-05-14
you want to set the errordocument directive.
take a look at:
[http://httpd.apache.org/docs/2.0/mod/core.html#errordocument](http://httpd.apache.org/docs/2.0/mod/core.html#errordocument)
for a discussion.

likely in your 
/etc/apache2/apache2.conf
or if you are using virtual hosts, you'd put it in the respective virtual host file.
virtual host files at:
/etc/apache2/sites-available/

edit
sorry, misread your post a bit.  Basically, though I suspect you need a script of some sort which can suggest other similar pages. If I were doing this, I'd use the access logs to see where people are getting 404 errors, and where they go next or ultimately end up (not a trivial exercise), and start to build a database of intelligent suggestions for common mistakes.

---

### Post by mbeach on 2009-05-14
Apparently I'm completely off my rocker.

Look into 300 Multiple Choices

Specialized google search
[http://www.google.com/search?q=HTTP+300+%22Multiple+Choices%22](http://www.google.com/search?q=HTTP+300+%22Multiple+Choices%22)
shows lots of people doing this so it should be easy - I'll keep looking.

edit:
perhaps this is of some interest:
[http://httpd.apache.org/docs/2.2/mod/mod_negotiation.html](http://httpd.apache.org/docs/2.2/mod/mod_negotiation.html)

---

