---
title: "htaccess won't secure a directory (AWSTATS)"
date: 2010-11-22
forum: Server Platforms
---

### Post by clay7 on 2010-11-22
Hello,

I installed AWSTATS on my LAMP 10.04 LTS and followed several tutorials ([http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/](http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/) among others) but I can't secure the folder, either by an alias or by .htaccess. I tried both methods manually and by using Webmin.

If you go to the URL [www.mywebsite/awstats/awstats.pl](www.mywebsite/awstats/awstats.pl) it shows up, which is good, but this is the default installation site and anyone who knows awstats could possibly see my stats. The conf  folder is /etc/awstats/, and I did an alias for that, then .htacess, but neither worked. With the .htaccess, I would get a password promt but the full stats page was visible behind the password promt, and if you clicked "Cancel" about 20 times or so the promt would go away and the full stats page would be visible. 

The actual file that powers awstats is in /usr/share/lib/cgi-bin/awstats.pl, and I also tried an Alias and .htaccess seperately and neither worked.

I restarted apache2 after each change and I've searched several forums, but I still can't figure this out.

Thank you,

---

### Post by Ceyx on 2011-03-12
As my stats are only accessed from behind my router, never off site, I used the following in my awstats.domain.conf file:

AllowAccessFromWebToFollowingIPAddresses="192.168.1.1"

From off site, I get an ugly screen saying "not allowed from IP xx.xx.xx.xx

which confirms that awstats is running, but it will not allow anything else to be seen.

If you have figured out a more elegant way, post it !

Hope it helps.....

---

### Post by itilious on 2011-05-16
worked perfectly and is exactly what I was lookin for, ty

---

### Post by MaxBux on 2011-09-19
To secure the AWStats directory, usually located in /cgi-bin/, requires use of .htpasswd and this has to be allowed in your Apache configuration using “AllowOverride AuthConfig”. 

You can also allow access to AWStats only from your public IP and configured username. Its also safe to disable browser updates.

Sources:
[http://www.in4mnation.com/install-secure-awstats-ubuntu-server-desktop-apache2/](http://www.in4mnation.com/install-secure-awstats-ubuntu-server-desktop-apache2/)

---

### Post by M1GEO on 2012-12-05
I know this is a bit late, but just for the record. There were a lot of people asking for this online when I searched, but few answers.

Create a password file with htpasswd and put it somewhere safe and outside of public reach, setting permissions.  I put mine in /etc/apache2/.htpasswd

Then edit/create the .htaccess file inside the cgi-bin folder (/usr/lib/cgi-bin on Ubuntu Server 12.10), and add the following:

```
<Files "awstats.pl">
        AuthUserFile /etc/apache2/.htpasswd
        AuthGroupFile /dev/null
        AuthName "AWStats is Private"
        AuthType Basic
        require valid-user
</Files>
```

You will need to edit the AuthUserFile line to reflect your passwords file.  You can also change the requirement to a specific name (require george) or whatever.

Finally, and I guess this is where people go wrong, you have to tell Apache2 to allow you to override the default settings for the cgi-bin folder.

Edit /etc/apache2/sites-available/default (and other virtual host files as required, e.g. SSL) looking for the CGI-BIN section, you need to change the "AllowOverride None" to "AllowOverride AuthConfig" to allow the .htaccess file to work.  It should look something like this:

```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
        AllowOverride AuthConfig
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
</Directory>

```

Hope that helps.  Sorry for digging up an old thread.

---

