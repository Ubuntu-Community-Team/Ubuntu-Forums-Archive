---
title: "Mod_rewrite not working on Jaunty"
date: 2009-08-10
forum: Server Platforms
---

### Post by a1anmacp on 2009-08-10
Hi All,

Thanks for reading and I hope you can help. I have copied my site from a CentOS server (where all is fine) to a Jaunty one. All static pages are working but the rewrite rules do not. It all works fine on Centos on Apache 2.0.63. The Jaunty server is Apache 2.2.11, all installed via repositories.

My rules are:
Options +FollowSymlinks
Options -indexes
ErrorDocument 404 /index2.php

RewriteEngine on
RewriteCond %{HTTP_HOST} ^(([a-z0-9\-]+)\.)*birtest2.co.uk [NC]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^((.*)/(.*)/(.*)/)|((.*)/(.*)/)|((.*)/)$ /index.php?&action=$2$7&param=$3&%{QUERY_STRING} [L]
RewriteRule ^$ /index.php?imprint=%{HTTP_HOST}&%{QUERY_STRING} [L]

The idea is that a URL like [www.birtest2.co.uk/articles/details/85/](www.birtest2.co.uk/articles/details/85/) is transformed into 
[www.birtest2.co.uk/index.php?link=articles&action=details&param=85](www.birtest2.co.uk/index.php?link=articles&action=details&param=85)

What I'm getting in my rewrite log file is:
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] add path info postfix: /var/www/public_html/articles.php -> /var/www/public_html/articles.php/details/85/
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] strip per-dir prefix: /var/www/public_html/articles.php/details/85/ -> articles.php/details/85/
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] applying pattern '^((.*)/(.*)/(.*)/)|((.*)/(.*)/)|((.*)/)$' to uri 'articles.php/details/85/'
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (4) [perdir /var/www/public_html/] RewriteCond: input='www.birtest2.co.uk' pattern='^(([a-z0-9\-]+)\.)*birtest2.co.uk' [NC] => matched
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (4) [perdir /var/www/public_html/] RewriteCond: input='/var/www/public_html/articles.php' pattern='!-f' => not-matched
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] add path info postfix: /var/www/public_html/articles.php -> /var/www/public_html/articles.php/details/85/
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] strip per-dir prefix: /var/www/public_html/articles.php/details/85/ -> articles.php/details/85/
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (3) [perdir /var/www/public_html/] applying pattern '^$' to uri 'articles.php/details/85/'
192.168.1.233 - - [10/Aug/2009:16:46:35 +0100] [[www.birtest2.co.uk/sid#b9b3f018]](www.birtest2.co.uk/sid#b9b3f018])[rid#b9cdcf60/subreq] (1) [perdir /var/www/public_html/] pass through /var/www/public_html/articles.php

It looks like it's picking up articles.php for some reason, and I don't know why.

Any ideas? All greatefully received.
Kind regards,
Alan

---

