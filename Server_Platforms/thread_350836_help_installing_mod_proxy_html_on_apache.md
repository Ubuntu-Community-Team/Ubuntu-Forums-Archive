---
title: "help installing mod_proxy_html on apache"
date: 2007-02-01
forum: Server Platforms
---

### Post by funkar on 2007-02-01
Hello everyone,

i am a newbie and I am having problems installing mod_proxy_html module on apache. I have already configured reverse proxy using standard apache module but i need to install this mod_proxy_html to rewrite URLs in the HTML pages. 

system configurations are:

```
Kubunto Edgy 
KDE 3.5.5
Apache 2
libxml2

```

i have installed mod_proxy_html module using apt-get  (libapache2-mod-proxy-html). I have added thse links in the apache2 config file

```
LoadFile /usr/lib/libxml2.so
LoadModule proxy_html_module /usr/lib/apache2/modules/mod_proxy_html.so
```

when i start the apache server i can see these warnings in error log file

```
[Thu Feb 01 09:49:04 2007] [warn] module proxy_html_module is already loaded, skipping
[Thu Feb 01 09:49:04 2007] [notice] Apache/2.0.55 (Ubuntu) proxy_html/2.4 mod_jk/1.2.18 configured -- resuming normal operations
```

according to this this module is loaded and now i should be able to use this.  but the following settings in the apache2 config file doesnt do anything! infact its not even parsing the values (i tried putting some typos in the lines but apache loaded the file). does it mean that apache actually didnt load the mod_proxy.c module?  

```
<IfModule mod_proxy.c>
    ProxyRequests Off
    ProxyPass /local/ http://example.org/
    ProxyPassReverse /local/ http://example.org/
    ProxyHTMLURLMap http://example.org /local
    SetOutputFilter  proxy-html
    ProxyHTMLURLMap  /      /local/
    ProxyHTMLURLMap  /local  /local
</IfModule>

```

i would be thankful if anyone can help me with this issue.

thanks.

---

### Post by GSMD on 2007-04-23
Seems like there's smth wrong with mod_proxy_html in Ubuntu, or ProxyHTMLURLMap has been deprecated.

Do you have any success on this?

---

### Post by eantoranz on 2007-05-09
Has any of you made apache2 work with mod_proxy_html?

I've had too many attempts to make it, but nothing seems to work.

feisty here.

---

### Post by GSMD on 2007-05-10
Have a look: [http://www.centricware.org/confluence/display/UKB/apache2+proxying](http://www.centricware.org/confluence/display/UKB/apache2+proxying)

---

### Post by eantoranz on 2007-05-10
It requires authentication and I don't see a place to register: in other words, can't see it. :(

---

### Post by huggy77 on 2007-05-15
any word on this... i am stuck - i am trying to get proxypass working and i need mod proxy

---

### Post by eantoranz on 2007-05-15
ProxyPass works like a charm. All you have to do is enable the mod_proxy module (or force its load in the apache configuration file) and put the ProxyPass clause. 

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypass](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#proxypass)

---

### Post by huggy77 on 2007-05-15
i cant find mod_proxy in my available mod folder under apache...  do i have to recompile apache2?

thanks for the help

---

### Post by huggy77 on 2007-05-15
found it under : /usr/lib/apache2/modules/

oops...

---

### Post by DeHorde on 2007-08-08
htttpd.conf in /etc/apache2/ might be depricated, but I like it, cause it keeps all your tweaks in one place. 
Just find the line in apache2.conf where it includes this file, and move it to the end of apache2.conf. Also, I found that removing the link /etc/apache2/sites-enabled/000-default gave me back some control. 

as for the loading of modules, you do not need to do that by hand: 
a2enmod en a2dismod do this nicely. Just use one of those commands without any options and see what you can add/ can remove (ctrl+c cancels)

same goes for enabling and disabling sites: a2ensite a2dissite 

I wanted mod_proxy_html version 3.0 for its exented options, so I did the following (this might be wrong, harmfull, or just plain ugly and if it breaks anything you get to keep the pieces,  but it works for me!(tm)):

```
root@vmhost:~# cat mod_proxy_html-3.0-howto.txt
Okay, I don't know if I did this right, but:
wget http://apache.webthing.com/mod_proxy_html/mod_proxy_html.tgz
tar -tvzf mod_proxy_html.tgz
tar -xvzf mod_proxy_html.tgz
cd mod_proxy_html

apt-get install apache2-prefork-dev
apt-get install libxml2-dev
ln -s /usr/include/libxml2/libxml /usr/include/libxml
apxs2 -i -c mod_proxy_html.c

What happened was:

/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i486-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql  -c -o mod_proxy_html.lo mod_proxy_html.c && touch mod_proxy_html.slo
/usr/share/apr-1.0/build/libtool --silent --mode=link --tag=disable-static i486-linux-gnu-gcc -o mod_proxy_html.la  -rpath /usr/lib/apache2/modules -module -avoid-version    mod_proxy_html.lo
/usr/share/apache2/build/instdso.sh SH_LIBTOOL='/usr/share/apr-1.0/build/libtool' mod_proxy_html.la /usr/lib/apache2/modules
/usr/share/apr-1.0/build/libtool --mode=install cp mod_proxy_html.la /usr/lib/apache2/modules/
cp .libs/mod_proxy_html.so /usr/lib/apache2/modules/mod_proxy_html.so
cp .libs/mod_proxy_html.lai /usr/lib/apache2/modules/mod_proxy_html.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/apache2/modules
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/apache2/modules

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
chmod 644 /usr/lib/apache2/modules/mod_proxy_html.so

root@vmhost:~/mod_proxy_html# ls
COPYING           mod_proxy_html.la  mod_proxy_html.slo  README
mod_proxy_html.c  mod_proxy_html.lo  proxy_html.conf

root@vmhost:~/mod_proxy_html# cat proxy_html.conf

# Configuration example.
#
# First, to load the module with its prerequisites
#
# For Unix-family systems:
# LoadFile      /usr/lib/libxml2.so
# LoadModule    proxy_html_module       modules/mod_proxy_html.so
#
# For Windows (I don't know if there's a standard path for the libraries)
# LoadFile      C:/path/zlib.dll
# LoadFile      C:/path/iconv.dll
# LoadFile      C:/path/libxml2.dll
# LoadModule    proxy_html_module       modules/mod_proxy_html.so
#
# All knowledge of HTML links has been removed from the mod_proxy_html
# code itself, and is instead read from httpd.conf (or included file)
# at server startup.  So you MUST declare it.  This will normally be
# at top level, but can also be used in a <Location>.
#
# Here's the declaration for W3C HTML 4.01 and XHTML 1.0

ProxyHTMLLinks  a               href
ProxyHTMLLinks  area            href
ProxyHTMLLinks  link            href
ProxyHTMLLinks  img             src longdesc usemap
ProxyHTMLLinks  object          classid codebase data usemap
ProxyHTMLLinks  q               cite
ProxyHTMLLinks  blockquote      cite
ProxyHTMLLinks  ins             cite
ProxyHTMLLinks  del             cite
ProxyHTMLLinks  form            action
ProxyHTMLLinks  input           src usemap
ProxyHTMLLinks  head            profile
ProxyHTMLLinks  base            href
ProxyHTMLLinks  script          src for

# To support scripting events (with ProxyHTMLExtended On),
# you'll need to declare them too.

ProxyHTMLEvents onclick ondblclick onmousedown onmouseup \
                onmouseover onmousemove onmouseout onkeypress \
                onkeydown onkeyup onfocus onblur onload \
                onunload onsubmit onreset onselect onchange

# If you need to support legacy (pre-1998, aka "transitional") HTML or XHTML,
# you'll need to uncomment the following deprecated link attributes.
# Note that these are enabled in earlier mod_proxy_html versions
#
# ProxyHTMLLinks        frame           src longdesc
# ProxyHTMLLinks        iframe          src longdesc
# ProxyHTMLLinks        body            background
# ProxyHTMLLinks        applet          codebase
#
# If you're dealing with proprietary HTML variants,
# declare your own URL attributes here as required.
#
# ProxyHTMLLinks        myelement       myattr otherattr
#
# Also at top level in httpd.conf, you can declare charset aliases.
# This is the most efficient way to support encodings that libxml2
# doesn't natively support.  See the documentation at
# http://apache.webthing.com/mod_proxy_html/

```

in httpd.conf:
```
Include /etc/apache2/mods-enabled/proxy_html.conf
SetOutputFilter proxy-html
ProxyHTMLExtended On
#ProxyHTMLURLMap http://vm01 /foo
ProxyHTMLLinks option value
ProxyHTMLURLMap (.*)http://vm01(.*) $1/foo$2 Ril

```

If anyone sees any fault in what I've done, I'd be grateful if you added your comments!

---

