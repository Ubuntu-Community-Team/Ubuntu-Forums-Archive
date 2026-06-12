---
title: "mod_ruby and 403 errors"
date: 2005-04-17
forum: Server Platforms
---

### Post by HungSquirrel on 2005-04-17
I cannot for the life of me get Apache to stop spitting out 403 errors when running Ruby scripts via mod_ruby.  I followed the [instructions](http://www.modruby.net/en/doc/?InstallGuide) to no avail (except for the module loading part...the Ubuntu libapache2-mod-ruby package automagically loads the module).  Apache accepts the config file fine, but when I create a *.rbx Hello World file, Apache gives me 403 errors when I try to access it.  The file is owned by www-data and marked executable (I even went so far as to chmod 777 briefly, no luck!).  If I rename the file to 99.foo, I can access its source just fine.

I get the same error when trying to access scripts in /ruby , following the instructions on the mod_ruby site.  Here is what the instructions told me to put in my apache2.conf, which I did:

```
<IfModule mod_ruby.c>
  RubyRequire apache/ruby-run

  # Excucute files under /ruby as Ruby scripts
  <Location /ruby>
  SetHandler ruby-object
  RubyHandler Apache::RubyRun.instance
  </Location>

  # Execute *.rbx files as Ruby scripts
  <Files *.rbx>
  SetHandler ruby-object
  RubyHandler Apache::RubyRun.instance
  </Files>
</IfModule>
```

This is with Hoary's apache2 and libapache2-mod-ruby packages.  Does anyone have any ideas?  Is the maintainer of mod_ruby in the house?  (The website says he/she has an Ubuntu box.)

---

### Post by alastair on 2005-04-17
Is there anything else in either the Apache access or error log?

---

### Post by HungSquirrel on 2005-04-17
Access log has a bunch of entries similar to this one:
```
192.168.1.102 - - [17/Apr/2005:06:33:45 -0500] "GET /99.rbx HTTP/1.1" 403 368 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.7) Gecko/20050414 Firefox/1.0.3"
```

In the error log, I found the problem:
```
[Sun Apr 17 06:32:44 2005] [error] access to /var/www/99.rbx failed for (null), reason: Options ExecCGI is off in this directory
```

I should have thought to check the logs.  Thanks!

For the curious, I changed the following in /etc/apache2/sites-enabled/default:
```
<Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
</Directory>
```
To:
```
<Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews ExecCGI
            AllowOverride All
            Order allow,deny
            allow from all
</Directory>
```

---

