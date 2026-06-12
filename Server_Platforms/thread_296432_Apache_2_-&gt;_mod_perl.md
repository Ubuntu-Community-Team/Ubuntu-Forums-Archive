---
title: "Apache 2 -&gt; mod_perl"
date: 2006-11-09
forum: Server Platforms
---

### Post by Kurt` on 2006-11-09
Hi,

I've apt-get installed apache2-mpm-prefork and libapache2-mod-perl2.

The mod_perl module is loaded (symlinked into mods-enabled), and I've verified that it's running, but I can't seem to find out how to enable directories to parse .pl files as perl scripts! :P

I'm aware of the AddHandler directive, but I can't seem to find one for mod_perl (shouldn't it have been automatically added?). All of the documentation I can find online is for mod_perl for apache 1... any help would be greatly appreciated!

Thanks :D

---

### Post by cotn on 2006-11-10
To parse .pl files as perl scripts with apache I think you need cgi.

So you have added the folloing line to youre configuration: 
AddHandler cgi-script .cgi .pl.

Do you have cgi.load in your mods-enabled directory ?
Generally you can parse .pl files in your htdocs directory structure or where you have defined the directory for your webserver.

---

### Post by Kurt` on 2006-11-10
Thank you for the reply.

I added the SetHandler directive to /etc/apache2/apache2.conf (since it was not already in there). The cgi.load file is symlinked into mods-enabled, and is running.

When I request my Perl file, this is the result:

```
GET /cgi-bin/test.pl HTTP/1.1

HTTP/1.x 500 Internal Server Error
Date: Fri, 10 Nov 2006 17:51:55 GMT
...
Content-Length: 0
Connection: close
Content-Type: text/x-perl

```

And it prompts me to download a 0 byte file called test.pl. Any ideas?

Thanks again!

P.S. I assumed mod_perl would be like PHP: just apt-get it and restart Apache. :>

---

### Post by cotn on 2006-11-11
ok. Do you have added Exec CGI in youre virtual host file ?
 
By example: 

/etc/apache2/sites-enabled/000-default 
```

    <Directory "/var/www/mywebspace"> 
        Options Indexes ExecCGI FollowSymLinks MultiViews # See this line
        AllowOverride Options AuthConfig FileInfo Indexes Limit
        Order allow‚deny
        Allow from all
    </Directory>

```


I assume you know whre perl is and otherwise do: > which perl
Something like "#!/usr/bin/perl" must be in top of youre test.pl

Also important is to chmod youre perl files: chmod 755 test.pl (if you upload, upload in ascci)

Does this works in ssh/telnet/shell:  > perl -d test.pl 
This runs the first line

And the whole file: > perl test.pl
This runs the complete script


Then try it in youre browser.

If you still get an HTTP/1.x 500 Internal Server Error, then  check youre apache error.log. If you see something like: 

[error] [client 127.0.0.1] Premature end of script headers: "/var/www/mywebspace/cgi-bin/test.pl"

In most cases this is a script error:
The script has stopped for some reasons before it returned any output to the web server. Before printing any HTML its neccesary  to tell the script to set the content type to text/html, this is done by sending a header, like this:

```

print "Content-type: text/html\n\n";

```

---

