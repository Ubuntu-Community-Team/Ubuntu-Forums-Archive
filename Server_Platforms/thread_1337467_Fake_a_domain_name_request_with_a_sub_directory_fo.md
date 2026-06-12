---
title: "Fake a domain name request with a sub directory for name based vhost in Apache2"
date: 2009-11-25
forum: Server Platforms
---

### Post by emattias on 2009-11-25
I'm running Apache2.2 with name based virtual hosts

How can I make it so that this request:

[http://serverIp/**example.com**]("http://serverIp/example.com")

is the same as going to [http://**example.com**]("http://%3Cb%3Eexample.com%3C/b%3E") on a machine where example.com has been pointed to my servers ip in the hosts file?

I'd like to be able to send a link to a client without forcing them to modify their hosts file to point example.com to my servers ip. 

My idea was to fake a domain name request using a sub directory but porhaps this has a smarter soultion?

---

### Post by Lars Noodén on 2009-11-26
[mod_rewrite](/rewrite_intro.html) is where to start.  

[http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html](http://httpd.apache.org/docs/2.2/rewrite/rewrite_intro.html)

[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

[http://httpd.apache.org/docs/2.2/rewrite/rewrite_tech.html](http://httpd.apache.org/docs/2.2/rewrite/rewrite_tech.html)

[http://httpd.apache.org/docs/2.2/rewrite/rewrite_guide.html](http://httpd.apache.org/docs/2.2/rewrite/rewrite_guide.html)

---

