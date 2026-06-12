---
title: "SSI server side includes on Ubuntu? fixed"
date: 2005-12-04
forum: Server Platforms
---

### Post by bwiese on 2005-12-04
I've been running debian-based servers for a few years now and never had a problem running Server Side Includes (SSI) on Apache 1.3 until now on Ubuntu Hoary... anyone have a suggestion?

I have a test/index.shtml page on my server with SSI directives on the page but they are not being executed. They are as follows:

SSI Tests: lastmod: <!--#flastmod file="index.shtml" --> fsize: <!--#fsize virtual="index.shtml" -->  
(note: no space before "#")

my /usr/lib/apache/1.3 has: 090mod_include.info  mod_include.so

my httpd.conf:
    # To use server-parsed HTML files mod_include has to be enabled.
    #
    <IfModule mod_include.c>
     AddType text/html .shtml
     AddHandler server-parsed .shtml
    </IfModule>

my modules.conf (line added myself):
LoadModule include_module /usr/lib/apache/1.3/mod_include.so

but upon apache(ctl) start, I get:
Syntax error on line 25 of /etc/apache/modules.conf:
Can't locate API module structure `include_module' in file /usr/lib/apache/1.3/mod_include.so: /usr/sbin/apache: undefined symbol: include_module
/usr/sbin/apachectl start: httpd could not be started

---- ok, wait up.  I noticed that I shouldn't update the modules.conf file manually... so now I ran:

$ sudo /usr/sbin/apache-modconf apache enable mod_include
Replacing config file /etc/apache/modules.conf with new version

told it to install the package maintainers updated version then in which I noticed added the line:
LoadModule includes_module /usr/lib/apache/1.3/mod_include.so
(note the "S"!!!)

now:
$ sudo apachectl start
/usr/sbin/apachectl start: httpd started

woot! woot!  ssi working, but not this thing yet:
[http://www.barcahall.com/gallery-block-random.html](http://www.barcahall.com/gallery-block-random.html)

just posting in case it might help another.

---

