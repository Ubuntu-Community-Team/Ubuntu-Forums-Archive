---
title: "Upgrading to TLS Within HTTP"
date: 2011-12-23
forum: Security
---

### Post by salmontres on 2011-12-23
Hi everyone, 

I'm trying to upgrade an HTTP connection to a secure HTTPS connection through TLS over the same TCP connection. 

I'm not trying to use the Server Name Indication method, nor am I using the SubjectAltName route outlined in Wikipedia. (Neither method can be employed well if multiple hosts are sharing the same connection.) 

[http://en.wikipedia.org/wiki/Virtual_hosting](http://en.wikipedia.org/wiki/Virtual_hosting)
(The main issue is outlined in the Name-Based section of Virtual Hosting.) 

I'm actually trying to follow up with the strategies in this RFC: 

[http://www.ietf.org/rfc/rfc2817.txt](http://www.ietf.org/rfc/rfc2817.txt)

However, I can't seem to find more information on it? Has anyone had a similar problem? How did you handle it? 

To sum up, I'm trying to initialize TLS on an HTTP connection to upgrade to a secure connection. The RFC mentioned outlines a strategy, but I haven't found any further information on this, nor have I found any instances where it's been carried out. 

Any info/advice would be greatly appreciated!

---

### Post by lensman3 on 2011-12-24
I don't think a generic port 80 html connection can be upgraded to TLS.  That is what https (443) is for.  There is an addon for Firefox that forces all http (80) connections to go to https (443).  Https is encrypted.  This addon make all port 80 connections secured by forcing the connection to https. 

I know that Google has https at its lowest level. Gmail uses it automatically.  I'm not sure all www servers are 443 enabled but it sounds like the one you want to go to is enabled.

Hope this helps

---

### Post by salmontres on 2011-12-24
Thanks Lensman,

You're absolutely right. I did a little more exploration here, and when this note was written, the intention wasn't meant for general purpose browsing. If anyone else had an interest in this, either contact me or look into Server Name Indication, which is quickly becoming the standard for this type of work.

I'll mark the thread as solved, thanks for the help!

---

