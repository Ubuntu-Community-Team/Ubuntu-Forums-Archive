---
title: "apache2 CONNECT responds like &quot;GET /&quot;?"
date: 2006-10-30
forum: Server Platforms
---

### Post by graybark on 2006-10-30
I have a simple apache2 server (2.0.55-4) running on dapper.  This morning in the access log I noticed this entry:

61.216.243.137 - - [30/Oct/2006:03:49:14 -0500] "CONNECT mx3.mail2000.com.tw:25 HTTP/1.0" 200 1383 "-" "-"

This server is not set up to be any kind of proxy, so I was concerned about the 200 OK response to this.  Trying it out myself via telnet I can see that the server is responding as if it had received a "GET /".  Is that normal/expected?  The response it's giving seems harmless enough but I would have expected some kind of failure, not morphing of an unsupported command into "GET /"?

---

### Post by MJN on 2006-10-30
Can you confirm you don't have any **Proxy* (e.g. ProxyRequests On)** directives set?
 
Do you have the PHP module loaded? I seem to recall it can be responsible for the 200 responses (as opposed to 405 etc).
 
Mathew

---

### Post by graybark on 2006-10-30
Thanks for the reply.  I can't find any Proxy* directives in any enabled config files.  (ProxyRequests is Off in proxy.conf under mods-available, but that is not linked into mods-enabled.)  No PHP, but I do have mod_python enabled.  Beyond that I have only cgid and userdir .conf and .load files in mods-enabled.  Not sure what they do and I didn't do anything (knowingly) to turn them on so they must be defaults?

---

