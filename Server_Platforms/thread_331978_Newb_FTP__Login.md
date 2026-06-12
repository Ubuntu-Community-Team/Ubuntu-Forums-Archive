---
title: "Newb FTP ? Login"
date: 2007-01-05
forum: Server Platforms
---

### Post by kramerkeller on 2007-01-05
So I succesfully installed vsFTPd.  It seems to be a good program.  I can login by typing into my browser username@ipaddress and the it prompts for a password.  I log in and everything is fine.

However, I was wondering how to login by jus going to [ftp://ipaddress](ftp://ipaddress) and then allowing the user to input there username and password there instead of having to put the username in the ftp:// bar at the top.

---

### Post by kidders on 2007-01-05
Hi there,

That's a little like asking "How do I get to [www.google.com](www.google.com) by just typing 'google' into the address bar?" As you probably know, it will only work if (a) your browser supports lazy addresses in the first place, and (b) a DNS lookup for "google" fails first. Similarly, what you're describing is browser-dependent, and would presumaby rely on an initial failed anonymous login, I suppose.

---

### Post by rth on 2007-01-05
To clarify, URLs basically follow this syntax:
```
protocol://username:password@server:port
```
Your browser is made to surf with HTTP as the protocol, rather than FTP, so any server name/address that is in there will go to HTTP by default. If you put in "ftp://server" and have anonymous disabled, then it *should* prompt for a username and password. If anonymous is enabled, it will do that first because no username was specified.

---

