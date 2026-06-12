---
title: "Apache2 webdav file truncation"
date: 2008-10-13
forum: Server Platforms
---

### Post by alanlit on 2008-10-13
I've just set up apache2 on ubuntu 8.04 with webdav enabled. All seemed fine _but_ GETs only seem to return the first 34-36K bytes of the file (!). 

The access log gives me status code of 200 and the correct file length so it thinks everything is ok and I get this behaviour both accessing via an XP Webdav client _and_ locally on the server via Firefox. Writes _to_ the server are fine for multi-magabyte uploads.

I slapped Ethereal on it and I see the first ~36K come over then the connection is broken (even though the access log says everything was sent).

Color me confused.

---

### Post by alanlit on 2008-10-13
Ah,

    part of the filesystem my webdav is making available is a locally mounted CIFs volume being shared by another ubuntu server. If I take a file from here and copy it to my local drive then webdav works fine -- but if it is left in the mounted CIFs volume I only get the first 35K. Hence the issue seems to be a CIFs/Apache/Webdav interaction of some form .... strange ...

---

### Post by alanlit on 2008-10-14
Well,

   it seems Apache and Sendfile may interact badly in certain (unspecified) circumstances and it would seem my config (Ubuntu 8.04-AMD64) is one of them ! Adding 

<Directory "/path-to-mounted-files">   
    EnableSendfile Off  
</Directory>  

Fixes everything.

---

