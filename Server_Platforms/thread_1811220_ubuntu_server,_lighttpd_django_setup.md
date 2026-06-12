---
title: "ubuntu server, lighttpd/ django setup"
date: 2011-07-24
forum: Server Platforms
---

### Post by vanspud on 2011-07-24
Hi,
       I am trying to get a Django(latest dev version) site running on lighttpd/ Ubuntu  server(11.04) for the first time and am not having any success thus far  and was looking for some advice/ assistance.


       My setup is as follows:


       I have "/etc/lighttpd/lighttpd.conf" with the following...
       server.modules = (
        "mod_access",
        "mod_alias",
        "mod_compress",
        "mod_redirect",
        "mod_rewrite",
        #"mod_fastcgi",
)
       server.document-root = "/var/www"
       $HTTP["host"] == "www.mysite.com" {
fastcgi.server = (
    "/mysite.fcgi(where should this file be placed? I have it in my webroot?)" => (
        "main" => (             # Use host / port instead of socket for TCP fastcgi
            #"host" => "127.0.0.1",
            #"port" => 3033,
            "socket" => "/home/phil/projects/mysite/mysite.sock",
            "check-local" => "disable",
        )
    ),
)
}




       But I also have a "lighttpd/conf-enabled/10-fastcgi.conf" file with
the following....
       server.modules += ( "mod_fastcgi" )
       $HTTP["url"] =~ "^/cgi-bin/" {
        cgi.assign = ( ".py" => "/usr/bin/python" )
       }
                 
[LIST=1]
[*]Warning this represents a security risk, as it allow to execute any file
[*]with a .pl/.php/.py even outside of /usr/lib/cgi-bin. #
cgi.assign      = (
[/LIST]

[LIST=1]
[*]      ".pl"  => "/usr/bin/perl",
[*]      ".php" => "/usr/bin/php-cgi",
       ".py"  => "/usr/bin/python",
)
[/LIST]
       

I run the following in "mysite" directory...
./manage.py runfcgi method=prefork socket=/home/phil/projects/mysite/mysite.sock pidfile=django.pid




       I always just get a "Not Found" page, can anyone see where I am  going wrong or if I'm missing something? Any advice is most appreciated, thanks.

---

