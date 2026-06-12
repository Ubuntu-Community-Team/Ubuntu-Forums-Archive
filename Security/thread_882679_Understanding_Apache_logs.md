---
title: "Understanding Apache logs"
date: 2008-08-07
forum: Security
---

### Post by data0213 on 2008-08-07
I am using Apache2 on Hardy (versions and modules included below). I recently started pouring through my apache logs recently and found some HTTP Get requests coming from some servers in China such as this:

[FONT="Courier New"]59.63.157.211 - - [03/Aug/2008:08:57:46 -0400] "GET http://www.wantsfly.com/prx1.php?hash=57A3B266F7FCBF5C4352F9921F404E9CE3CD61DCCEA4 HTTP/1.0" 404 419 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)"
[/FONT]
I don't have a deep understanding of what happens when you do a GET with an external URL. Can someone please tell me if someone is trying to probe for a vulnerability? How can I secure the server so that I can prevent any attacks through this route?

Thanks,
MT
--------------------------
Apache/2.2.8 (Ubuntu) 
DAV/2 
mod_python/3.3.1 
Python/2.5.2 
PHP/5.2.4-2ubuntu5.2 with Suhosin-Patch 
mod_ssl/2.2.8 
OpenSSL/0.9.8g 
mod_perl/2.0.3 
Perl/v5.8.8

---

### Post by cdenley on 2008-08-07
He's trying to use your server as an http proxy. However, the way apache seems to work by default, is it will simply read the URI (/prx1.php?hash=57A3B266F7FCBF5C4352F9921F404E9CE3CD 61DCCEA4) and process that request on your server. If you don't have your server configured as a proxy (which seems to be the case), nothing to worry about. The 404 shows that the file /prx1.php doesn't exist on your server.

---

