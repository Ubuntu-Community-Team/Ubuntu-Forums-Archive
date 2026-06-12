---
title: "ssi's working, but index.shtml displays dir tree"
date: 2007-05-30
forum: Server Platforms
---

### Post by takayuki on 2007-05-30
hi,

i just installed apache2, mysql, php5 and everything works fine.  i use the server locally to build and test web sites.

i've set things up so apache parses files from my home/public_html dir.

i've "installed" server side includes via this howto: [https://wiki.ubuntu.com/ServerSideIncludes](https://wiki.ubuntu.com/ServerSideIncludes)
and includes *do* work fine.  when i load a simple test page includes are working.

**but**

if i load [http://localhost/home/public_html/](http://localhost/home/public_html/) , it does not load the index page, instead it just displays the list of files in the public_html directory.

if i load [http://localhost/home/public_html/index.shtml](http://localhost/home/public_html/index.shtml).  it loads the page fine.

what do i need to tweak to get /public_html/ to load the index page?

thanks for any input.

takayuki

---

### Post by MJN on 2007-05-30
The **DirectoryIndex** directive (see [http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.0/mod/mod_dir.html#directoryindex)) controls the list of files to look for, and serve, instead of a directory listing if no specific file is requested. As this is usually a server-wide setting you will likely find it in **/etc/apache2/apache2.conf** and you will need to add **index.shtml** to it.
 
Note that the order of the specified files is important if multiple matching files exist (descending order of priority).
 
Mathew

---

### Post by takayuki on 2007-05-30
MJN,

thank you for your help.  that did it.  i added

```
DirectoryIndex index.html index.shtml index.htm index.cgi
```

to the apache2.conf file and the index.shtml page loaded.

takayuki

---

