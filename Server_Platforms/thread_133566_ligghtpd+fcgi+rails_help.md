---
title: "ligghtpd+fcgi+rails help"
date: 2006-02-20
forum: Server Platforms
---

### Post by firecat53 on 2006-02-20
Hey...I'm trying to get lighttpd+fcgi+rails working and it's almost there, except for the fcgi.

Configuration:  ruby1.9 and rails from ubuntu repositories, ruby gems .8.11 from source, ruby-fcgi-0.8.6 from source, lighttpd CVS (compiled), fcgi-2.4.0 from source. No PHP installed (yet).

Everything installs fine.  I made a test rails directory ("rails test") that worked fine.  The webrick server starts fine with "ruby script/server webrick". When I try "ruby script/server", gives the following:
```

=> Booting lighttpd (use 'script/server webrick' to force WEBrick)
=> Rails application started on http://0.0.0.0:3000
=> Call with -d to detach (requires absolute paths in config/lighttpd.conf)
=> Ctrl-C to shutdown server (see config/lighttpd.conf for options)
2006-02-20 09:49:57: (mod_fastcgi.c.1009) execve failed for: public/dispatch.fcgi No such file or directory
2006-02-20 09:49:57: (mod_fastcgi.c.1035) the fastcgi-backend public/dispatch.fcgi failed to start:
2006-02-20 09:49:57: (mod_fastcgi.c.1039) child exited with status 2 public/dispatch.fcgi
2006-02-20 09:49:57: (mod_fastcgi.c.1042) if you try do run PHP as FastCGI backend make sure you use the FastCGI enabled version.
You can find out if it is the right one by executing 'php -v' and it should display '(cgi-fcgi)' in the output, NOT (cgi) NOR (cli)
For more information check http://www.lighttpd.net/documentation/fastcgi.html#preparing-php-as-a-fastcgi-program
2006-02-20 09:49:57: (mod_fastcgi.c.1047) If this is PHP on Gentoo add fastcgi to the USE flags
2006-02-20 09:49:57: (mod_fastcgi.c.1337) [ERROR]: spawning fcgi failed.
2006-02-20 09:49:57: (server.c.834) Configuration of plugins failed. Going down.
``` The file "public/dispatch.fcgi" exists within the rails test directory, so I'm not sure why it's saying it doesn't exist.

The rails generated lighttpd.conf file in test/config is:
```
 # Default configuration file for the lighttpd web server
# Start using ./script/server lighttpd

server.port = 3000

server.modules           = ( "mod_rewrite", "mod_accesslog", "mod_fastcgi" )
server.error-handler-404 = "/dispatch.fcgi"
server.document-root     = "public/"

server.errorlog          = "log/lighttpd.error.log"
accesslog.filename       = "log/lighttpd.access.log"

url.rewrite              = ( "^/$" => "index.html", "^([^.]+)$" => "$1.html" )

# Change *-procs to 2 if you need to use Upload Progress or other tasks that
# *need* to execute a second request while the first is still pending.
fastcgi.server = ( ".fcgi" =>
  ( "localhost" =>
      (
        "min-procs" => 1,
        "max-procs" => 1,
        "socket"    => "log/fcgi.socket",
        "bin-path"  => "public/dispatch.fcgi",
        "bin-environment" => ( "RAILS_ENV" => "development" )
      )
  )
)

mimetype.assign = (
  ".css"        =>  "text/css",
  ".gif"        =>  "image/gif",
  ".htm"        =>  "text/html",
  ".html"       =>  "text/html",
  ".jpeg"       =>  "image/jpeg",
  ".jpg"        =>  "image/jpeg",
  ".js"         =>  "text/javascript",
  ".png"        =>  "image/png",
  ".swf"        =>  "application/x-shockwave-flash",
  ".txt"        =>  "text/plain"
)
``` 
Can anyone help? I'm still trying to wrap my brain around ruby and rails!!

Thanks, Scott

---

### Post by firecat53 on 2006-02-21
Ok...solved.  Had to change the path to the dispatch.fcgi in lighttpd.conf to an absolute path:

        "bin-path"  => CWD + "/public/dispatch.fcgi",

Apparently this is fixed in lighttpd 1.4.10, but the lighgtpd config file that rails generated still had a relative path.

---

