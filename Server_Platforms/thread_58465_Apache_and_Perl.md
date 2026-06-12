---
title: "Apache and Perl"
date: 2005-08-20
forum: Server Platforms
---

### Post by Watcher on 2005-08-20
I tried to run some perl scripts on my apache2 server here. But when I opened the file in firefox (by [http://localhost/perl/ed.plx](http://localhost/perl/ed.plx)) I just get my source code, no interpretation what so ever.

Any idea's what I need to change? Apache says that mod_perl is loaded, but not working. If you want some config files, ask, didn't put any here because I don't know which one too post.

---

### Post by gruepig on 2005-08-20
Do you have the file /etc/apache2/mods-enabled/perl.load?  It should be a symlink to /etc/apache2/mods-available/perl.load which should contain the line 'LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so'.

Also if you haven't already, you likely need to add plx to the list of mime types your server knows how to handle.  Edit /etc/mime.types and add 'plx' to the 'text/x-perl' line.  (Or, for that matter, just rename your script to end in .pl.)

If that doesn't fix your problem, post any error messages your seeing in your logs.  As for which config files to post, most of the config (aside from the above-mentioned) is in /etc/apache2/apache2.conf and /etc/apache2/sites-enabled/*.

---

### Post by Watcher on 2005-08-20
Ok tried everything you said already. I don't get too see my source code anymore, now I just get a download question?

I know that perl works on this computer I made already lots of little small perl scripts, but this just won't work :s.

---

### Post by Velox Letum on 2005-08-20
It appears .pl and .plx aren't being recognised by the server as files to be run through PERL before displaying. Make sure that mod_perl is loaded.

---

### Post by LordHunter317 on 2005-08-21
Make sure your scripts can be run with mod_perl before doing so.

Mod_perl normally needs special, per-directory/site configuration before using it.  See the documentaiton at perl.apache.org

Otherwise, you probably want to just do CGI handling of your scripts.  Two ways to do that:[list=1][*]Put all your scripts in a directory and use a ScriptAlias or Options ExecCGI in the Directory directive to enable CGI support on all executable files.[*]Add a handler for CGI scripts ending in .pl.[/list]It's most likely you want the former, not the latter option.

---

### Post by Watcher on 2005-09-04
[QUOTE=LordHunter317]Make sure your scripts can be run with mod_perl before doing so.

Mod_perl normally needs special, per-directory/site configuration before using it.  See the documentaiton at perl.apache.org

Otherwise, you probably want to just do CGI handling of your scripts.  Two ways to do that:[list=1][*]Put all your scripts in a directory and use a ScriptAlias or Options ExecCGI in the Directory directive to enable CGI support on all executable files.[*]Add a handler for CGI scripts ending in .pl.[/list]It's most likely you want the former, not the latter option.[/QUOTE]And can you explain how to do that? I tried a lot of thins but none quite work good, but maybe this is it ](*,)

---

### Post by LordHunter317 on 2005-09-04
[QUOTE=Watcher]And can you explain how to do that? I tried a lot of thins but none quite work good, but maybe this is it ](*,)[/QUOTE]
 If you have a directory of CGI scripts you want to run, and they're outside the webroot (meaning in /usr/local/cgi-bin or similiar, not /var/www/mysite/cgi-bin):```
ScriptAlias /cgi-bin /usr/local/cgi-bin
<Directory /usr/local/cgi-bin>
Options None

Order allow,deny
Allow from all
```Which will make any requests to [http://example.com/cgi-bin/](http://example.com/cgi-bin/) go to /usr/local/cgi-bin on the filesystem.

The second method is if the directory with the scripts is in the DocumentRoot:```

AddHandler cgi-handler .pl

<Directory /var/www/mysite/scripts>
Options +ExecCGI -Indexes

Order allow,deny
Allow from All
```Which does the same.  The first directive is only needed once.

---

