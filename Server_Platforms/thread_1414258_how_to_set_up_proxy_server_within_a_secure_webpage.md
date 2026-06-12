---
title: "how to set up proxy server within a secure webpage?"
date: 2010-02-23
forum: Server Platforms
---

### Post by gobbledigook on 2010-02-23
Hi!

i'm sure this is fairly simple, yet i have fund nothing useful by searching :(

I would like to set up a proxy server at home which i can use to access sites from work. I was thinking a web-page i log into and then a sort of use like a browser? like [_**this**_]("http://anonymouse.org/anonwww.html") for example, but where i can have a secure login :)

any ideas how i can accomplish this?

---

### Post by elliotbeken on 2010-02-23
yes i am also intersted in this i want to do the same

i have a squid proxy that works well but i want to do it this way aswell

---

### Post by gobbledigook on 2010-02-24
*bump*

---

### Post by gobbledigook on 2010-02-25
i have done this now using [poxy]("http://sourceforge.net/projects/poxy/") and [phpSecurePages]("http://www.phpsecurepages.com/")

---

### Post by noway2 on 2010-02-25
use SSH as a socks proxy.  You can make it very secure using password-less login.  All of your traffic will be encrypted.  You can use remote DNS option on firefox and even the DNS lookups (where you go) will be done remotely.

This is really easy to do.  Set up an SSH server at home. Then from the client end, pull up a shell, cygwin, or putty, and then connect with "SSH -CND 9999 user@yourdomain".  Then in firefox configure a socks proxy of localhost on port 9999.  All traffic will be routed through the SSH to your server.

---

