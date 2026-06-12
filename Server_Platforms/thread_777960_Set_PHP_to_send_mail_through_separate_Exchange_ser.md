---
title: "Set PHP to send mail through separate Exchange server"
date: 2008-05-01
forum: Server Platforms
---

### Post by ringobob on 2008-05-01
I've got Ubuntu 7.10 installed as an internal web server with Apache 2 and PHP 5, and I've got a separate windows server that handles email through exchange.  I know on Windows, I can just set the appropriate IP address in the PHP ini and it works.  Is there some similar setting I can use here, or do I have to use something like postfix to interact with the Exchange server?

---

### Post by ringobob on 2008-05-02
I searched around some more and settled on using postfix, setting it to use a smarthost to handle all email needs and forwarded everything to the exchange server.

Everything checks out.

---

