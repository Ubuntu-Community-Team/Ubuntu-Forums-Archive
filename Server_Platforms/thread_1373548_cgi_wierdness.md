---
title: "cgi wierdness"
date: 2010-01-05
forum: Server Platforms
---

### Post by litspliff on 2010-01-05
helo, i am working on a cgi project with a 9.04 ubuntu server.


i had the problem of my cgi scripts appearing in plain text when accessing them via port 80, so i did a search on the forums, and found this....
> 
 Re: I need some help getting perl pages to load!! SOLVED
Well, I got it fixed. I had to add these lines to apache.conf:

AddHandler cgi-script .cgi .pl
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>i used this in my apache2.conf
```

AddHandler cgi-script .cgi
<Files ~ "\.cgi$">
Options +ExecCGI
</Files>
```when i tr to hit a *.cgi script under /cgi-bin on port 80, now i get a 404.
when i hit a *.cgi script under any other directory on port 80, i get a 500.

i've tried a bash script and a perl script, with same results.

need some help....thanks for reading.

---

