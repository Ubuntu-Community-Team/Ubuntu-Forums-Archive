---
title: "Squid 3.0 Header_access problem"
date: 2007-09-28
forum: Server Platforms
---

### Post by JSPT on 2007-09-28
Hello, my new server is up and running with Squid 3.0 (I've used 2.6 till now) and I noticed that all the header_access are now in reply_header_access and request_header_access. I go and set them as both anonymous as described in the conf file. I load the proxy in my office using Internet Explorer and go to spotip.com and see that it's correct. I then visit many sites all working fine, except for hotmail.com which won't let me log in, and sites like ticketmaster.com which gives me  (111) Connection refused. I checked out my old squid version 2.6 conf file and can't find anything different except for these header rules. Unless I'm missing something. Thanks in advance,
Pete

---

