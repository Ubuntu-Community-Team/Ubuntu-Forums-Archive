---
title: "mod_jk apache tomcat questions"
date: 2007-10-03
forum: Server Platforms
---

### Post by wiz561 on 2007-10-03
Hi!

I'm trying to setup Subsonic, which requires using Apache Tomcat.  I have never used or installed Tomcat before, and have some questions about it.

I'm currently running Apache 2 and serving up some web pages.  I was messing around with Tomcat, and it looks like it runs it on a high port, and then you tell apache to proxy everything through to that higher port number.  Am I correct or am I missing something?  It sort of reminds me of how ruby on rails is setup with mongrel.  

And then, you would use mod_jk in order to make Apache Web Server interface with the Tomcat server?  Or, can I just use mod_jk and not install tomcat all together?

Thanks!
Mike

---

### Post by HermanAB on 2007-10-03
If things are simple but you need Java applets, then I'd suggest that you remove Apache and only use Tomcat.  Otherwise, to use both Apache and Tomcat, you need to install the jk2 connector as described in this old guide:
[http://www.aeronetworks.ca/tomcat-howto.html](http://www.aeronetworks.ca/tomcat-howto.html)

Cheers,

Herman

---

### Post by wiz561 on 2007-10-03
Thanks for the information.  I stumbled upon one of those pages and then another howto in the ubuntu forums that seemed to work well.  I was just wondering if I was on the right track or off in left field.

I guess I was just doubting myself because how everybody says how great Subsonic is....but I found that it was a PITA to get everything to work.  

Thanks again for the link and the info!

Mike

---

