---
title: "mod_rewrite won't load"
date: 2011-04-17
forum: Server Platforms
---

### Post by greybeard95a on 2011-04-17
Hello all,

Trying to track down reasons why mod_rewrite won't load, I found this [site]("http://tymonn.wordpress.com/2009/07/31/how-to-enable-mod_rewrite-in-apache2-debianubuntu/"); hopefully, this will reduce the idiocy of this question.

Based on it and other sources:

```
graton# locate mod_rewrite.so
/root/share/openh323/lib/apache2/modules/mod_rewrite.so
/root/share/pwlib/lib/apache2/modules/mod_rewrite.so
/usr/lib/apache2/modules/mod_rewrite.so
graton# ls -al /usr/lib/apache2/modules/mod_rewrite.so
-rw-r--r-- 1 root root 58664 2010-11-18 13:20 /usr/lib/apache2/modules/mod_rewrite.so
```

And running phpinfo() through grep yields:

```
graton# php /root/phpinfo.php | grep -i rewrite
url_rewriter.tags => a=href,area=href,frame=src,input=src,form=fakeentry => a=href,area=href,frame=src,input=src,form=fakeentry
```

I don't know if that result is even relevant.

And,

```
graton# apachectl -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c
```

Just to be sure:

```
graton# apache2 -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c
```

Oh yes, and:

```
graton# cat /etc/apache2/mods-enabled/rewrite.load 
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
```

As near as I can tell it doesn't load.

I'm desperately trying to solve a problem where I need to force applications like WordPress and Drupal to use http even when they are insisting on using https (and doing so even after revising the configurations appropriately).  I have created an environment where this is okay: Apache2 runs on my old laptop which is connected to a Linode through an OpenVPN and nginx will serve as the "reverse proxy" (as I guess it is supposed to be called) and handle the SSL stuff that I could never get right under Apache but seems to work flawlessly under nginx.  But these applications run under different domains.  The long and gory story of how this situation arises is [here]("http://drupal.org/node/1129676").

I need rewrite for multiple reasons, but I think I need it for this rule, which currently blows up as shown:

```
graton# apachectl configtest
[Sat Apr 16 21:56:31 2011] [warn] module php5_module is already loaded, skipping
Syntax error on line 8 of /etc/apache2/sites-available/graton.parts-unknown.org-ssl:
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
```

The rule is:

```
RequestHeader edit Destination ^https http early
```

I hope I have supplied enough information to meaningfully answer what, as near as I can tell, are the obvious questions.  But the final one is that this is Maverick and:

```
graton# dpkg -l | grep apache2
ii  apache2                                     2.2.16-1ubuntu3.1                                   Apache HTTP Server metapackage
ii  apache2-mpm-prefork                         2.2.16-1ubuntu3.1                                   Apache HTTP Server - traditional non-threaded model
ii  apache2-utils                               2.2.16-1ubuntu3.1                                   utility programs for webservers
ii  apache2.2-bin                               2.2.16-1ubuntu3.1                                   Apache HTTP Server common binary files
ii  apache2.2-common                            2.2.16-1ubuntu3.1                                   Apache HTTP Server common files
ii  libapache2-mod-php5                         5.3.3-1ubuntu9.3                                    server-side, HTML-embedded scripting language (Apache 2 module)
```

Help, please?!???

Thanks a million!

---

### Post by soulresin on 2011-04-17
> **greybeard95a said:**
> Hello all,




```
graton# apachectl configtest
[Sat Apr 16 21:56:31 2011] [warn] module php5_module is already loaded, skipping
Syntax error on line 8 of /etc/apache2/sites-available/graton.parts-unknown.org-ssl:
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
```

The rule is:

```
RequestHeader edit Destination ^https http early
```

I hope I have supplied enough information to meaningfully answer what, as near as I can tell, are the obvious questions.  But the final one is that this is Maverick and:

```
graton# dpkg -l | grep apache2
ii  apache2                                     2.2.16-1ubuntu3.1                                   Apache HTTP Server metapackage
ii  apache2-mpm-prefork                         2.2.16-1ubuntu3.1                                   Apache HTTP Server - traditional non-threaded model
ii  apache2-utils                               2.2.16-1ubuntu3.1                                   utility programs for webservers
ii  apache2.2-bin                               2.2.16-1ubuntu3.1                                   Apache HTTP Server common binary files
ii  apache2.2-common                            2.2.16-1ubuntu3.1                                   Apache HTTP Server common files
ii  libapache2-mod-php5                         5.3.3-1ubuntu9.3                                    server-side, HTML-embedded scripting language (Apache 2 module)
```

Help, please?!???

Thanks a million!

RequestHeader comes from mod_headers, not mod_rewrite.  Make sure mod_headers is enabled.

---

### Post by greybeard95a on 2011-04-17
Got it.  Unfortunately, it didn't solve the problem.

But maybe starting and stopping Apache enough times makes a difference.  The crucial application that demands mod_rewrite ([YOURLS]("http://yourls.org/")) is suddenly working (just not at the front page).

I think perhaps I've been chasing down too many rat holes trying to get this server back up (a longer version of that story is [here]("http://drupal.org/node/1129676")).

Thanks!

---

