---
title: "Apt-mirror/apache2 question"
date: 2015-12-25
forum: Server Platforms
---

### Post by Spency on 2015-12-25
I run apt-mirror on an 14.04 server. 

I would like to be able to start using my apt-mirror even if it isn't finished downloading. Found quickly this [page]("http://ebb.org/bkuhn/blog/2008/01/24/apt-mirror-2.html") which describes a solution of redirecting requests not found on the local mirror to online sources, but I'm not totally sure how to apply it and whether it would still work given the age of the article.

I've adapted the apache configuration described for my system.

```
#RewriteEngine on#RewriteLogLevel 0
#RewriteCond %{REQUEST_FILENAME} !^/cgi/
#RewriteCond /opt/apt-mirror/mirror/archive.ubuntu.com%{REQUEST_FILENAME} !-F
#RewriteCond /opt/apt-mirror/mirror/archive.ubuntu.com%{REQUEST_FILENAME} !-d
#RewriteCond %{REQUEST_URI} !(Packages|Sources)\.bz2$
#RewriteCond %{REQUEST_URI} !/index\.[^/]*$ [NC]
#RewriteRule ^(http://%{HTTP_HOST})?/(.*) http://archive.ubuntu.com/ubuntu//$2 [P]
```

It's commented out at the end of my apache2.conf file currently, but is that where it belongs?
Is the /cgi directory he's indicating in the code now /usr/lib/cgi-bin?

The article also mentions adding

```
[COLOR=#000000]ErrorDocument 403 /cgi/redirect-forbidden.cgi[/COLOR]
```

to apache config - so this would also go at the end of the file? but obviously directing to /usr/bin/redirect-forbidden.cgi with the following code:
```
[COLOR=#000000]#!/usr/bin/perl[/COLOR]            
            use strict;
            use CGI qw(:standard);
            
            my $val = $ENV{REDIRECT_SCRIPT_URI};
            
            $val =~ s%^http://(\S+).sflc.info(/.*)$%$2%;
            if ($1 eq "ubuntu-security") {
               $val = "http://91.189.88.37$val";
            } else {
               $val = "http://91.189.88.45$val";
            }
             [COLOR=#000000]            print redirect($val);[/COLOR]
```

Besides what I've mentioned, do I need to adapt this any further?

---

### Post by matt_symes on 2015-12-26
Thread moved to **Server Platforms**

You may get better help for your query here.

---

