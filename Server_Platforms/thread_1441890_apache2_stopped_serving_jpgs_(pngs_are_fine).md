---
title: "apache2 stopped serving jpgs (pngs are fine)"
date: 2010-03-29
forum: Server Platforms
---

### Post by zim2dive on 2010-03-29
Got back from a trip and decided to upload my recent pics to my home-brew photo album (served on my webserver).. really a collection of simple CGI scripts.

Discovered that I cannot get _any_ jpgs to serve off my server.

The behavior I see is that the file name is displayed (as text in the browser) and FF acts like its trying to fetch the image.. but it never shows up.. and finally stops.

My access.log shows```
xx.xx.xx.xx - - [29/Mar/2010:09:53:07 -0400] "GET /sharpedges.jpg HTTP/1.1" 200 29172 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.2.2) Gecko/20100316 Firefox/3.6.2"
```

I get nothing in my error.log

/etc/mime.types has ```
image/jpeg                                      jpeg jpg jpe
```
I can see png images (and gif images) just fine.

I'm totally stumped on this.  Any ideas?

I've restarted apache2 already, but no change.

This _was_ working at one point, but that was weeks (and many ubuntu updates) ago that I last checked.

Solved: Didn't think it was exactly the same, but I guess it was... [http://ubuntuforums.org/showpost.php?p=8713914&postcount=3](http://ubuntuforums.org/showpost.php?p=8713914&postcount=3)

---

