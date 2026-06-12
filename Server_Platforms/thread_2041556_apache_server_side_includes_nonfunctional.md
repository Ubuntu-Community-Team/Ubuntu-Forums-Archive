---
title: "apache: server side includes nonfunctional?"
date: 2012-08-12
forum: Server Platforms
---

### Post by illumilore on 2012-08-12
I followed the instructions from [http://httpd.apache.org/docs/current/howto/ssi.html](http://httpd.apache.org/docs/current/howto/ssi.html) , making sure .htaccess works, and has the proper permissions by putting AllowOverride All in apache2.conf under the proper directory. The page loads, but the <!--#include virtual="http://192.168.1.5/htc/sidebar.shtml" --> does nothing. I am getting two errors everytime I load the page:
```

[error] an unknown filter was not added: includes
[error] [client 192.168.0.1] (13)Permission denied: cannot read directory for multi: /var/www/

```
The first one seems to be caused by the AddOutputFilter INCLUDES .shtml in my htaccess file, which is strange because adding that line was in the tutorial.
For the second, it doesn't seem to be related to the include not working, as the webpage loads just fine other than the include missing.

---

### Post by TheFu on 2012-08-12
I think SSI only works for local files, for example:
```
 <!--#include virtual="/footer.shtml" -->
```Not with remote websites.  OTOH, I've never tried to use it any other way.

Did you enable the SSI module in apache? I don't think it is enabled by default. 
Does /etc/apache2/mods-enabled/include.load link properly?

---

### Post by Doug S on 2012-08-13
When I last looked into SSI (Server Side Includes), the apache web site notes were not correct for ubuntu and a little obsolete. (I don't know if that is still true.)
For a how to, try this: [https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes) I know for sure that those instructions worked back in March/April for Ubuntu 12.04, and I think 10.10.
 
I don't know about an external link, as TheFu mentioned, I never tried it.
 
If your version of Ubuntu is new enough, then you do not need to add the AddOutputFilter INCLUDES .shtml line, as it will already be in /etc/apache2/mods-available/mime.conf.

---

### Post by SeijiSensei on 2012-08-13
I don't think you can include external URLs either, but you can do this in PHP.  You do need to change "allow_url_include = Off" to "On" in /etc/php5/apache2/php.ini to make that work, though.  Then you can write a page like this:

```

[HTML code]
<?php include("http://192.168.1.5/htc/sidebar.shtml")?>
[rest of HTML code]

```

Another solution might be to export the directory containing sidebar.shtml with NFS or CIFS and mount it on the webserver.  That would make the remote file "local" to the machine that needs to do the include.

---

