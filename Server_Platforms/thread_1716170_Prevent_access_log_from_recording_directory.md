---
title: "Prevent access log from recording directory"
date: 2011-03-28
forum: Server Platforms
---

### Post by dacoder96 on 2011-03-28
Hi,

I am building AJAX into my website and obviously, every HTTP request is being recorded in the access log. I have Googled how to avoid this but I haven't been able to make it work.
Here is the line that I found...
```
SetEnvIf Request_URI "^/ajax$" dontlog
```
If I had a directory in my *htdocs* folder called *ajax*, how do I prevent Apache from logging access to this folder?

Here is the Log Config. part of the *httpd.conf* file
```
#
# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog logs/error_log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn
SetEnvIf Request_URI "^/trash$" dontlog
<IfModule log_config_module>
    #
    # The following directives define some format nicknames for use with
    # a CustomLog directive (see below).
    #

    
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common
    

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O

      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    #
    # The location and format of the access logfile (Common Logfile Format).
    # If you do not define any access logfiles within a <VirtualHost>
    # container, they will be logged here.  Contrariwise, if you *do*
    # define per-<VirtualHost> access logfiles, transactions will be
    # logged therein and *not* in this file.
    #
    CustomLog logs/access_log common

    #
    # If you prefer a logfile with access, agent, and referer information
    # (Combined Logfile Format) you can use the following directive.
    #
    #CustomLog logs/access_log combined
</IfModule>
```


Thank you very much!

---

