---
title: "Weird files on my ubuntu webserver"
date: 2008-03-20
forum: Security Discussions
---

### Post by Nocturne5577 on 2008-03-20
Lately I have found multiple strange txt and log files on my Ubuntu webserver.
All is secured as far as I know and still this crap comes on my webserver in certain directories which haven't been shielded with a blank index.html file.
I deleted all files and stored a blank index in every open directory.

Then I searched on google with my domain name as query and this was the result:
[http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Anl%3Aofficial&hs=ZnS&q=www.etclan.eu&btnG=Zoeken&meta=](http://www.google.nl/search?hl=nl&client=firefox-a&rls=org.mozilla%3Anl%3Aofficial&hs=ZnS&q=www.etclan.eu&btnG=Zoeken&meta=)

I certainly didn't post that, my question is: How can these files come onto my server? :S
Also there have been cullprits connecting to ports which they don't need access to, I now manually add those ports in iptables and also those connectees are dropped using iptables.
how can i set my server so that only ports 80 (web), 21(ftp), 6667(irc) and other relevant webserver ports should be opened?

Greetz 
:guitar:

---

### Post by eisublime on 2008-03-25
> **Nocturne5577 said:**
> 
Also there have been cullprits connecting to ports which they don't need access to, I now manually add those ports in iptables and also those connectees are dropped using iptables.
how can i set my server so that only ports 80 (web), 21(ftp), 6667(irc) and other relevant webserver ports should be opened?


have you tried putting a DROP or REJECT at the end of your iptables script?  I'm not exactly an expert on iptables, but I think that something like 
-A INPUT -p tcp -j REJECT 
at the end of your file would get you there. I'd try it on a test box first though to be sure it doesn't.

---

### Post by Nocturne5577 on 2008-03-27
I manually set them to DROP :)

---

