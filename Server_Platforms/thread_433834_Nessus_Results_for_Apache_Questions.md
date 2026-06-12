---
title: "Nessus Results for Apache Questions"
date: 2007-05-05
forum: Server Platforms
---

### Post by Dark Elitist on 2007-05-05
Hello,

My first time setting up a LAMP server and I have a few questions regarding security.

After successfully setting up the server, I went ahead and ran a full Nessus scan, dangerous options enabled.  Only one actual hole was found, that doesn't seem to appear to affect Linux but it would still be nice to know how to fix just for kicks, and a recommendation that I can't seem to find any clear solution to performing.

> It was possible to freeze or reboot Windows by
reading a MS/DOS device through HTTP, using
a file name like CON\CON, AUX.htm or AUX.

A cracker may use this flaw to make your
system crash continuously, preventing
you from working properly.

Solution: upgrade your system or use a 
HTTP server that filters those names out.

Risk Factor : High
CVE : CVE-2001-0386, CVE-2001-0493, CVE-2001-0391, CVE-2001-0558, CVE-2002-0200, CVE-2000-0168, CVE-2003-0016, CVE-2001-0602
BID : 1043, 2575, 2608, 2622, 2649, 2704, 3929, 6659, 6662
Plugin ID : 10930

Is there an easy way to fix this just so my Nessus doesn't show any holes?

Also, this recommendation was made but I can't find any specific direction that make sense to me as to how to go about performing it; where and between what do I put the code it recommends inserting into what configuration file?

> Synopsis :

Debugging functions are enabled on the remote HTTP server.

Description :

The remote webserver supports the TRACE and/or TRACK methods. TRACE and TRACK
are HTTP methods which are used to debug web server connections. 

It has been shown that servers supporting this method are subject to
cross-site-scripting attacks, dubbed XST for "Cross-Site-Tracing", when
used in conjunction with various weaknesses in browsers. 

An attacker may use this flaw to trick your legitimate web users to give
him their credentials. 

Solution:

Disable these methods.

See Also :

[http://www.kb.cert.org/vuls/id/867593](http://www.kb.cert.org/vuls/id/867593)

Risk Factor :

Low / CVSS Base Score : 2 
(AV:R/AC:L/Au:NR/C:P/A:N/I:N/B:N)

Solution: 

Add the following lines for each virtual host in your configuration file :

RewriteEngine on
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]

When Googling the code that corrects the problem, everybody seems to have a variation of the second line.  What exactly do I do, specifically?

I've done things like turned the ServerSignature off and set ServerTokens to Prod.  What else can I do to secure all of LAMPs components, save postfix and mailx - those never worked right and errored during the install do I just purged them as they weren't needed anyway.  Pretty much just dealing with SQL, PHP 5, and Apache.

Thanks!

---

### Post by masmad on 2007-05-10
First enable mod_rewrite like this:
```
sudo a2enmod rewrite
```

Then add the text
```
RewriteEngine On
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]
```
to a place of your choosing, this can be server config, virtual host, directory, .htaccess, I think. I didn't get this to work by adding it to httpd.conf but using it in the virtual hosts worked. So, in my case I wrote the above lines to all the files under /etc/apache2/sites-available/.

Then reload apache configs by
```
sudo /etc/init.d/apache2 reload
```

Now if you test it with nessus, I'm pretty sure that it still reports the TRACE and TRACK methods as being active, because of the way the "fix" works. It doesn't disable the methods, but prevents using them.

The way to test manually is
```
telnet your_apache_host 80

TRACE /index.html HTTP/1.1
Host: your_apache_host



```
Note: you need to press enter a few times to signify the end of the commands.

If you get any other response than a 403 forbidden one, something has gone wrong.

---

