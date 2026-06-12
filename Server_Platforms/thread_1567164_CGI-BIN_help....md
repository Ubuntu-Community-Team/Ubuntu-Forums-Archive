---
title: "CGI-BIN help..."
date: 2010-09-03
forum: Server Platforms
---

### Post by mytinytown on 2010-09-03
I am using Ubuntu 10.04 server with apache 2. I have set up a virtual server for the web server. I got the MySQL database working and PHP working. I just can not get my CGI scripts to run. I have 2 different systems set up and I can not get the CGI to work on either.

This is what I have:
Per-Directory Options
Directory /
Directory /var/www/
Directory /usr/lib/cgi-bin
Directory /usr/share/doc/

CGI Programs
CGI directory aliases
from /cgi-bin/
to /usr/lib/cgi-bin/
I have changed to above several different ways and no luck.

I was told to put a cgi-bin folder in the /var/www/ so it would be /var/www/cgi-bin/

This give me a "Not Found" I have the cgi script chmod at 755 and I have tried 777. If I put a copy in /usr/lib/cgi-bin/ I get an "Internal Server Error". The script works find on the Host Gator server. The top of the script has "#!/usr/bin/perl" I know this is correct too.

Any tips?

---

### Post by spjackson on 2010-09-03
> **mytinytown said:**
> If I put a copy in /usr/lib/cgi-bin/ I get an "Internal Server Error". The script works find on the Host Gator server. The top of the script has "#!/usr/bin/perl" I know this is correct too.

Check the apache error.log. By default this is /var/log/apache2/error.log. This should give a clue as to what is going wrong with the script. It may require a perl package that is not installed.

Also, try running the script from a terminal. What do you get then?

---

### Post by mytinytown on 2010-09-03
> **spjackson said:**
> Check the apache error.log. By default this is /var/log/apache2/error.log. This should give a clue as to what is going wrong with the script. It may require a perl package that is not installed.

Also, try running the script from a terminal. What do you get then?

OK error log shows nothing if I only have the cgi script in /var/www/cgi-bin/ it still adds nothing if it is in /usr/lib/cgi-bin/

I do all my testing from a terminal, my set up of Ubuntu is based on the old SG20. I only have a power cable and ethernet cable plugged in. I use putty and webmin.

Any clue what package it could be?

Edit:
I just changed the:
CGI Programs
CGI directory aliases
from /cgi-bin/
to /usr/lib/cgi-bin/
TO
from /var/www/cgi-bin/
to /usr/lib/cgi-bin/
Now it shows the script like a txt file.

Also it too a bit for the info to show up in the apache log
"PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Sep 03 12:54:53 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Fri Sep 03 13:01:58 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Sep 03 13:02:51 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations"

---

### Post by spjackson on 2010-09-03
It is unusual, but not impossible to have an Internal Server Error page returned but no message in error.log. If you are successfully running the perl script in a terminal on the webserver host, then it's not likely that there's a missing package ('use' or 'require' statements in the perl script) - unless there are search path issues.

I confess that I am confused about:

[LIST]
[*]What error you are currently getting
[*]Where the perl script is currently installed (one and only one place to clarify matters)
[*]How your cgi-bin is currently configured in the apache configuration
[*]What url you are putting in your browser to access the cgi script
[/LIST]

---

### Post by mytinytown on 2010-09-03
> What error you are currently getting
No idea either, I have very little experience.

> Where the perl script is currently installed (one and only one place to clarify matters)
Did a find on perl and came up with:
/etc/perl (dir)
/etc/bash_completion.d/perl (file)
/usr/lib/perl (dir)
/usr/bin/perl (file)
/usr/share/lintian/overrides (file)
/usr/share/doc/perl (dir)
/usr/share/doc/samba-doc/examples/scripts/shares/perl (dir)
/usr/share/perl (dir)

> How your cgi-bin is currently configured in the apache configuration
How could I show you or check it?

> What url you are putting in your browser to access the cgi script
It is for my personal server, not really wanting the url to be public. I will private message you the url. I have 2 CGI scripts that should work. 1 is a simple IP logger and the other is guardian. Which the IP logger still works 100% on my current Host gator server.

---

### Post by mytinytown on 2010-09-06
This has been resolved, I had DOS line ends on my scripts.

---

