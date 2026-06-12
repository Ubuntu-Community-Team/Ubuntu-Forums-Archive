---
title: "apache2 mod_rewrite help needed"
date: 2006-07-04
forum: Server Platforms
---

### Post by fommil on 2006-07-04
Hi everyone,

I'm afraid mod_rewrite is confusing me like crazy. I have it installed and it is working.

I have a server which has 2 domain names pointing to it. I want the server to realise which domain name it has been invoked from, and show a different root each time.

More specifically... say I have foo.com and bar.com, and I have two users, foo and bar. I want the server to show pages from /~foo/ when a client gets here from foo.com, and likewise for /~bar/ and bar.com. I don't want the client's location bar to be redirected.

Could somebody please give me some advice? Or at least an example doing something similar.

Apache mod_rewrite docs:-
[http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html)
[http://httpd.apache.org/docs/2.0/rewrite/rewrite_guide.html](http://httpd.apache.org/docs/2.0/rewrite/rewrite_guide.html)

---

### Post by fommil on 2006-07-04
Should probably have pointed out that the most relevant section in those docs is entitled "Virtual User Hosts". Which I can follow perfectly... it's all just a bunch of sed scripts, but it doesn't seem to be working! I've been able to confirm that the module is loaded through some other rewrite rules, so it can't be that.

RewriteEngine on
RewriteCond   %{HTTP_HOST}      ^foo\.com$
RewriteRule   ^(.+)                     %{HTTP_HOST}$1          [C]
RewriteRule   ^foo\.com(.*)          /~foo/$1

is a slightly rewritten and simplified version of the example in the docs. This should be spotting when someone has arrived through foo.com/X, and then give them back /~foo/X, without redirecting the client... but it's not doing *any* rewriting for me!

Any help appreciated.

---

