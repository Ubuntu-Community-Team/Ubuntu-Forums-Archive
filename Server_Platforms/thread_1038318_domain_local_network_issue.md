---
title: "domain local network issue"
date: 2009-01-12
forum: Server Platforms
---

### Post by snares on 2009-01-12
Okay right now I have a server set-up. Domain name and all but when using a computer on the network I can't go to [http://www.domain.com/location](http://www.domain.com/location) it brings up error or in the case of [http://www.domain.com](http://www.domain.com) it brings me to the modem admin page. Not what I want. How do I get it so that [www.domain.com](www.domain.com) goes to the same place regardless of wether I'm using a computer on the network or through the web? Thanks.

cheers,
snares

---

### Post by stefangr1 on 2009-01-12
What you need is a reverse DNS server. Have you already had a look here?

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

---

### Post by snares on 2009-01-12
thanks for the help but I was a ijiot. The server is setup as a dns. that was my first thought. but as usually the case the problem lies between keyboard and chair. I had the hostname as server1.domain.com becuase I was following a tutorial by falko over at howtoforge and never changed it to [www.domain.com](www.domain.com) . All this time and it was the easy thing that fixed the problem. Thanks for the help though. And so fast I love this Ubuntu and the community as well. ;)

cheers
snares

---

