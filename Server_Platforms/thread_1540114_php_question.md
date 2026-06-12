---
title: "php question"
date: 2010-07-27
forum: Server Platforms
---

### Post by terazen on 2010-07-27
Just testing something and wanted to ask here since all of my web searches are pulling up the wrong things.  Can php get hostnames of client pc's?  I know you can get their ip address, but not sure about hostname since php runs on the server side.  Is javascript better for this kind of thing?

---

### Post by lukeiamyourfather on 2010-07-27
PHP won't be able to do that unless its a local network and the DNS is accessible. Otherwise you'll need something client side to provide the hostname.

---

### Post by cdenley on 2010-07-27
You can get the reverse DNS lookup for the client's IP. This doesn't usually resolve to what you might think, though. For example, ubuntu.com resolves to 91.189.94.156. However that IP resolves to the hostname vostok.canonical.com with reverse DNS. Most ISP's usually have their user IP's resolve to a random-looking string of characters which include the ISP's name and the IP itself.

[http://www.php.net/manual/en/function.gethostbyaddr.php](http://www.php.net/manual/en/function.gethostbyaddr.php)

That is the only hostname information you can get about a client. Not all systems have a "hostname". If you mean like the "computer name" of a windows system, the browser shouldn't disclose that information.

---

