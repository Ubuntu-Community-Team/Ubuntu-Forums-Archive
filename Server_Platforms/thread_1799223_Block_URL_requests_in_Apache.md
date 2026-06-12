---
title: "Block URL requests in Apache"
date: 2011-07-07
forum: Server Platforms
---

### Post by GWBouge on 2011-07-07
I've got a little web server set up with Ubuntu 10.04 64-bit, standard LAMP setup, hosting nothing important or anything that I'm scared to lose, but mainly for the learning experience.  Looking at the logs this morning, I'm getting requests through my IP (I guess?) to a URL:

```
fioexst.simplehosts.net - - [07/Jul/2011:06:58:50 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" 200 5799 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
server.bogtube.com - - [07/Jul/2011:06:59:23 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" 200 5799 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
64.120.177.26 - - [07/Jul/2011:07:01:40 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" 200 5799 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
174.133.7.18 - - [07/Jul/2011:07:02:09 -0500] "POST http://yourinfo.any-request-allowed.com/ HTTP/1.1" 200 5799 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)"
31.44.184.245 - - [07/Jul/2011:07:12:48 -0500] "POST http://myinfo.any-request-allowed.com/?strGet=get4851 HTTP/1.1" 200 5780 "-" "-"
```

I'm effectively stopping (and logging) these request with iptables by IP address as they show up, but that's damned aggravating.  But, I can't seem to figure out how to make apache ignore/drop/forbid requests to what they're trying to do.  I've looked up the mod_rewrite stuff to do this through .htaccess and httpd.conf and I just can't seem to get it to work like I want it to, but I think that's more my ignorance of all the regex used in the tutorials and help I'm finding.

Any way someone can come up with a RewriteCond I can use to block this request?  Or a better method I'm overlooking?

---

