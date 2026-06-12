---
title: "Apache rewrites not using file-system path"
date: 2011-12-13
forum: Server Platforms
---

### Post by djeyewater on 2011-12-13
In apache2.conf I have
```
<LocationMatch "favicon.ico$">
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule .* /img-sys/favicon.ico
</LocationMatch>
```
And then I have several virtualhosts.

According to apache docs
> mod_rewrite tries to guess whether you have specified a file-system path or a URL-path by checking to see if the first segment of the path exists at the root of the file-system. For example, if you specify a Substitution string of /www/file.html, then this will be treated as a URL-path unless a directory named www exists at the root or your file-system, in which case it will be treated as a file-system path. 

/img-sys/favicon.ico does exist, yet any requests for a non-existent favicon are being rewritten to DOCUMENT_ROOT/img-sys/favicon.ico. This does not exist, so it gets stuck in a rewrite loop:

> 127.0.0.1 - - [13/Dec/2011:10:22:58 +0000] [[www.domain.can/sid#21b834a8]](www.domain.can/sid#21b834a8])[rid#21d6e028/initial] (2) [perdir favicon.ico$/] rewrite '/home/djeyewater/webapps/htdocs/domain.com/files/favicon.ico' -> '/img-sys/favicon.ico'
127.0.0.1 - - [13/Dec/2011:10:22:58 +0000] [[www.domain.can/sid#21b834a8]](www.domain.can/sid#21b834a8])[rid#21d6e028/initial] (1) [perdir favicon.ico$/] internal redirect with /img-sys/favicon.ico [INTERNAL REDIRECT]
127.0.0.1 - - [13/Dec/2011:10:22:58 +0000] [[www.domain.can/sid#21b834a8]](www.domain.can/sid#21b834a8])[rid#21d844f8/initial/redir#1] (2) [perdir favicon.ico$/] rewrite '/home/djeyewater/webapps/htdocs/domain.com/img-sys/favicon.ico' -> '/img-sys/favicon.ico'

So apache is rewriting relative to DOCUMENT_ROOT, when actually it should be using the file-system path. I did find an Ubuntu and Debian bug report for this problem, however both reports had people saying that actually it worked okay, and had been closed.

Version is Apache/2.2.14 (Ubuntu)

Any ideas? 

Thanks

Dave

---

