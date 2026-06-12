---
title: "403 forbidden on apache2"
date: 2006-02-26
forum: Server Platforms
---

### Post by kasemodz on 2006-02-26
alright I have apache2 installed. The default folder for apache2 is /var/www/. I have an index.html and index.php that work fine. However, I have a file called nph-proxy.cgi and would like to get that to work as well. I placed it in the folder and in apach2.conf in the directory index part i added "nph-proxy.cgi" without the quotes. When i try to access it it gives me a 403 forbidden stating I don't have permission to access /nph-proxy.cgi. What am i doing wrong? I dont know if its the permission problem, because my index.html is user 500, group 500 and the index.php is user root, group root. What should I do?

---

### Post by gruepig on 2006-02-26
You don't want it in DirectoryIndex; that's for files apache should try to serve if you access a directory, rather than a file.

To enable cgis, you need a line like "AddHandler cgi-script .cgi .sh .pl" in your apache2.conf file.  You'll also need to add "ExecCGI" to the Options line for the  directory in sites-enabled/<whatever>.  It's recommended that you have a separate directory just for cgi scripts.  I think the apache2 default config has this, so you just have to put your script wherever it says, and then access it as http://<yoursite>/cgi-bin/nph-proxy.cgi.

---

### Post by kasemodz on 2006-02-26
alright I set up these variables in apache2.conf and httpd.conf

apache2.conf
> AddHandlet cgi-script .cgi .pl
<Directory /var/www/cgi-bin/>
Options + ExecCGI
</Directory>

httpd.conf
> ScriptAlias /cgi-bin/ /var/www/cgi-bin/

then I restarted apache2 and tried to access it by going to
> [http://ipaddress/cgi-bin/nph-proxy.cgi](http://ipaddress/cgi-bin/nph-proxy.cgi)
On internet explorer it said page not found. So then I went back to the files and looked at the ownership. I have an index.html and index.php both owned by user 500 and group 500. The number view under permissions is 644. The text view is > -rw-r--r--
So then I looked at the proxy file and changed the permission to 500:500, number view to 644, and the text view to -rw-r--r--. However, when I do all of that, on the proxy file I get this picture of a lock on the top right of the icon. However, my index.php and index.html don't have that even though the permissions are the same. How do I remove that? Do you think thats causing the problem?

---

### Post by gruepig on 2006-03-01
I think cgi scripts need to be set executable.  Try 'chmod 755 nph-proxy.cgi' or 'chmod ugo+x nph-proxy.cgi'.

A general debugging strategy.  Take a look at /var/log/apache2/*.log.  Specifically, try to access the page via a web browser, and then 'tail /var/log/apache2/*.log' and look at the output.

---

### Post by LordHunter317 on 2006-03-01
Your issue is those directives are being overriden by the vhost directives and it's looking in /usr/lib/cgi-bin, which is teh default installation place for CGI scripts.

You shouldn't set **any** of those directives except for AddHandler globally and should be editing sites-available/default instead.

---

### Post by lailoken on 2006-07-20
You misspelled it?

AddHandlet cgi-script .cgi .pl

should be:

AddHandler cgi-script .cgi .pl


A snippit of my vhosts file looks like:

----

        AddHandler cgi-script .cgi .pl
        <Location /proxy>
                Options ExecCGI FollowSymLinks
                DirectoryIndex nph-proxy.cgi
                AllowOverride None
                SSLRequireSSL
        </Location>

----

Check the file is owned by the proper user, and that it is executable.

---

