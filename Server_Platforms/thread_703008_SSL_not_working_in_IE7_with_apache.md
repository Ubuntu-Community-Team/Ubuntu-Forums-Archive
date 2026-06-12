---
title: "SSL not working in IE7 with apache"
date: 2008-02-20
forum: Server Platforms
---

### Post by kerinin on 2008-02-20
I just found out that my server isn't working for IE, specifically version 7.  The regular pages load just fine, but any time I try to access a SSL page via IE, i get a page not found error.

I've looked around and tried all the fixes I can find, I've checked to make sure that the keepalive problem is patched like this:

SetEnvIf User-Agent ".*MSIE.*"
nokeepalive ssl-unclean-shutdown
downgrade-1.0 force-response-1.0

I've changed the SSLCipherSuite values to everything I can find online, I've change dthe SSLProtocol to everything I've seen suggested, and every time IE says the page can't be found.  

Can anyone help me out here?  I'm running essentially an out of the box apache server with a couple virtual hosts.  I don't understand why something as basic as SSL is such a problem...

-Ryan

---

