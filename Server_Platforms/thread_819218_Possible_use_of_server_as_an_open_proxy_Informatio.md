---
title: "Possible use of server as an open proxy? Information from access log."
date: 2008-06-05
forum: Server Platforms
---

### Post by mm3gss on 2008-06-05
I checked my access log this moring on my hardy server and was greeted with a few of the following enteries:

207.45.69.69 - - [05/Jun/2008:08:45:44 +0100] "POST [http://207.45.69.69:11111/](http://207.45.69.69:11111/) HTTP/1.0" 200 274 "-" "-"
207.45.69.69 - - [05/Jun/2008:08:45:44 +0100] "CONNECT 207.45.69.69:11111 HTTP/1.0" 200 274 "-" "-"

There are a number of the above entries with different IP Addresses being added in. If im right does this mean someone is using my server to access another address, in the above case 207.45.69.69:11111? 200 means the request was ok I think.

207.45.69.69:11111 takes you to a page that says Open Proxy Check.

Any help / advice on what this is and how to stop it would be appreciated.

Cheers

---

### Post by prshah on 2008-06-05
> **mm3gss said:**
> 
207.45.69.69:11111 takes you to a page that says Open Proxy Check.

Any help / advice on what this is and how to stop it would be appreciated.
Cheers

The [wiki]("http://en.wikipedia.org/wiki/Open_proxy") contains a lot of information including this (chilling) note:> It is possible for a computer to be running an open proxy server without knowledge of the computer's owner. This can be the result of misconfiguration of proxy software running on the computer, or of infection with malware (viruses, trojans or worms) designed for this purpose.

All considered, I'd say you have a mis configured proxy. Are you using your server for internet sharing or intentionally as a proxy?

Following from the wiki, this may be useful too:
[http://www.corpit.ru/mjt/proxycheck.html](http://www.corpit.ru/mjt/proxycheck.html)

---

### Post by mm3gss on 2008-06-05
Server is just running as a standard web server (PHP and MySQL) with an SSH server installed. 

Also running as a TOR exit node. Not sure if that has something to do with what im seeing in the logs.

Until i can get to the bottom of it the server is off :) - thats the best method of protection!

---

