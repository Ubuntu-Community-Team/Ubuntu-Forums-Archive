---
title: "HELP: 58.49.171.46 [05/Feb/2008:09:31:35] &quot;CONNECT 211.150.96.25:25 HTTP/1.1&quot; 405"
date: 2008-02-05
forum: Server Platforms
---

### Post by cjtjamandra on 2008-02-05
I've seen this log on my apache server:

58.49.171.46 - - [05/Feb/2008:09:31:35 +0800] "CONNECT 211.150.96.25:25 HTTP/1.1" 405 298 "-" "-"


can someone explain me what is this... thx...

---

### Post by nemilar on 2008-02-05
Basically:

You got a connection from IP address 58.49.171.46 on Feb 5 at 9:31:35.

They asked the server to use method CONNECT with an IP address of  211.150.96.25:25  

[http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)  says that CONNECT is for use with proxy servers that are able to dynamically act as SSH tunnels.

The "405" is the response given by your server:
[http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)

The response is that the CONNECT method is not allowed (so this person was turned away).

---

### Post by cjtjamandra on 2008-02-05
Thx for the reply and clarification.

So meaning someone is trying to use my server to be a proxy server?

Do you have any idea what's the intention of this person?

---

