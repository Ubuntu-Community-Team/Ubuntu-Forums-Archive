---
title: "New Wordpress endeavor - need help"
date: 2010-06-12
forum: Server Platforms
---

### Post by comicbookcrap on 2010-06-12
Good news and bad news. First endeavor into this world. Certified MS monkey but I know Cisco IOS too so dont judge. 
 
Why am I getting Apache2 "It Works!" page and not Wordpress "Hello World!" page?
 
Everything appears to be correct. 
 
Ubuntu Server 10 - no issues
Installed LAMP option; SSL / FTP is working fine. 
MySQL database is fine as is the myphp interface. 
PHP installed fine looks good.
Wordpress installed fine; dashboard up.
 
My issue is that I am stuck on Apache2 It Works! and not the expected Hello World page. All posts / pages fail (About page). So it looks like apache2 issue but my configs look good?
 
Ideas?

---

### Post by Jive Turkey on 2010-06-12
Did you install wordpress from the ubuntu repositories or from the .zip download?  

If it was the former, try [http://hostname/wordpress](http://hostname/wordpress) substituting "hostname" with your server's resolvable hostname or IP address. 

If the latter, make sure the document root in your apache site config file is correct for where you unzipped the wordpress package.

---

### Post by comicbookcrap on 2010-06-12
> **Jive Turkey said:**
> Did you install wordpress from the ubuntu repositories or from the .zip download? 
 
If it was the former, try [http://hostname/wordpress](http://hostname/wordpress) substituting "hostname" with your server's resolvable hostname or IP address. 
 
If the latter, make sure the document root in your apache site config file is correct for where you unzipped the wordpress package.
 
It was the later (download, unpack) - I unpacked to /var/www/ (DocumentRoot in default configuration for Apache2) as instructed. Then I used the PHP installer from Wordpress as instructed. 
 
Database connected and I was able to ftp themes and test posts etc. 
 
The only thing that did not work was actually being able to view my blog / wp site. All I could get to was Apache's It Works! Page.

---

### Post by Ryan Dwyer on 2010-06-12
Potentially stupid question, but did you remove the index.html and other files (if any) before extracting the Wordpress files to that directory?

Have you tried pressing Ctrl + F5 in your browser to force reload the page?

---

### Post by The Bright Side on 2010-11-03
Hey comicbookcrap,

try to get rid of the index.php or index.html file from /var/www and instead put index.php from the wordpress ZIP there. That may work!

You say you have been able to plug themes into your wordpress installation on your localhost. How are you doing that? For me, it doesn't work.

When I download e.g. the Arras theme as zip, unpack it and move the folder into /var/www/kme/wp-content/themes, it simply won't show up in my "Appearance" section of the wp admin panel.

If I try to download and install it from the panel, I get the screen that asks me for FTP info (Host name, username, password), and I'm a bit stumped there. No matter what I enter, I get

> Failed to connect to FTP Server localhost:21

or variations thereof, depending on what I put in as FTP server (e.g. "localhost/kme").

How did you get past that?

---

