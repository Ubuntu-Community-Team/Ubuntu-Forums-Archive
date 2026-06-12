---
title: "Squid refusing incoming connections to a web server?"
date: 2009-07-29
forum: Server Platforms
---

### Post by Stronghol on 2009-07-29
Alright so what I want to do is set up a website on my office server/firewall. Im running Shorewall and Squid on a transparent proxy. I have Apache2 listening on port 81 (thats what the tutorial said to do), but whenever I browse to mydomain.net I get: 

ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://mydomain.net]("http://mydomain.net/")

The following error was encountered:

    * Connection to mypublicip Failed 

The system returned:

    (110) Connection timed out

The remote host or network may be down. Please try the request again.

Your cache administrator is webmaster.
Generated Tue, 28 Jul 2009 19:04:07 GMT by my.domain.name(squid/2.7.STABLE3)

---

