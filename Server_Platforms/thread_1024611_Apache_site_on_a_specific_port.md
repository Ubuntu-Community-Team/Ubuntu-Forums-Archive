---
title: "Apache site on a specific port"
date: 2008-12-29
forum: Server Platforms
---

### Post by ensis2k on 2008-12-29
I want one of my sites in /etc/apache2/sites-available to listen on a specific port. So browsing to [http://myserver/trac](http://myserver/trac) should not be possible. But [https://myserver/trac](https://myserver/trac) should work.

The site i want to add is my projects [Trac]("http://en.wikipedia.org/wiki/Trac") site. The port is HTTPS(443).

I already tried:
[LIST]
[*]<Location /trac:443>
[*]Encapsulate <Location> with <VirtualHost>
[*]Google
[/LIST]

---

### Post by ikonia on 2008-12-29
first thing is 443 - thats the SSL/https port, running a website on that is not a good call in my opinion, unless you want to use https, in which case setup https.

The other thing is the virtual host tag should be all you need.

eg: if your using name based virtual hosts all you need to do is

<VirtualHost *:123>
blah
</VirtualHost>

This will tell apache to listen on all IP's on your system, on port 123 for the site defined in ServerName

you can narrow it down to 

<VirtualHost 127.0.0.1:123>
blah
</VirtualHost>

which will only listen on 127.0.0.1(localhost) on port 123 for the site defined in ServerName

---

