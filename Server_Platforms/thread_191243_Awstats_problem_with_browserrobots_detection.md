---
title: "Awstats problem with browser/robots detection"
date: 2006-06-07
forum: Server Platforms
---

### Post by Gerbils on 2006-06-07
I have installed Awstats and run through the config files. All seems to be ok except for it not recognising browsers and robots. I am using dapper with apache2.

Line from the domain file in sites-available:
CustomLog /var/log/apache2/mydomain.com.log combined

In my awstats.conf file:
LogFormat=1
LevelForBrowsersDetection=2
LevelForRobotsDetection=2 

Line from the log file:
11.22.33.44 - - [07/Jun/2006:13:41:54 +0200] "GET / HTTP/1.1" 200 4609 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.3) Gecko/20060426 Firefox/1.5.0.3"

Any Idea what might be wrong here?

Please ask if more information is required.

---

### Post by Gerbils on 2006-06-08
Anyone?

---

### Post by jackrobinson on 2007-03-25
> **Gerbils said:**
> Anyone?

I am having the exact same problem except that I am on Ubuntu 6.10. Awstats works perfectly except for browser/operating-system/robot detection. I am running apache2 and yes, browser/os detection is enabled by default in /etc/awstats/awstats.conf
I have included /etc/apache2/awstats.conf in /etc/apache2/apache2.conf .
/etc/apache2/awstats.conf reads as follows:
> Alias /awstatsclasses "/usr/share/awstats/lib/"
Alias /awstats-icon/ "/usr/share/awstats/icon/"
Alias /awstatscss "/usr/share/doc/awstats/examples/css"
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
ScriptAlias /awstats/ /usr/lib/cgi-bin/
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch

<Directory "/usr/share/awstats/">
Options FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
</Directory>
Any help would be greatly appreciated.

---

### Post by MJN on 2007-03-26
Are the robot charts showing? That is, empty?

Do you have ShowRobotsStats=HBL set?

Mine's working out of the box (I don't recall making any modifiction for the robots bit) -  [http://www.newtonnet.co.uk/cgi-bin/awstats.pl](http://www.newtonnet.co.uk/cgi-bin/awstats.pl)

Mathew

---

### Post by kebes on 2007-07-15
I know this is an old thread, but I just encountered the same problem and managed to find a solution. The problem seems to be that a default install of AWStats on Ubuntu sets the log format to a type that ignores the user agent string. To fix it, just change LogFormat from "4" to "1" in the file /etc/awstats/awstats.conf (or whatever config file you are using).

So, just go:
```

$ sudo nano /etc/awstats/awstats.conf

```

Find the line that says "LogFormat=4" and change it to:
LogFormat=1

Save the file, and it should work from now on.


I hope that helps someone.

---

### Post by bojo on 2007-12-30
just Thank you - fixed it right away :-)

---

### Post by KooW on 2008-04-09
Thanks kebes! That fixed the problem for me :guitar:

---

