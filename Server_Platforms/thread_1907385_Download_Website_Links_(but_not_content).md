---
title: "Download Website Links (but not content)"
date: 2012-01-11
forum: Server Platforms
---

### Post by ThePol1 on 2012-01-11
[COLOR=black][FONT=Verdana]I am looking for a tool that can download links referred to by a website but not the website content. I simply need the list of urls dumped to a text file. It needs to be recursive within the domain I specify. Can anyone suggest a tool for doing this?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] I've looked at wget, but it doesn't seem to support this...[/FONT][/COLOR]

---

### Post by Habitual on 2012-01-11
```
lynx -dump http://www.domain.com | grep -A999 "^References$" | tail -n +3 | awk '{print $2 }' > /path/to/file.ext
```may have to install lynx. it is safe to do so.

---

### Post by ThePol1 on 2012-01-11
> **Habitual said:**
> ```
lynx -dump http://www.domain.com | grep -A999 "^References$" | tail -n +3 | awk '{print $2 }' > /path/to/file.ext
```may have to install lynx. it is safe to do so.
 
[COLOR=black][FONT=Verdana]Thank you for pointing out Lynx! I'm assuming I would just use the -crawl or -traverse flag to get it to crawl the site recursively... I'll look into these. Thanks again! :)[/FONT][/COLOR]

---

### Post by Habitual on 2012-01-11
Glad to be of help!

---

### Post by ThePol1 on 2012-01-11
Well... it appears that adding the -crawl and/or -traverse flags don't help. The above works great for one webpage, but not for an entire website. Any suggestions?

---

### Post by hackertarget on 2012-01-11
Here is a new python based tool I have been playing with.

[http://code.google.com/p/golismero/](http://code.google.com/p/golismero/)

It has been developed as a security tool for assessments and penetration testing but has some good functionality and produces clean results.

---

