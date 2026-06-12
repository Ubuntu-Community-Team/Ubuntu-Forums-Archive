---
title: "Postfix Configuration"
date: 2005-02-04
forum: Server Platforms
---

### Post by CyberCam on 2005-02-04
I'm unable to connect to postfix on my ubuntu warty 4.10 server box via telnet [host ip] 25. I've just completed a fresh install and can only connect from the server itself.  

Here's the output when I try from a client node on my lan.

[username]@[client hostname]:~ $ telnet [server host ip] 25
Trying [server host ip]...
telnet: Unable to connect to remote host: Connection refused

Here's the output when I try from the server

[username]@[server hostname]:~ $ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 mail.kiasystems.com ESMTP Postfix (Ubuntu)

I'm trying break free from M$ Winblows & Argosoft mail server and I'm now trying to use Postfix & Courier-IMAP. I need to get a connection in order to continue the configuration process. Any help would be greatly apreciated?

---

### Post by JsPr on 2005-02-04
Hi,
Check this:
[http://www.webservertalk.com/message864299.html](http://www.webservertalk.com/message864299.html)

It talks about the main.cf parameter 
inet_interfaces = all. "all" seems to telll postfix to listen to all interfaces, not only localhost.

---

### Post by alastair on 2005-02-07
I think mail server configuration is still something one should be careful with - but mainly if the server is publically accessible. By default, Postfix appears to be configured to listen to the localhost (127.0.0.1) interface only on Ubuntu. This is a good thing. To configure it for access externally, it is expected that you do some research. Luckily, Postfix is a great mailserver, with good docs and a great mailing list.

A good place to start : [http://www.postfix.org](http://www.postfix.org)

---

