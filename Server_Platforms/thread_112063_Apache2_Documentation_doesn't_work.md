---
title: "Apache2 Documentation doesn't work"
date: 2006-01-03
forum: Server Platforms
---

### Post by Chrissss on 2006-01-03
Hi There!

For a documentiation I installed, the Apache2 Doc "apache2-doc" via apt on my breezy box. The first thing i noticed is that it is not linked into /var/www, so I created the link:

# sudo ln -s /usr/share/doc/apache2-doc/manual /var/www/

After that I opened the manual inside my browser (doesn't matter which one: ff1.5, ff1.0.7, ephipany, all do the same)

[http://localhost/manual/](http://localhost/manual/)

But all I get is this

> URI: index.html.de Content-Language: de Content-type: text/html; charset=ISO-8859-1 URI: index.html.en Content-Language: en Content-type: text/html; charset=ISO-8859-1 URI: index.html.es Content-Language: es Content-type: text/html; charset=ISO-8859-1 URI: index.html.fr Content-Language: fr Content-type: text/html; charset=ISO-8859-1 URI: index.html.ja.euc-jp Content-Language: ja Content-type: text/html; charset=EUC-JP URI: index.html.ko.euc-kr Content-Language: ko Content-type: text/html; charset=EUC-KR URI: index.html.ru.koi8-r Content-Language: ru Content-type: text/html; charset=KOI8-R

When i open [http://localhost/manual/index.html.en](http://localhost/manual/index.html.en) it works, but after each link the same story again. Somehow the language detection doesn't work. Did I miss a apache2 module that should be installed?

Thanks
 Christoph

---

### Post by mcook2 on 2007-05-29
To recap, with Ubuntu-Feisty and apache2-doc, at this URL: [http://127.0.0.1/doc/apache2-doc/manual/](http://127.0.0.1/doc/apache2-doc/manual/) you get this in your browser:

"URI: index.html.de Content-Language: de Content-type: text/html; charset=ISO-8859-1 URI: index.html.en Content-Language: en Content-type: text/html; charset=ISO-8859-1 URI: index.html.es Content-Language: es Content-type: text/html; charset=ISO-8859-1 URI: index.html.fr Content-Language: fr Content-type: text/html; charset=ISO-8859-1 URI: index.html.ja.euc-jp Content-Language: ja Content-type: text/html; charset=EUC-JP URI: index.html.ko.euc-kr Content-Language: ko Content-type: text/html; charset=EUC-KR URI: index.html.pt-br Content-Language: pt-br Content-type: text/html; charset=ISO-8859-1"

This apparent garbage is the contents of the default index.html file, which is actually a "type map" used by Apache Content Negotiation to handle multiple languages.     

Even if you add index.html.en to the end of the above URL (or if you delete index.html), the main page will load OK, but then all subordinate links give similar results.  

The bug report at [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/97392](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/97392) 
tells you what you can do to resolve the problem.  

Rather than go and remove all the files ending ".html", I chose to rename all the file names ending ".html" to ".html.var". 

This renaming is easiest to do if you open a Terminal, navigate to /usr/share/doc/apache2-doc/manual and there run the following command with appropriate permissions:
 
```
find . -name "*.html" -type f | xargs rename 's/\.html$/\.html.var/' 
```

---

### Post by splinux on 2007-11-03
hello,
i was working out the same problem and i found a template to use
under :
*/usr/share/doc/apache2.2-common/examples/apache2/extra/*

there i found lots of configuration examples.

the one we are interested in is
* httpd-manual.conf *

then i copied it on my apache conf.d/ directory:
```
sudo cp /usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-manual.conf /etc/apache2/conf.d/httpd-manual.conf

sudo vim /etc/apache2/conf.d/httpd-manual.conf

```

and i changed the following Directives:
> 
...
AliasMatch ^/manual(?:/(?:de|en|es|fr|ja|ko|pt-br|ru))?(/.*)?$ [COLOR="Red"]"/usr/share/apache2/default-site/htdocs/manual$1"[/COLOR]

<Directory [COLOR="Red"]"/usr/share/doc/apache2-doc/manual"[/COLOR]>
...


with my documentation location path(that is, the default location i found after apt-getting the *apache2-doc* package) :
> 
...
AliasMatch ^/manual(?:/(?:de|en|es|fr|ja|ko|pt-br|ru))?(/.*)?$ [COLOR="Red"]"/usr/share/doc/apache2-doc/manual$1"[/COLOR]

<Directory [COLOR="Red"]"/usr/share/doc/apache2-doc/manual"[/COLOR]>
...


then, after hitting in my browser
```
http://locahost/manual/
```
i get the 2.2 documentation

anyway have a look the the example directory if you have it...
apache 2 it's a bit messy! and i know i bypassed the 
/default-site/htdocs/ URI that should be used , that's because
i have my own dirty VirtualHost configuration :guitar:

Use it as an example. hope it work to all you too.
cheers.
Splinux

---

