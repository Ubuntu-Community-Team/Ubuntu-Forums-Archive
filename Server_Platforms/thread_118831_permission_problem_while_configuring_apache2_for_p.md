---
title: "permission problem while configuring apache2 for python cgi?"
date: 2006-01-17
forum: Server Platforms
---

### Post by furtivefelon on 2006-01-17
hello everyone!

I'm trying for a couple of hours now to set up apache/python cgi on my
ubuntu development machine.. Though, whenever i go to the cgi file, it
give me a 403 Forbidden page.. Exactly as follows:
Forbidden

You don't have permission to access /www/test.cgi on this server.
Apache/2.0.54 (Ubuntu) mod_python/3.1.3 Python/2.4.2
PHP/5.0.5-2ubuntu1.1 Server at localhost Port 80

My httpd.conf file is as follows(noting that /var/www/ is the folder
where the root www folder resides):
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
AddHandler cgi-script .cgi .py .pl
<Directory /var/www>
Options +ExecCGI
AddHandler cgi-script .cgi .py .pl
</Directory>

Also, i have chmod all file permission to 777..

The content of the cgi is the most basic testing script and should not
have any problems, is as follows:
#!/usr/bin/python

# Required header that tells the browser how to render the text.
print "Content-Type: text/plain\n\n"

# Print a simple message to the display window.
print "Hello, World!\n"

Anyone know what am i doing wrong?

Thanks alot!

---

### Post by TFleck on 2007-02-09
I'm having the same problem here, does anyone knows how to solve this?

---

### Post by conjur3r on 2007-02-09
> **furtivefelon said:**
> 
You don't have permission to access /www/test.cgi on this server.
Apache/2.0.54 (Ubuntu) mod_python/3.1.3 Python/2.4.2
PHP/5.0.5-2ubuntu1.1 Server at localhost Port 80

My httpd.conf file is as follows(noting that /var/www/ is the folder
where the root www folder resides):
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
AddHandler cgi-script .cgi .py .pl
<Directory /var/www>
Options +ExecCGI
AddHandler cgi-script .cgi .py .pl
</Directory>

Also, i have chmod all file permission to 777..



Whenever you obtain apache errors, your first point of call is to check the apache error log for any further information.

Why is it saying /www/test.cgi when the file resides in /var/www/test.cgi ?  According to your apache configs, only /var/www/*.cgi are eligible to be executed.  Is there a symbolic link for /www and /var/www ???

Failing all this, you may need an "Allow from all", eg:

<Directory /var/www>
Options +ExecCGI
AddHandler cgi-script .cgi .py .pl
Allow from all
</Directory>

[http://httpd.apache.org/docs/2.0/mod/mod_access.html#allow](http://httpd.apache.org/docs/2.0/mod/mod_access.html#allow)

---

