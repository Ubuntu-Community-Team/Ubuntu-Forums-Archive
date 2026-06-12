---
title: "How to coax Apache to download a file"
date: 2008-12-16
forum: Server Platforms
---

### Post by GrandBob on 2008-12-16
I'm having a blast writing my website with BASH.  Everything was sailing along swimmingly until I exerted a downloading link.  Zip, zero, nada.  I consolidated the issue into a small example which fails.

I have experimented with several pokes at this and that, all to no avail. Also, as to an **.htaccess** file, the Apache docs intimate that I should not require one.  Nothing exotic here... only mp3 podcast files.

We're in the directory holding the object files. For purposes of illustration, we'll focus on one file.

[B]$ pwd
/home/grandbob/dcs/audiovisual
$ ls -hog | tail -n1
-rw-r--r-- 1  11M 2008-12-16 07:37 GORP.mp3[/B]

Now the directory with the CGI executable...

[B]/home/grandbob/dcs
$ ls -hog download
-rwxr-xr-x 1 139 2008-12-16 07:36 download
$ cat download
#!/bin/bash
	echo	'Content-type: text/html'
	echo
	echo	'Hello from '$(pwd)
	echo	'<br>'
	echo	'<a href="/dcsfiles/GORP.mp3">Download</a>[/B]

This is what I have in my apache site file.

[B]$ sed '86,$d' /etc/apache2/sites-available/default | sed '1,66d'
# CGI executable
ScriptAlias /dcs/ /home/grandbob/web/dcs/
<Directory "/home/grandbob/web/dcs">
	AllowOverride None
	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	SetHandler cgi-script
	Order allow,deny
	Allow from all
</Directory>

# CGI object files to be downloaded
ScriptAlias /dcsfiles/ /home/grandbob/dcs/audiovisual/
<Directory "/home/grandbob/dcs/audiovisual">
	AllowOverride None
	Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	SetHandler cgi-script
	Order allow,deny
	Allow from all
</Directory>[/B]

And this in my mime table...

[B]$ grep mp3 /etc/mime.types
audio/mpeg	mpga mpega mp2 mp3 m4a[/B]

Then restart apache... by log entry, it is happy.

[B]$ sudo /etc/init.d/apache2 restart
  (blah, blah, ...)
$ tail -n1 /var/log/apache2/error.log
[Tue Dec 16 08:00:15 2008] [notice] Apache/2.2.8 (Ubuntu) DAV/2
 SVN/1.4.6 PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8
 OpenSSL/0.9.8g configured -- resuming normal operations[/B]

The browser paints a good screen.

[B]$ lynx [https://localhost/dcs/download](https://localhost/dcs/download)

   Hello from /home/grandbob/web/dcs
   [COLOR="DarkOrchid"]Download[/COLOR][/B]

The "source view" screen looks good.

[B]Hello from /home/grandbob/web/dcs
<br>;
<a href="/dcsfiles/GORP.mp3">Download</a>[/B]

Exerting the download rudely respond[FONT="Microsoft Sans Serif"][/FONT]s...

[B]                             Internal Server Error

   The server encountered an internal error or misconfiguration and was
   unable to complete your request.

   Please contact the server administrator, webmaster@localhost and inform
   them of the time the error occurred, and anything you might have done
   that may have caused the error.

   More information about this error may be available in the server error
   log.
     __________________________________________________________________


    Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 PHP/5.2.4-2ubuntu5.3 with
    Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g Server at localhost Port
    443[/B]

[SIZE="4"][COLOR="Red"]What now, Kemosabe?[/COLOR][/SIZE]

---

### Post by Wayne_V on 2008-12-16
$ tail -f /var/log/apache2/*log

Then hit the download again.   It may become apparent .....

---

### Post by windependence on 2008-12-16
You ARE a masochist aren't you? :)

I suspect without even looking at the logs that this is a permissions problem. The file that you are putting out there for download must be at least world readable.

As to the .htaccess file, no you don't need one at all, in fact I try not to have any of these on my commercial sites. Makes admin a lot simpler.

-Tim

---

### Post by GrandBob on 2008-12-24
Wayne and Tim,

Thank you for your time and efforts.  Your suggestions sent me down a classic path of step-by-step eliminations which lead me to the golden fleece.

My mistake was a bad case of Apache configuration speak.

Should have used Alias, not ScriptAlias, which I pasted from a working <Location> for CGI scripts, not data files.

Order has been restored to my Apache universe.

Thanks again.

---

