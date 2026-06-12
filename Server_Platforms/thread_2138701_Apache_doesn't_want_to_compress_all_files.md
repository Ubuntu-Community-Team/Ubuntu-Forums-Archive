---
title: "Apache doesn't want to compress all files"
date: 2013-04-25
forum: Server Platforms
---

### Post by mastablasta on 2013-04-25
i am hosting a site and would liek to use deflate or gzip to compress the files for tranfers. 

currently i have it set to:
```
SetOutputFilter DEFLATE
```

but 've also tried:
```
# compress text, html, javascript, css, xml:
AddOutputFilterByType DEFLATE text/plain
AddOutputFilterByType DEFLATE text/html
AddOutputFilterByType DEFLATE text/xml
AddOutputFilterByType DEFLATE text/css
AddOutputFilterByType DEFLATE application/xml
AddOutputFilterByType DEFLATE application/xhtml+xml
AddOutputFilterByType DEFLATE application/rss+xml
AddOutputFilterByType DEFLATE application/javascript
AddOutputFilterByType DEFLATE application/x-javascript

# Gzip all text-based files
<FilesMatch ".(php|html|css|js)\?.*$">
SetOutputFilter DEFLATE
</FilesMatch>

```

however, it only compresses text and html files. anyone knows why this is happening and how to force it to compress everything?

---

### Post by SeijiSensei on 2013-04-25
You shouldn't try to compress graphics; they are already compressed.  Try to compress them again just adds overhead and provides little improvement in size.  Other than text, there is little that is compressible on most web sites.  What do you think needs further compression?

---

### Post by mastablasta on 2013-04-26
i know about the graphics. didn't want to compress them. i just left the command there in frustration.... i will change it back to text and others only

i wanted to compress java scripts and php which is not getting compressed and that is the issue. 

yslow plugin as well headers show only html files and text are getting compressed.

---

### Post by SeijiSensei on 2013-04-26
There is no compression of PHP scripts because they are not sent to the browser, just the rendered pages which should be compressed already.  

You do realize we're talking here about something that will change download speeds by a few milliseconds for most anyone on a connection better than a dialup line, right?

---

### Post by mastablasta on 2013-04-26
that may be but half of customers form webpage come from Indonesia. Indoensia has poor main line with internet. As a "bonus" many people there connect with mobile internet and their infrastructure is still being upgraded. though it is supposed to be 3G, often connections are really slow sometimes. especially during working hours. you might see them slower or something similar to than dialup. imagine those speeds and modern websties...

---

### Post by Doug S on 2013-04-26
Is it possible that the issue here is that some clients are not accepting compressed data? The "GET" packet from the client will include an "Accept-Encoding" portion that needs to include "gzip" and/or "deflate" or whatever, otherwise (I think) the server will send the page uncompressed. I see varying reply sizes for the same thing in my apache logs all the time. Example from wireshark attached.

Edit: Adding an uncompressed "GET" example, for a "robots.txt" fetch. The returned data is around 3400 bytes when compression is allowed and around 10820 bytes when not allowed.

---

### Post by mastablasta on 2013-04-29
no, that doesn't seem to be the case. client has compression enabled. hmm i will try to investigate this further.

---

