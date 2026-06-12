---
title: "Apache CGI configuration problem"
date: 2009-01-30
forum: Server Platforms
---

### Post by vital101 on 2009-01-30
Hey everyone,

I've lately been trying to get cgi scripts to work on a pre-existing installation of Apache on Ubuntu.  I made sure to install the libapache2-mod-perl2 package and then reload the web server.  However, when I go to "http://www.mysite.com/cgi-bin/script.cgi", I just get a blank page.  The script has 0755 permissions as well.

My virtual server file for this site looks like:
```

<VirtualHost *>
SuexecUserGroup "#1007" "#1009"
ServerName wrestlingaddix.com
ServerAlias www.wrestlingaddix.com
DocumentRoot /home/wrestlingaddix/public_html
ErrorLog /home/wrestlingaddix/logs/error_log
CustomLog /home/wrestlingaddix/logs/access_log combined
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/wrestlingaddix/public_html>
Options Indexes IncludesNOEXEC FollowSymLinks
allow from all
AllowOverride All
</Directory>
ScriptAlias        /cgi-bin/  "/home/wrestlingaddix/public_html/cgi-bin/"
<Directory "/home/wrestlingaddix/public_html/cgi-bin">
        Options ExecCGI
        AddHandler cgi-script cgi pl
</Directory>

</VirtualHost>

```

Any help would be greatly appreciated.  Thanks.

---

### Post by RealPSL on 2009-02-01
Maybe the configuration is right and the script you are running is wrong. What happens if you put a script like the one below as a test and try to access it via your web server:
```

#!/usr/bin/perl

print "Content-type:text/html\n\n";

print "<html><head><title>Hello World!</title>\n\n";
print "<body>\n";
print "<p><b>Hello World!</b></p>\n";
print "</body></html>";

```

Do not forget to set the permissions on this one too.

---

### Post by vital101 on 2009-02-02
Okay, per your advice, I'd added the script to my cgi-big directory.

If I name the script test.pl and try to access it from the browser, it claims that the file doesn't exist on the server (404).  I then renamed it to test.cgi, and it says the file exists, but I get a blank page.  I checked the source and it is also blank.

Any ideas?

Thanks.

---

### Post by albinootje on 2009-02-02
> **vital101 said:**
>  If I name the script test.pl and try to access it from the browser, it claims that the file doesn't exist on the server (404).  

For cgi problems (and the like) you should always check the apache logfiles to see whether error messages in there can help out debugging the problem.

---

### Post by vital101 on 2009-02-02
I checked the error_log and I kept getting an error like this for any CGI script.

> 
[Mon Feb 02 21:27:31 2009] [error] [client 24.247.207.54] suexec policy violation: see suexec log for more details
[Mon Feb 02 21:27:31 2009] [error] [client 24.247.207.54] Premature end of script headers: test.cgi


I don't even know where to look for the suexec log.  Are there any known issues like this for Ubuntu servers running apache2?

---

### Post by albinootje on 2009-02-02
> **vital101 said:**
>  I don't even know where to look for the suexec log.

I've never used suexec myself yet, but perhaps this is useful :
[http://httpd.apache.org/docs/1.3/suexec.html#debug](http://httpd.apache.org/docs/1.3/suexec.html#debug)

---

### Post by vital101 on 2009-02-02
Maybe some more useful information that I don't understand.

> 
[2009-02-02 21:27:31]: uid: (1007/wrestlingaddix) gid: (1009/1009) cmd: test.cgi
[2009-02-02 21:27:31]: command not in docroot (/home/wrestlingaddix/public_html/cgi-bin/test.cgi)


---

### Post by albinootje on 2009-02-03
> **vital101 said:**
> Maybe some more useful information that I don't understand.
Could it simply be that your script tries to run a command which is not in your DocumentRoot ?

---

### Post by vital101 on 2009-02-04
Probably.  But I don't really know what that means or how to fix it.  I googled around and most responses say I need to re-compile apache.  However, this is apache under ubuntu, which is a pre-compiled package.  I am also running webmin, which may be having some strange effect.

---

### Post by albinootje on 2009-02-04
> **vital101 said:**
> Probably.  But I don't really know what that means or how to fix it. 

Would you mind publishing your test.cgi ?
Or telling us which perl and/or cgi scripts you eventually want to run ?

---

### Post by vital101 on 2009-02-04
For my test.cgi, I'm using the code from the 2nd reply in this thread.

---

### Post by albinootje on 2009-02-04
> **vital101 said:**
> For my test.cgi, I'm using the code from the 2nd reply in this thread.

Okay, good.
I just did the following :
1) Put test.cgi in /usr/lib/cgi-bin/
2) Did a chmod 755 on /usr/lib/cgi-bin/test.cgi
3) Loaded localhost/cgi-bin/test.cgi in Firefox.

And that worked fine.
I'm using apache2 on Ubuntu 8.04 without much customization at all.

---

### Post by RealPSL on 2009-02-04
The problem is not the script or the permissions. The problem is suexec is very strict about where you can place files, who can own them and what permissions they can have. To me from what I have read it is more trouble than it is worth. Below is the link I read I think the key to solving this problem is figuring out what Ubuntu has the docroot for suexec set to.

[http://httpd.apache.org/docs/2.0/suexec.html]("http://httpd.apache.org/docs/2.0/suexec.html")

Read the security model section and the section I quoted below

> --with-suexec-docroot=DIR
    Define as the DocumentRoot set for Apache. This will be the only hierarchy (aside from UserDirs) that can be used for suEXEC behavior. The default directory is the --datadir value with the suffix "/htdocs", e.g. if you configure with "--datadir=/home/apache" the directory "/home/apache/htdocs" is used as document root for the suEXEC wrapper.

---

### Post by vital101 on 2009-02-06
Thanks everyone for the help.  In the end, I found the problem in my Apache configuration for the web site.  At the very top of the file there was a line that went something like:
> 
SuExec id "#1007 #1009"


I just removed that line and everything worked perfectly.

---

