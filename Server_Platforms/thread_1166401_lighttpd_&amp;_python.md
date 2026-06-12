---
title: "lighttpd &amp; python"
date: 2009-05-21
forum: Server Platforms
---

### Post by Bios Element on 2009-05-21
Has anyone had much luck getting lighttpd and python or more particularly, django working? I've spend the last day looking around to find a working tutorial and have yet to find anything that looked very relevant.

Here's my mod_fastcgi config file. I just don't know how to correctly add python/django to this.

```

server.modules += ("mod_fastcgi")
fastcgi.server = ( ".php" =>
  ( "localhost" =>
    (
      "bin-path" => "/usr/bin/php5-cgi",
      "socket" => "/tmp/php.socket"
    )
  ),
)

```

---

### Post by Dysport on 2009-07-30
In case you haven't solved the problem yet:
```
sudo nano /etc/lighttpd/conf-enabled/10-cgi.conf
```

Now add the following lines at the end of the file:
```
$HTTP["url"] =~ "^/cgi-bin/" {
        cgi.assign = ( ".py" => "/usr/bin/python" )
}

```

This way a python script becomes executable by your webserver as soon as it's in a folder named "cgi-bin"
If you want to run scripts in other folders as well you might want to comment out some of the lines at the end of the file, in your case:
```
## Warning this represents a security risk, as it allow to execute any file
## with a .pl/.php/.py even outside of /usr/lib/cgi-bin.
#
#cgi.assign      = (                   <= This line …
#       ".pl"  => "/usr/bin/perl",
#       ".php" => "/usr/bin/php-cgi",
#       ".py"  => "/usr/bin/python",   <= … and this …
#)                                     <= … and lastly this one.

```
so it looks like this:
```
## Warning this represents a security risk, as it allow to execute any file
## with a .pl/.php/.py even outside of /usr/lib/cgi-bin.
#
cgi.assign      = (
#       ".pl"  => "/usr/bin/perl",
#       ".php" => "/usr/bin/php-cgi",
       ".py"  => "/usr/bin/python",
)

```

Hope that was helpful.

---

### Post by durand on 2010-08-11
Thanks Dysport!

---

