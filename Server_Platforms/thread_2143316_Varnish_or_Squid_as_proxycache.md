---
title: "Varnish or Squid as proxy/cache?"
date: 2013-05-08
forum: Server Platforms
---

### Post by Lars Noodén on 2013-05-08
I'm familiar with using and configuring Squid as a proxy/cache.  I see lots of material referring to Varnish as an accelerator/reverse proxy, but (a dumb question) is it also useful as a proxy/cache? 

I'm not finding material on using Varnish as a proxy/cache and vcl is, so far, greek to me.   So I would appreciate pointers to some simple introductions.  I'm aware of the examples at [www.varnish-cache.org](www.varnish-cache.org) but looking for something even more elementary, including ACLs.

---

### Post by Habitual on 2013-05-09
Lars:
I hope this helps you out.
It's a recipe/cheat from my recent varnish3 install and config for a client.
**/etc/default/varnish**

  ```
START=yes
NFILES=131072
MEMLOCK=82000
DAEMON_OPTS="-a :80 \
             -T 0.0.0.0:6082 \
             -f /etc/varnish/default.vcl \
             -S /etc/varnish/secret \
             -s malloc,256m"

   ## Alternative 4, Do It Yourself
#
# DAEMON_OPTS=""

```

**/etc/varnish/default.vcl**

  ```
backend default {
   .host = "FQDN.com"; <--- NO Changes are required on this host. # can also be an /etc/hosts entry. ;)
   .port = "80";  
}

```


**/etc/apache2/ports.conf**

  ```
NameVirtualHost *:8080
Listen 127.0.0.1:8080

   <IfModule mod_ssl.c>
    Listen 443
</IfModule>

   <IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```
but that ports.conf is from the remote "backend" from above stanza.
If httpd is using something other than '80" that should be changed in the default.vcl

the varnish host was/is .243
the web host is .245
I installed varnish on .243 and configured it to 
cache the .245:80 traffic.
A Records point to .243 in this case.

Subscribed with interest...

Edit:
 ```
netstat -pntl | grep -E "apache2|varnish"
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      11694/varnishd  
tcp        0      0 127.0.0.1:8080          0.0.0.0:*               LISTEN      11596/apache2   
tcp        0      0 0.0.0.0:6082            0.0.0.0:*               LISTEN      11692/varnishd  
tcp6       0      0 :::80                   :::*                    LISTEN      11694/varnishd
```

---

### Post by Habitual on 2013-05-09
Everything I have, so far:
[Putting Varnish In Front Of Apache On Ubuntu/Debian]("http://www.howtoforge.com/putting-varnish-in-front-of-apache-on-ubuntu-debian")
[How to Install and Configure Varnish with Apache on Ubuntu 12.04]("https://www.digitalocean.com/community/articles/how-to-install-and-configure-varnish-with-apache-on-ubuntu-12-04--3")

    [Documentation]("https://www.varnish-cache.org/docs/3.0/%20")

[LIST]
[*][Main  documentation site.]("http://varnish-cache.org/docs/") 
[*][Installation]("https://www.varnish-cache.org/docs/3.0/installation/index.html") 
[*][Using Varnish]("https://www.varnish-cache.org/docs/3.0/tutorial/index.html") 
[*][FAQ]("https://www.varnish-cache.org/docs/3.0/faq/index.html") 
[*][Poul-Hennings random outbursts]("https://www.varnish-cache.org/docs/3.0/phk/index.html") 
[*][Glossary]("https://www.varnish-cache.org/docs/3.0/glossary/index.html") 
[*][Index]("https://www.varnish-cache.org/docs/3.0/genindex.html") 
[*][Search Page]("https://www.varnish-cache.org/docs/3.0/search.html") 
[*][Varnish Reference Manual]("https://www.varnish-cache.org/docs/3.0/reference/index.html") 
[*][The Varnish Book]("https://www.varnish-software.com/static/book/#welcome-to-the-varnish-book") 
[*][Introduction]("https://www.varnish-software.com/static/book/Introduction.html%20") 
[*][Getting started]("https://www.varnish-software.com/static/book/Getting_started.html%20") 
[*][Tuning]("https://www.varnish-software.com/static/book/Tuning.html%20") 
[*][HTTP]("https://www.varnish-software.com/static/book/HTTP.html%20") 
[*][VCL Basics]("https://www.varnish-software.com/static/book/VCL_Basics.html%20") 
[*][VCL functions]("https://www.varnish-software.com/static/book/VCL_functions.html%20") 
[*][Cache invalidation]("https://www.varnish-software.com/static/book/Cache_invalidation.html%20") 
[*][Saving a request]("https://www.varnish-software.com/static/book/Saving_a_request.html%20") 
[*][Content Composition]("https://www.varnish-software.com/static/book/Content_Composition.html%20") 
[*][Finishing words]("https://www.varnish-software.com/static/book/Finishing_words.html%20") 
[*][Appendix A: Varnish Programs]("https://www.varnish-software.com/static/book/Appendix_A__Varnish_Programs.html%20") 
[*][Appendix B: Extra Material]("https://www.varnish-software.com/static/book/Appendix_B__Extra_Material.html%20") 
[*][VCL Examples]("https://www.varnish-cache.org/trac/wiki/VCLExamples"), small snippets for doing common tasks. 
[*]The Varnish Book's  [Online Reference]("https://www.varnish-software.com/static/book/") and  [PDF download]("https://www.varnish-software.com/book"). 
[*][VTLA]("https://www.varnish-cache.org/trac/wiki/VTLA"), VTLA documentation 
[*][A collection of ways to use varnishlog]("https://www.varnish-cache.org/trac/wiki/VarnishlogExamples") 
[*][VCL.BNF]("https://www.varnish-cache.org/trac/wiki/VCL.BNF") grammar for VCL 
[*][varnish-software.com]("http://www.varnish-software.com/") is our commercial sister-site 
[*][Debugging Varnish]("https://www.varnish-cache.org/trac/wiki/DebuggingVarnish") 
[*][Performance tuning of Varnish and the underlying OS]("https://www.varnish-cache.org/trac/wiki/Performance") 
[*][Installing Varnish from source code]("https://www.varnish-cache.org/trac/wiki/Installation") 
[*][Developer resources]("https://www.varnish-cache.org/trac/wiki/DeveloperResources") 
[*][Accelerating Wordpress with Varnish]("https://www.varnish-cache.org/trac/wiki/VarnishAndWordpress") 
[*][Varnishing over Drupal]("https://www.varnish-cache.org/trac/wiki/VarnishAndDrupal") 
[*][Varnish over Windows (with Cygwin DLL)]("https://www.varnish-cache.org/trac/wiki/VarnishOnCygwinWindows") 
[*][List of Varnish Modules (aka VMODs)]("https://www.varnish-cache.org/vmods") 
[*][Patchwork (patch tracking system)]("https://www.varnish-cache.org/patchwork") 
[*][Local Varnish User Groups]("https://www.varnish-cache.org/trac/wiki/LVUG") 
[*][Why is there no SSL?]("https://www.varnish-cache.org/docs/3.0/phk/ssl.html") 
[/LIST]
    [Using restarts to try multiple backends]("https://www.varnish-cache.org/trac/wiki/VCLExampleRestarts%20")
[Using directors for load balancing]("https://www.varnish-cache.org/trac/wiki/VCLExampleDirector%20")
[Redirecting the browser to another hostname]("https://www.varnish-cache.org/trac/wiki/VCLExampleHostnameRemapping%20")

---

### Post by Lars Noodén on 2013-05-09
Thanks.  I'd seen all the varnish-cache docs.  The example in #2 helped with VCL though.  I think that I may have a misunderstanding of the capabilities.  I'm looking for this:

```

browser <--> cache <--> Internet <--> server

```

Squid can do that.  Squid can also be an accelerator, which is what Varnish seems to do exclusively.  This is what Varnish seems specialized in:  

```

browser <--> Internet <--> cache <--> server

```

I'm looking for the first case above.  Though, I will look more into VCL because Varnish could come in handy later.

---

